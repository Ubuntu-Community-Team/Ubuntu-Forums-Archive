---
title: "Problems getting the JMF to work in 11.04"
date: 2011-09-02
forum: Multimedia Software
---

### Post by tambascot on 2011-09-02
Hi forum,

I'm an old hand at linux (maybe a little bit too old), but have been operating primarily on a Mac and Solaris for the past half a decade and am wondering if anyone can help me figure this out. I develop an application that relies on the JMF, and while my application (Soundboard) works under Mac, Windows, and Open Solaris, when I try running it in the latest Ubuntu, I get this:

```


Exception in thread "main" java.lang.NoClassDefFoundError: javax/media/Player
Caused by: java.lang.ClassNotFoundException: javax.media.Player
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: soundboard.SoundBoard. Program will exit.

```

If I'm not mistaken, this means that Soundboard (or rather java) can't find the JMF or its components. I've made sure the LD_LIBRARY_PATH and CLASSPATH environment variables all point to the right places, and have tried copying the *.so files from the JMF package into /usr/lib, but all to no avail. For the sake of argument, I even tried specifying the classpath of the JMF and associated *.jar files at runtime using java -cp /path, and went so far as to copy JMF related *.jars into Soundboard's own lib directory, but again, to no avail.

Just to be safe, I have tried both editing the *.so download from Oracle, and downloading the compressed binary and trying with that. Again, nothing. 

One of the reasons I started developing this program was so that there would be something like it available on linux and its cousins, and a few years ago an earlier version was successfully tested with one flavor of Ubuntu or another. I'm hoping some generous soul on this forum could point me in the direction of a solution so that I can help my Ubuntu users get this thing running again.

Thanks in advance.

---

