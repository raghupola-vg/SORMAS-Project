
# SORMAS Development Environment

## Server
- [Install your local server](SERVER_SETUP.md)

## Git
- Install [Git for your OS](https://git-scm.com/downloads)
- Recommended: Install a Git client such as [TortoiseGit](https://tortoisegit.org/) if you don't want to handle version control from the command line or separately for the Eclipse and Android Studio projects
- Open the Git Bash and execute the command <code>git config --global branch.development.rebase true</code> (which ensures that rebase is used when pulling rather than merge)

## Eclipse
- Install the latest Eclipse version
- Set the default JRE of Eclipse to the installed Zulu Java SDK: [Assigning the default JRE for the workbench ](https://help.eclipse.org/kepler/index.jsp?topic=%2Forg.eclipse.jdt.doc.user%2Ftasks%2Ftask-assign_default_jre.htm)
- Clone the SORMAS-Open repository and import the projects to Eclipse
	- If you're using Eclipse to clone, choose "File -> Import -> Git -> Projects from Git" and continue until you're asked to create a new project from the cloned repository; click cancel instead and use "File -> Import -> Maven -> Existing Maven Projects" to import the separate projects into your workspace
	- If you've cloned the repository from the command line or a Git client, you obviously only need to perform the last step
- Install [Payara Tools](https://marketplace.eclipse.org/content/payara-tools)
- Install the [Vaadin Plugin for Eclipse](https://marketplace.eclipse.org/content/vaadin-plugin-eclipse) (no need to install the commercial UI designer)
- Add a Payara server to Eclipse and enter the credentials you specified when setting up the server

### Additional Steps
- Make a copy of "build.properties.example" contained in "sormas-base", rename it to "build.properties" and set "glassfish.domain.root" to the location of the sormas domain located in the "glassfish/domains" folder inside your payara installation
- Drag the "build.xml" file contained in "sormas-base" into the Ant view in Eclipse
  - Either: Run "Maven install" on the sormas-base project
  - Or: Execute the "install [default]" ant script (this needs a maven installation on your system with the M2_HOME variable set)
  - Then: Execute the "deploy-serverlibs" ant script
- Highlight all Eclipse projects and choose "Maven -> Update Project" from the right click menu; perform the update for all projects
- Start the Glassfish server and deploy "sormas-ear", "sormas-rest" and "sormas-ui" by dragging the respective projects onto it, or use the "Add and Remove..."-function by right clicking on the server.
- Open your browser and type in "http://localhost:6080/sormas-ui" or "https://localhost:6081/sormas-ui" to test whether everything has been set up correctly (and to use the application)

## Android Studio
**Note: This is only needed for development of the SORMAS Android app
* Install the latest Android Studio version (to avoid errors, start the installation with admin rights)
* Start the application
* To avoid errors, ensure that the path for the Android SDK contains no whitespaces
	* The path could be edited at ``Tools -> SDK Manager -> Android SDK Location``
* Open Android Studio and import the "sormas-app" project from Eclipse
* Create a keystore.properties file in sormas-app (see keystore.properties.example for reference).
* Build the Android Studio project by executing the gradle build (this may be done automatically)


