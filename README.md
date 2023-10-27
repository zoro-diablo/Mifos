# Mifos X Web App [![Build Status](https://travis-ci.com/openMF/web-app.svg?branch=master)](https://travis-ci.com/openMF/web-app)

Mifos X Web App is the revamped version of the Mifos X Community App, an effective financial inclusion solution and the default web application built on top of the Mifos X platform for the Mifos User Community.

It is a Single-Page App (SPA) written in standard web technologies [HTML5](http://whatwg.org/html), [SCSS](http://sass-lang.com) and [TypeScript](http://www.typescriptlang.org). It leverages the popular [Angular](https://angular.io/) framework and [Angular Material](https://material.angular.io/) for material design components.


## Getting started using

The latest code is continuously deployed at https://openmf.github.io/web-app/ whenever a PR is merged into the master branch.


## Getting started developing

1. Ensure you have the following installed in your system:

    [`git`](https://git-scm.com/downloads)

    [`npm`](https://nodejs.org/en/download/)

2. Install [angular-cli](https://github.com/angular/angular-cli) globally.
```
npm install -g @angular/cli@14.2.12
```

3. Clone the project locally into your system.
```
git clone https://github.com/zoro-diablo/Mifos.git
```

4. `cd` into project root directory and make sure you are on the master branch.

5. Install the dependencies.
```
npm install
```

6. To preview the app, run the following command and navigate to `http://localhost:4200/`.
```
ng serve
```
 ERROR 1 => Error appears on the first 'ng serve' execution
```
PS C:\Users\Albin Jose\Desktop\webb app\Mifos> ng serve
ng : File C:\Users\Albin Jose\AppData\Roaming\npm\ng.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see 
about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ ng serve
+ ~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```
SS ->
[![Whats-App-Image-2023-10-27-at-18-23-18-3e60f3d9.jpg](https://i.postimg.cc/8cwHQyvJ/Whats-App-Image-2023-10-27-at-18-23-18-3e60f3d9.jpg)](https://postimg.cc/BPLD2BM4)

Go to windows powershell as administrator and type
```
Set-ExecutionPolicy RemoteSigned
```
And then type ' y ' and press enter. Now check if it is updated by typing this command
```
Get-ExecutionPolicy
```
If it is showing RemoteSigned then continue Step 6 --> ng serve

ERROR 2 => Error appears on the second 'ng serve' execution
```
FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory
 1: 00007FF736A3457F node::SetCppgcReference+15775
 2: 00007FF7369ADD86 SSL_get_quiet_shutdown+74710
 3: 00007FF7369AFBA1 SSL_get_quiet_shutdown+82417
 4: 00007FF73741AF01 v8::Isolate::ReportExternalAllocationLimitReached+65
 5: 00007FF737404698 v8::Function::Experimental_IsNopFunction+1336
 6: 00007FF737265FE0 v8::Platform::SystemClockTimeMillis+659552
 7: 00007FF737272263 v8::Platform::SystemClockTimeMillis+709347
 8: 00007FF73726FBC4 v8::Platform::SystemClockTimeMillis+699460
 9: 00007FF737262D00 v8::Platform::SystemClockTimeMillis+646528
10: 00007FF73727837A v8::Platform::SystemClockTimeMillis+734202
11: 00007FF737278BF7 v8::Platform::SystemClockTimeMillis+736375
12: 00007FF73728182E v8::Platform::SystemClockTimeMillis+772270
13: 00007FF7372923AA v8::Platform::SystemClockTimeMillis+840746
14: 00007FF737296E78 v8::Platform::SystemClockTimeMillis+859896
15: 00007FF73700E522 v8::base::Thread::StartSynchronously+372210
16: 00007FF7373AA721 v8::SharedValueConveyor::SharedValueConveyor+257617
17: 00007FF7373AAA60 v8::SharedValueConveyor::SharedValueConveyor+258448
18: 00007FF7374CBA3E v8::PropertyDescriptor::writable+674286
19: 00007FF6B876FD67
```
SS ->

[![Whats-App-Image-2023-10-27-at-18-25-11-74fbfaf6.jpg](https://i.postimg.cc/RCcf3bNw/Whats-App-Image-2023-10-27-at-18-25-11-74fbfaf6.jpg)](https://postimg.cc/Wt1tC8m4)

To Resolve this problem copy the given command below and execute :-

```
node --max_old_space_size=4096 node_modules/@angular/cli/bin/ng serve
```
After this the ng serve should work

7. Log in to mifos
```
http://localhost:4200/
```

The application is using the development server with basic authentication by default. The credentials for the same are:
 
    Username - mifos
    Password - password

Login to dev.mifos.io as in the SS

[![Whats-App-Image-2023-10-27-at-18-33-39-2b7c117a.jpg](https://i.postimg.cc/259MPRMW/Whats-App-Image-2023-10-27-at-18-33-39-2b7c117a.jpg)](https://postimg.cc/TymtDSR2)


**Important Note:** Please do not make any alterations to these credentials.

### Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

### Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use
`ng generate directive|pipe|service|class|guard|interface|enum|module`.

### Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--configuration production` flag for a production build.

Run `npm run build:prod` to build a production artifacts Instead.

### Further help

To get more help on the Angular CLI use `ng help` or go check out the
[Angular-CLI README](https://github.com/angular/angular-cli).


## Setting up a local server

Follow the given instructions for your operating system to setup a local server for the Mifos X platform.

[Windows](https://cwiki.apache.org/confluence/display/FINERACT/Fineract-platform+Installation+on+Windows)

[Ubuntu](https://cwiki.apache.org/confluence/display/FINERACT/Fineract+Installation+on+Ubuntu+Server)

For connecting to server running elsewhere update the base API URL and/or tenant identifier property in the `environments/environment.ts` file and `environments/environment.prod.ts` file for development and production use respectively.

By default OAuth2 is disabled. To enable it, change the value of oauth.enabled property to true in the `environments/environment.ts` file and `environments/environment.prod.ts` file for development and production use respectively.

### Docker


To locally build this Docker image from source (after `git clone` this repo), run:
```
docker build -t openmf/web-app:latest .
```
You can then run a Docker Container from the image above like this:
```
docker run -d -p 4200:80 openmf/web-app:latest
```

Access the webapp on http://localhost:4200 in your browser.

### Docker compose
It is possible to do a 'one-touch' installation of Mifos X Web App using containers (AKA "Docker").
Fineract now packs the Mifos community-app web UI in it's docker deploy.

As Prerequisites, you must have `docker` and `docker-compose` installed on your machine; see
[Docker Install](https://docs.docker.com/install/) and
[Docker Compose Install](https://docs.docker.com/compose/install/).

Now to run a new MifosX Web App instance you can simply:

1. `git clone https://github.com/openMF/web-app.git ; cd web-app`
1. for windows, use `git clone https://github.com/openMF/web-app.git --config core.autocrlf=input ; cd web-app`
1. `docker-compose up -d`
1. Access the webapp on http://localhost:4200 in your browser.

You can also setup different configurations for the MifosX Web App using environment variables:

1. Use environment variables (best choice if you run with Docker Compose):

Fineract backend settings
```
FINERACT_API_URLS
```
Value to set a Fineract server list (environments) to be used, Default value:
```
https://dev.mifos.io,https://demo.mifos.io,https://qa.mifos.io,https://staging.mifos.io,https://mobile.mifos.io,https://demo.fineract.dev,https://localhost:8443
```

```
FINERACT_API_URL
```
Default value used from the Fineract server list. Default value:
```
https://localhost:8443
```

```
FINERACT_PLATFORM_TENANT_IDENTIFIER
```
Fineract Tenant identifier to be used by default, It must be aligned with the Fineract `tenants` table. Default value:
```
default
```

```
FINERACT_PLATFORM_TENANTS_IDENTIFIER
```
Fineract Tenant identifier list to be used, Those must be aligned with the Fineract `tenants` table. 


Setting for Languages (i18n) still under development
```
MIFOS_DEFAULT_LANGUAGE=en-US
```
```
MIFOS_SUPPORTED_LANGUAGES=en-US,fr-FR
```


Setting for applying the Client preload in the Clients view, Default true
```
MIFOS_PRELOAD_CLIENTS=false
```


Setting for exporting report table to CSV file using this field delimiter
```
MIFOS_DEFAULT_CHAR_DELIMITER=,
```

For more information look the env.sample file in the root directory of the project

## Want to help? [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/openMF/web-app/issues)

Want to file a bug, request a feature, contribute some code, or improve documentation? Excellent! Read up on our guidelines for [contributing](.github/CONTRIBUTING.md) and then check out one of our [issues](https://github.com/openMF/web-app/issues). Make sure you follow the guidelines before sending a contribution!
