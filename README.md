# n8n-heroku

![Docker](https://github.com/Plant-for-the-Planet-org/n8n-heroku-integration/workflows/Docker/badge.svg) ![Test Heroku](https://github.com/Plant-for-the-Planet-org/n8n-heroku-integration/workflows/Heroku/badge.svg)

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/Plant-for-the-Planet-org/n8n-heroku)

New method, just click, configure and get your n8n running.
Also, now set app stack to container and simply connect this Github repo and deploy, heroku uses default configuration from app.json

default basic auth is user:pass

### n8n(Nodemation) - Free and Open Workflow Automation Tool

This is a [Heroku](https://heroku.com/) focused container implementation for the [n8n Automation Tool](https://n8n.io/). Just connect your fork of this repo to heroku and let it work as a charm!

## Requirements
* Heroku CLI

## Setup

this is old setup guide not required now, connect this Github repo to heroku to auto configure. or click the above button to deploy without Github.

### STEP 1: CHANGE your App Stack to container
you can change your app's stack using heroku cli, make sure you have heroku cli installed.

#### login into heroku account
    heroku login

#### change app stack
    heroku stack:set container --app APP_NAME
replace APP_NAME with your heroku app name

### STEP 2: ADD Config Vars for enabling basic authentication (Optional)
It's recommended that you enable basic authentication when deployingn n8n on web. You need to set the following Environment Variables(Config Vars) in your App settings.

    N8N_BASIC_AUTH_ACTIVE=true
    N8N_BASIC_AUTH_USER=SET_USERNAME
    N8N_BASIC_AUTH_PASSWORD=SET_PASSWORD

### STEP 3: DONE! Now CONNECT Github repo and Deploy.

## Using Container Registry

you can also deploy this project using container registry (requires aditional requirements installed). Just clone/download this repository on your local machine.

### Additional Requirements (for building on local)
* docker
* docker-compose

### Steps
cd into your project directory

    cd n8n-heroku/

login into heroku account
    
    heroku login

create heroku app

    heroku create APP_NAME

change app stack

    heroku stack:set container --app APP_NAME
    
set config vars(optional)

    heroku config:set N8N_BASIC_AUTH_ACTIVE=true
    heroku config:set N8N_BASIC_AUTH_USER=SET_USERNAME
    heroku config:set N8N_BASIC_AUTH_PASSWORD=SET_PASSWORD

build and push container image to heroku

    heroku container:push web --app APP_NAME
    
release new build

    heroku container:release web --app APP_NAME
    
<br />

Maybe now you can specify which N8N version to install by Setting a Environment Variable N8N_VERSION or with a build time argument of the same. Not tested yet though, create an issue if it does't work. CI is passing so it is working correctly with default values.

_Update - To set n8n version you can pass a argument when deploying using container registry_

    heroku container:push web --arg N8N_VERSION=0.60.0 --app APP_NAME

### Sources

https://github.com/n8n-io/n8n
