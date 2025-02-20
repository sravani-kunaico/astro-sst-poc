# Astro Starter Kit: Minimal

```sh
npm create astro@latest -- --template minimal
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/minimal)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/astro/tree/latest/examples/minimal)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/withastro/astro?devcontainer_path=.devcontainer/minimal/devcontainer.json)

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
/
├── public/
├── src/
│   └── pages/
│       └── index.astro
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).

## Steps to Integrate SST and deploy to AWS S3 with Cloudfront

Pre-Requisites:
---------------
- Node installed
- Astro project created
- AWS credentials configured

Steps:
------
1. Once Astro project is created, cd into current project
2.  Now initialize SST in your application
    - npx sst@latest init
3. Once SST is initialized, it will create new file sst.config.ts, sst-env.d.ts, modify tsconfig.json, add sst to package.json.
4. The sst.config.ts file is the main configuration file for SST, which is a framework for deploying serverless applications on AWS. It defines infrastructure and deployment settings.
5. It will also ask to update astro.config.mjs. This file is the configuration file for Astro, a static site generator. It defines how Astro behaves, including build options, integrations, base URLs, and more.
                
                
                import aws from "astro-sst"; //This is an SST adapter that allows deploying Astro to AWS
                export default defineConfig({
                    output: "server", //Enables Server-Side Rendering (SSR) instead of Static Site Generation (SSG).
                    adapter: aws() //Uses the SST AWS adapter (astro-sst) to deploy the site to AWS.
                }); 
                
6. After making these changes, we are good to go.
7. To start in dev mode
    - npx sst dev // run your AWS application locally while simulating a live AWS environment with hot reloading.
8. To deploy to AWS
    - npx sst deploy // Fully deploys the app to AWS 
9. Once its deployed successfully, it will generate cloudfront URL where you can access your application.