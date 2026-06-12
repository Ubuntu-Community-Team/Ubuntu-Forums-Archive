---
title: "iRiverter won't work. :'["
date: 2008-09-20
forum: Multimedia Software
---

### Post by higashi on 2008-09-20
I've been wanting to use iRiverter for an EXTREMELY long time now, but i guess never enough to ask about it in the forums...
Every time i tried to run iRiverter, nothing would happen, so i tried it in the terminal and got:

> iriverter 
!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! no swt-pi-gtk-3236 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:823)
!!! java.lang.System.loadLibrary(System.java:1030)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
	at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)
george@george-desktop:~$ java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:/usr/lib/jni -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.thestaticvoid.iriverter.ConverterUI $*
Exception in thread "main" java.lang.NoClassDefFoundError: org/thestaticvoid/iriverter/ConverterUI
Caused by: java.lang.ClassNotFoundException: org.thestaticvoid.iriverter.ConverterUI
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)


i went on a site that seemed to solve this problem, but i didn't get it. :(
can someone help me out here?

---

### Post by Keeflookeem on 2009-01-17
*bump*
Me too
this is on 8.04 after trying to use it for the first time.
I installed using apt-get.
Anyone have any ideas? Maybe manually download the libraries from somewhere and dump them into /usr/lib/ or something?

> 
!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! no swt-pi-gtk-3236 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1698)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:840)
!!! java.lang.System.loadLibrary(System.java:1047)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
	at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)


---

