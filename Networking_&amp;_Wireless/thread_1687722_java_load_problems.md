---
title: "java load problems"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by smurphy_it on 2011-02-14
Upon invoking firefox, and going to a web page that uses java (web page for qlogic fibre switch) I get the following:


java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.5) (6b20-1.9.5-0ubuntu1~10.04.1)
OpenJDK Server VM (build 19.0-b09, mixed mode)
java.util.zip.ZipException: error in opening zip file
	at java.util.zip.ZipFile.open(Native Method)
	at java.util.zip.ZipFile.<init>(ZipFile.java:131)
	at java.util.jar.JarFile.<init>(JarFile.java:150)
	at java.util.jar.JarFile.<init>(JarFile.java:101)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJar(JarSigner.java:287)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJars(JarSigner.java:247)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.verifyJars(JNLPClassLoader.java:883)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:389)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
java.util.zip.ZipException: error in opening zip file
	at java.util.zip.ZipFile.open(Native Method)
	at java.util.zip.ZipFile.<init>(ZipFile.java:131)
	at java.util.jar.JarFile.<init>(JarFile.java:150)
	at java.util.jar.JarFile.<init>(JarFile.java:101)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJar(JarSigner.java:287)
	at net.sourceforge.jnlp.tools.JarSigner.verifyJars(JarSigner.java:247)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.verifyJars(JNLPClassLoader.java:883)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:389)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet.
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:604)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:395)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:395)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:168)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:249)
	at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:575)
	at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:548)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:729)
java.lang.NullPointerException
	at net.sourceforge.jnlp.NetxPanel.runLoader(NetxPanel.java:99)
	at sun.applet.AppletPanel.run(AppletPanel.java:380)
	at java.lang.Thread.run(Thread.java:636)
java.lang.NullPointerException
	at sun.applet.AppletPanel.run(AppletPanel.java:430)
	at java.lang.Thread.run(Thread.java:636)
^Tjava.lang.Exception: Applet initialization timeout
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:637)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
java.lang.RuntimeException: Failed to handle message: handle 67112092 for instance 1
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:660)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
Caused by: java.lang.Exception: Applet initialization timeout
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:637)
	... 2 more
Error: Unable to fetch applet instance id from Java side.
Error: Unable to fetch applet instance id from Java side.


Suggestions ?

Require any further information ?

---

