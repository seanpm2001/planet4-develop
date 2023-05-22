
# Planet 4 development environment

[![Last pipeline result on main branch](https://circleci.com/gh/greenpeace/planet4-develop.svg?style=shield)](https://app.circleci.com/pipelines/github/greenpeace/planet4-develop)

<p align="center"><em>
Get a full Planet 4 development environment to your local machine!
</em></p>

We are using [`wp-env`](https://github.com/WordPress/gutenberg/blob/trunk/packages/env/README.md) as a base and pulling all necessary themes and plugins so that you can develop for your website more easily.


## System Requirements

- docker, docker compose
  - https://docs.docker.com/get-docker/
  - https://docs.docker.com/compose/reference/
- node, npm, nvm
  - https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
  - https://github.com/nvm-sh/nvm
- curl
- wp-env
  - `npm -g i @wordpress/env`
- _optional: gsutil CLI_
  - https://cloud.google.com/storage/docs/gsutil_install

## Before anything

- Clone this repo
- Set node version
```console
nvm use
```
- Check the requirements with: 
```console
npm run env:requirements
```
- Install npm packages:
```console
npm install
```

## Installation

Install default developer environment with:
```console
npm run env:install
```

For NRO developers, use instead:
```console
npm run nro:install <your nro name>
```

## Clean up

```console
npm run env:clean
```

## All commands
```
npm run
- env:requirements                  Check requirements
- env:install                       Install default Planet 4 theme and database
- env:start                         Start the environment
- env:stop                          Stop the environment
- env:clean                         Clean wp-env and delete all Planet 4 files
- env:config                        Show generated configuration
- env:fix-permissions [all]         Fix files permissions to current user as owner
- env:clean-repos                   Remove main repos if they are not git repositories
- env:update                        Update installer, base and main repos
- env:status                        Status of docker containers
- env:e2e-install                   Install E2E tests dependencies
- env:e2e                           Run E2E tests on local instance
- nro:install <?nro>                Install NRO theme and database
- nro:enable                        Enable installed NRO theme and database
- nro:disable                       Switch back to default theme and database
- nro:theme <?nro>                  Clone NRO theme in themes dir
- build:assets                      Build main repos assets
- build:repos                       Clone and install main repos
- db:import <dump path> <db name>   Import database dump (gzip)
- db:use <db name>                  Switch to database
- shell:php                         Access PHP shell (WordPress container)
- shell:mysql                       Access MySQL console (current database)
- elastic:activate                  Activate ElasticSearch container and plugin
- elastic:deactivate                Deactivate ElasticSearch container and plugin
```

## Workflow

- themes are installed in `planet4/themes`
  - the theme is usually cloned by the installer and should be modifiable right away
  - you can add or create any theme in this folder, it will be available in your local instance
- plugins are installed in `planet4/plugins`
  - if a plugin you want to work on is not writable, either use `npm run env:fix-permissions`, or remove it and clone your own repo to replace it
  - you can add or create any plugin in this folder, it will be available in your local instance

## Resources

- https://github.com/WordPress/gutenberg/tree/trunk/packages/env
- https://github.com/WordPress/developer-blog-content/issues/89
