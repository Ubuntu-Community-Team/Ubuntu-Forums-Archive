---
title: "worldwind where in the world is it ,no EXE in usr/bin"
date: 2009-08-16
forum: Multimedia Software
---

### Post by LineAxe on 2009-08-16
just installed worldwind , so great I have heard, but where in the world is it. I cant find ANY exe like worldwind.exe anywhere, where oh where COULD :popcorn:synaptic have put it ????????sure didn't tell me...[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by snotplop on 2009-08-17
You won't find any ".exe"'s in this operating system (naturally)

However, you can quickly list the location of a *binary* that is in $PATH by using something along the lines of:
```
$ whereis worldwind
```Also, after you have installed any package using Synaptic, you can view what exactly went into the system and where by right-clicking its entry, clicking "Properties", and going to the "Installed Files" tab.

---

### Post by LineAxe on 2009-08-18
well i did find an executable text file that offered to 
 [COLOR="DarkRed"]run in terminal[/COLOR] ,          [COLOR="DarkRed"]display [/COLOR]        or   [COLOR="DarkRed"] run[/COLOR]   it.

after a few tries at each option ahove and seeing no result I
decided to ask this forum what does it take to get this software up and running ... thanks for the quick reply by the way...

---

### Post by snotplop on 2009-08-19
Try opening a terminal and running it that way.

Ubuntu > Accessories > Terminal

and then run this
```
$ worldwind
```
I just installed it myself from the repos and it works fine (although worldwind itself seems pretty buggy :?)

Many, many apps that are available through Synaptic and apt-get do not provide links to themselves in the ubuntu menu, nor will they all be necessarily installed in /usr/bin. 
Your best bet with an unfamilar app is to first try executing it by typing its name (or some permutation of it) on a command line

---

### Post by mcduck on 2009-08-19
> **LineAxe said:**
> just installed worldwind , so great I have heard, but where in the world is it. I cant find ANY exe like worldwind.exe anywhere, where oh where COULD :popcorn:synaptic have put it ????????sure didn't tell me...[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

You are not going to find any executable files with the ".exe" in Linux. Linux has better ways to figure out what files are than relying on file name extensions, and most files have no extensions at all.

Anyway, the "which"-command is useful for finding the executables, "which *someprogram*" will give the path and name of that program's executable.

for example:
```
$ which firefox
/usr/bin/firefox
$
```

---

### Post by LineAxe on 2009-08-19
thanks i just did and got the following
___________________________________________________
shedhed@shedhed-desktop:~$ worldwind
test: 61: unexpected operator
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

---

### Post by snotplop on 2009-08-20
> **LineAxe said:**
> thanks i just did and got the following
___________________________________________________
shedhed@shedhed-desktop:~$ worldwind
test: 61: unexpected operator
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

Like I said, WorldWind seems buggy :P

---

