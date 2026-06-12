---
title: "Problem Allocating memory to Minecraft"
date: 2011-08-05
forum: Multimedia Software
---

### Post by Quorio on 2011-08-05
quorio@quorio-VGN-NS140D:~$ java -Xmx1200M -Xms950M -cp Minecraft.jar net.minecraft.LauncherFrame
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.
 
 
tried to allocate min 950mb and max 1200mb ram to Minecraft, got this msg, what do? ](*,) :?

---

