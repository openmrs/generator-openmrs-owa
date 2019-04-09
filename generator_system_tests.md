# System Tests: Patient-Friendly Report Generator

<br>
These system tests deal with OWAs generated with AngularJS.
<br>

## Prerequisites
*These will necessary before any of the following system tests can be performed.*

1. OpenMRS and MySQL server must be installed.
2. The `openmrs-module-owa` package must be present.
3. The `generator-openmrs-owa` package must be present.
4. yo generator must be installed.
5. Chrome must be installed for Karma tests.
6. node.js must be installed.
7. Any other relevant OpenMRS OWA dependencies should be set up as needed.

<br>

## System Tests

### T - 01: Bundling With Version Number
1. Open the `webpack.config.js` file within the `generator-openmrs-owa` package (typical filepath might be `/Users/username/openmrs/generator-openmrs-owa/app/templates/webpack.config.js`).   Seek out a line within this file: 
> const packageIncludesVersionNumber = true;

2. Make sure this boolean value is `true` before moving forward. This will tell the generator to include the OWA version number in the generated OWA package.
3. Create a new directory in a location of your choosing (ex: a `test_owa` directory within an `openmrs` directory in your home directory works).  This directory will store all the OWA files.  Using a bash terminal, enter this folder (ex: `cd ~/openmrs-filepath/test_owa`).
4. Run `yo` to show yo generator option. You should be greeted with some yo generator prompts:
> ? 'Allo Ethan! What would you like to do? (Use arrow keys) <br>
> &nbsp;&nbsp; Run a generator <br>
> ❯ @openmrs/openmrs Owa <br>
> &nbsp;&nbsp; ────────────── <br>
> &nbsp;&nbsp; Update your generators <br>
> &nbsp;&nbsp; Install a generator <br>
> &nbsp;&nbsp; Find some help <br>
> &nbsp;&nbsp; Get me out of here! <br> 
> (Move up and down to reveal more choices)
5. Select the `@openmrs/openmrs Owa` generator option to begin OWA generation.
6. Enter the OWA information.
	* What is your app name? Any name will be fine. (ex: `my test owa`).
	* What is your app description? Any description will be fine. (ex: `Medical Report OWA`).
	* What libraries would you like to include? Make sure to select `AngularJS`.
	* What type of server are you running locally? Make sure to select `SDK`.
	* What URL will your app be served from? Hit **Enter** to accept the default (ex: `http://localhost:8080/openmrs/owa/mytestowa/index.html`).
	* What is the path of your local Open Web Apps directory? Hit **Enter** to accept the default (ex: `/Users/username/openmrs/openmrs-platform/owa`).  *NOTE: Your specific path may need to be manually entered or chnaged if you have configured your OpenMRS directories differently.*
	* What is your GitHub username? Enter your GitHub username.
	* What will the GitHub repo URL be? Enter the GitHub URL. You can also just hit **Enter** to accept the defult if you will not be using GitHub (ex: `https://github.com/username/openmrs-owa-mytestowa`).

7. After entering this information, yo should run a number of installs and commands to set up your OWA. This will show a numbeer of lines that look like `create {file-name}`, followed by a number of `npm` commands. Finally, you should recieve a success message and be returned to your OWA directory.
>  Bye from us! <br>
>  Chat soon. <br>
>  Yeoman team <br>
>  http://yeoman.io
8. Your (previously empty) OWA directory should now be populated with a number of files. You can run `ls` to verify the files are akin to...
> LICENSE <br>
> README.md <br>
> app <br>
> karma.conf.js <br>
> node_modules <br>
> package-lock.json <br>
> package.json <br>
> test <br>
> webpack.config.js
9. Open the `package.json` file in your `test_owa` directory and remove the raised carrot (^) from its placement before any version number that is an angular dependency (typically there are roughly 8 to remove). Save your changes.
> "angular-ui-router": "^0.3.0",
10. Remove the line starting with `.config` from the `home.js` file in the OWA directory (typical filepath might be `/Users/username/openmrs/test_owa/app/js/home/home.js`).
> .config(['$qProvider', function ($qProvider) { <br>
> &nbsp;&nbsp; $qProvider.errorOnUnhandledRejections(false); <br>
> }])
11. Run `npm install` in the OWA directory (ex: `test_owa`).
12. Run `npm run build:prod` the OWA directory (ex: `test_owa`) to generate your OWA zip file.
13. Run `mvn clean install` in the `openmrs-module-owa` directory (typical filepath might be `/Users/username/openmrs/openmrs-module-owa`).
14. Locate the OWA snapshot omod file in the `openmrs-module-owa` directory (ex: `/Users/username/openmrs/openmrs-module-owa/omod/target/owa-1.11.0-SNAPSHOT.omod`).
15. Move this omod file to the modules directory of your openmrs server directory (typical filepath might be `/Users/username/openmrs/server-name/modules`).
16. Start your OpenMRS server (start MySQL server and run `mvn openmrs-sdk:run`).
17. Log in to OpenMRS and import your newly-packaged OWA zip (ex: `/Users/username/openmrs/test_owa/mytestowa_0.1.0.zip`).
18. Confirm that the zip file contains the version number (ex: `mytestowa_0.1.0.zip`).
19. Open the OWA in OpenMRS and check that the URL does not include the version number (ex: `http://localhost:8080/openmrs/owa/mytestowa/index.html#/`).


