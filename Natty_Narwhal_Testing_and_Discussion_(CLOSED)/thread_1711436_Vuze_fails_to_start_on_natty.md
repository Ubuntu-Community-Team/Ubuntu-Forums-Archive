---
title: "Vuze fails to start on natty"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bigdave146 on 2011-03-21
Hello !
I built a new VM with the latest natty v11 ISO today.  I have run an update after installation, and have installed Vuze from the Software Center.  Now when I start Vuze nothing happens.  If i run it from the command line I get:


druddle@ubuntu:~/Desktop$ sudo vuze &
[1] 1785
druddle@ubuntu:~/Desktop$ file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/lib/java/swt-gtk-3.5.1.jar ; file:/home/druddle/Desktop/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3555 or swt-pi-gtk in swt.library.path, java.library.path or the jar file
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:254)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:79)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:59)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	... 12 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:120)
	at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:679)

I googled it and saw some messages about the swt.jar path.  I tried to create the symlink as they said and it told me it was already created.

Anyone seen this and know what the solution is ?

Dave

---

### Post by s.fox on 2011-03-21
Thread moved to [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

