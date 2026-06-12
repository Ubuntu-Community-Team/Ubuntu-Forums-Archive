---
title: "Need help getting ps3 media server to work"
date: 2009-07-03
forum: Multimedia Software
---

### Post by havoc783 on 2009-07-03
I downloaded the latest ps3 media server, a java application.  When I try to launch it I get this message:

jring@jring-desktop:~/pms-linux-1.10.5$ java ./PMS.sh
Exception in thread "main" java.lang.NoClassDefFoundError: //PMS/sh
Caused by: java.lang.ClassNotFoundException: ..PMS.sh
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: ./PMS.sh.  Program will exit.

I using Ubuntu 9.04.

Thanks for any advice.

---

### Post by Vangelis on 2009-08-06
Hi havoc,

Whilst the ps3 media server is indeed a java application, you don't need to execute the sh file via the java engine itself. This should be called withing the .sh file. So all you need to do is ls to the ps3 media server directory then just run ./PMS.sh.

But you probably know this already and have successfully run it.

Cheers,

Vangelis

---

### Post by vmwareguy on 2009-10-19
Hi havoc,

I know this reply is really late but this thread may help someone else.

The reason you were getting that message is that you had not run ant to build the package once you downloaded the latest source.

Just change directory to where the PMS.sh resides and run 'ant'. It shouldn't take long to build and then it will run fine.

You will likely need to run this if you haven't installed ant before:

```
sudo apt-get install ant
```

Enjoy!

---