### T - 02: Bundling Without Version Number
1. Open the `webpack.config.js` file within the `generator-openmrs-owa` package (typical filepath might be `/Users/username/openmrs/generator-openmrs-owa/app/templates/webpack.config.js`).   Seek out a line within this file: 
> const packageIncludesVersionNumber = true;

2. Make sure this boolean value is `false` before moving forward. This will tell the generator to include the OWA version number in the generated OWA package.
3. Create a new directory in a location of your choosing (ex: a `test_owa` directory within an `openmrs` directory in your home directory works).  This directory will store all the OWA files.  Using a bash terminal, enter this folder (ex: `cd ~/openmrs-filepath/test_owa`).
4. Run `yo` to show yo generator option. You should be greeted with some yo generator prompts:
> ? 'Allo Ethan! What would you like to do? (Use arrow keys) <br>
> &nbsp;&nbsp; Run a generator <br>
> ❯ @openmrs/openmrs Owa <br>
> &nbsp;&nbsp; ────────────── <br>
> &nbsp;&nbsp; Update your generators <br>
> &nbsp;&nbsp; Install a generator <br>
> &nbsp;&nbsp; Find some help <br>
> &nbsp;&nbsp; Get me out of here! <br> 
> (Move up and down to reveal more choices)
5. Select the `@openmrs/openmrs Owa` generator option to begin OWA generation.
6. Enter the OWA information.
	* What is your app name? Any name will be fine. (ex: `my test owa`).
	* What is your app description? Any description will be fine. (ex: `Patient Drug Report OWA`).
	* What libraries would you like to include? Make sure to select `AngularJS`.
	* What type of server are you running locally? Make sure to select `SDK`.
	* What URL will your app be served from? Hit **Enter** to accept the default (ex: `http://localhost:8080/openmrs/owa/mytestowa/index.html`).
	* What is the path of your local Open Web Apps directory? Hit **Enter** to accept the default (ex: `/Users/username/openmrs/openmrs-platform/owa`).  *NOTE: Your specific path may need to be manually entered or chnaged if you have configured your OpenMRS directories differently.*
	* What is your GitHub username? Enter your GitHub username.
	* What will the GitHub repo URL be? Enter the GitHub URL. You can also just hit **Enter** to accept the defult if you will not be using GitHub (ex: `https://github.com/username/openmrs-owa-mytestowa`).

7. After entering this information, yo should run a number of installs and commands to set up your OWA. This will show a numbeer of lines that look like `create {file-name}`, followed by a number of `npm` commands. Finally, you should recieve a success message and be returned to your OWA directory.
>  Bye from us! <br>
>  Chat soon. <br>
>  Yeoman team <br>
>  http://yeoman.io
8. Your (previously empty) OWA directory should now be populated with a number of files. You can run `ls` to verify the files are akin to...
> LICENSE <br>
> README.md <br>
> app <br>
> karma.conf.js <br>
> node_modules <br>
> package-lock.json <br>
> package.json <br>
> test <br>
> webpack.config.js
9. Open the `package.json` file in your `test_owa` directory and remove the raised carrot (^) from its placement before any version number that is an angular dependency (typically there are roughly 8 to remove). Save your changes.
> "angular-ui-router": "^0.3.0",
10. Remove the line starting with `.config` from the `home.js` file in the OWA directory (typical filepath might be `/Users/username/openmrs/test_owa/app/js/home/home.js`).
> .config(['$qProvider', function ($qProvider) { <br>
> &nbsp;&nbsp; $qProvider.errorOnUnhandledRejections(false); <br>
> }])
11. Run `npm install` in the OWA directory (ex: `test_owa`).
12. Run `npm run build:prod` the OWA directory (ex: `test_owa`) to generate your OWA zip file.
13. Run `mvn clean install` in the `openmrs-module-owa` directory (typical filepath might be `/Users/username/openmrs/openmrs-module-owa`).
14. Locate the OWA snapshot omod file in the `openmrs-module-owa` directory (ex: `/Users/username/openmrs/openmrs-module-owa/omod/target/owa-1.11.0-SNAPSHOT.omod`).
15. Move this omod file to the modules directory of your openmrs server directory (typical filepath might be `/Users/username/openmrs/server-name/modules`).
16. Start your OpenMRS server (start MySQL server and run `mvn openmrs-sdk:run`).
17. Log in to OpenMRS and import your newly-packaged OWA zip (ex: `/Users/username/openmrs/test_owa/mytestowa.zip`).
18. Confirm that the zip file does not contain the version number (ex: `mytestowa.zip`).
19. Open the OWA in OpenMRS and check that the URL does not include the version number (ex: `http://localhost:8080/openmrs/owa/mytestowa/index.html#/`).


## System Test Results
*Enter notes and results here:*

<br>
