---
title: "azureus 4.2.0.2 console mode"
date: 2009-05-13
forum: Multimedia Software
---

### Post by ninocass on 2009-05-13
hey all, 

Running 4.2.0.2 and trying to get -ui=console to work but im getting an error im using the command i previously used

"java -jar Azureus2.jar --ui=console" 

The error is

> [nino@<snip>/opt/vuze] java -jar Azureus2.jar  --ui=console
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.CommandLine
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: org.gudy.azureus2.ui.common.Main. Program will exit.

thanks!!

---

### Post by ninocass on 2009-05-13
typical!!!! google turns up and answer after posting!

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

---

