---
title: "Iriverter will not start; please offer a solution"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by Gruss2 on 2007-05-29
Hello, I've been having an ongoing problem with the video converter program Iriverter not starting on my computer; even though it was installed using Ubuntu's built in add/remove application program. I tried searching the forums for a solution. But when it seemed I came across one, it didn't work for me.  Strangely, it worked a couple of days ago, but only recently stopped launching. I tried uninstalling and reinstalling it, and then rebooting my pc, but it still will not start after clicking on it. Can someone please post a clear step by step solution to this problem, because I'm sure I'm not alone in having this issue. Thanks.

---

### Post by Leetbumble on 2007-10-19
I have the same problem. if you run it through the terminal you get this

Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/events/SelectionListener (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

I checked and i have all the java installs / ive run apt-get update and it has not helped. no idea yeah... if i get an answer ill post

---

### Post by jaymz52 on 2007-10-20
I'm having the exact same problem with a fresh install of Gutsy

---

### Post by silvagroup on 2007-11-05
Having same problem here.
Looks very similar to Leetbubles error;
[CODE$ iriverter
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
][/CODE]
Anyone have a solution yet?
Doesn't appear to be a problem in just Gutsy, Fiesty does the same thing.
However it runs just fine in Windows. Go figure.
Thanks in advance.

---

### Post by sml on 2007-11-10
Hmm what about installing java 5 not java 6? I am also having the same problem and not sure what to do.

---

### Post by Elegorod on 2007-11-10
Try to install package libswt3.2-gtk-java in Synaptic. It's the problem with swt library, not java itself.
Iriverter works on my computer, gutsy, Sun Java 6 update 3

---

### Post by silvagroup on 2007-11-13
Have been running in XP with no problems so I kind of forgot about it. I also found a really cool script in the KDE Apps website that makes the conversion process really easy. So for me iriverter may just be out the window for now.

Thanks all.

---

### Post by linuxfrank on 2007-11-13
Check and see through add and remove programs which JAVA web start you have installed. If you have 1.4 installed remove it.  Only have JAVA web start 6 installed. Thats the one that was probably used when iriverter was installed.   Im not sure about the whole technical details but their is a conflict when more then one version is installed.   I removed it and all my JAVA progs work now.Including     aTunes    which is a cool music manager.:guitar:

---

### Post by linuxfrank on 2007-11-14
HI everyone.

I encountered a problem after I got iriverter working. My aTunes would not launch. Long story short, The gcj8base package (java)  that is installed with iriverter disrupts the Java 6 runtime so that makes aTunes useless and any other prog that is installed using java 6 runtime to install. I uninstalled iriverter and the gcj8 packages, updated my mencoder and Mplayer back to the newest release ( aTunes depends on Mplayer) and bingo aTunes works.   Im now using VLC to convert my video files.  Open VLC select the wizard to encode your file.  It woks and works well. Anyone who want to email me for more info thats ok.   [email]ant200467@yahoo.com[/email]
LinuxFrank#-o#-o#-o#-o

---

### Post by spauldingsmails on 2007-11-19
If you are having trouble running iriverter with java 1.6 and are getting the following error at the terminal;

!!! no swt-pi-gtk-3236 in java.library.path

open the iriveter script;

sudo gedit /usr/bin/iriverter

and add the path to the jni directory to your library path (in red);

-Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib[COLOR="Red"]:${exec_prefix}/lib/jni[/COLOR]

This fixed the problem for me, hope it fixes it for you too.

---

### Post by kenjiru on 2007-12-08
I did something similar to solve the problem on Ubuntu 7.04.

I've edited /usr/local/bin/iriverter and changed
```

-Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib

```
into
```

-Djava.library.path=/usr/lib/jni

```

Regards

---

### Post by Gruss2 on 2007-12-17
Thanks kenjiru and spauldingsmails !   That solved my problem, and now my iriverter starts!  :)

Happy Holidays!

---

### Post by sojyujai on 2007-12-27
> **spauldingsmails said:**
> If you are having trouble running iriverter with java 1.6 and are getting the following error at the terminal;

!!! no swt-pi-gtk-3236 in java.library.path

open the iriveter script;

sudo gedit /usr/bin/iriverter

and add the path to the jni directory to your library path (in red);

-Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib[COLOR="Red"]:${exec_prefix}/lib/jni[/COLOR]

This fixed the problem for me, hope it fixes it for you too.

Thanks this got it working for me too.  I'm on gutsy and had installed sun java 6 which I guess messed up iriverter.

---

### Post by matthias_k on 2008-01-22
oh yeah, sweet, that did the job, thanks guys!

---

### Post by rocksocke on 2008-02-07
yeah!

adding :${exec_prefix}/lib/jni

solved the problem for me too. thanks a lot!

---

### Post by Sonja on 2008-02-11
I'm a Linux n00b. Can somebody please tell me the exact line or lines I must type in Terminal to fix Iriverter?

---

### Post by rocksocke on 2008-02-11
open a terminal and type

```
sudo gedit /usr/bin/iriverter
```

find the line where it says (at least on my amd64 gutsy):

```
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar 
```

and change it to (changed text is red)

```
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib[COLOR="Red"]:${exec_prefix}/lib/jni[/COLOR] -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar 
```

save the file and exit. it should work now.

---

### Post by DaV|d on 2008-03-04
Thanks Spauldingsmails, your fix worked for me :)

---

### Post by Sonja on 2008-03-04
I still get this:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/events/SelectionListener (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

```

---

### Post by darc on 2008-03-11
> **spauldingsmails said:**
> If you are having trouble running iriverter with java 1.6 and are getting the following error at the terminal;

!!! no swt-pi-gtk-3236 in java.library.path

open the iriveter script;

sudo gedit /usr/bin/iriverter

and add the path to the jni directory to your library path (in red);

-Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib[COLOR="Red"]:${exec_prefix}/lib/jni[/COLOR]

This fixed the problem for me, hope it fixes it for you too.


That did it for me as well, thanks for the help.
-darc

---

### Post by mihai.ile on 2008-03-23
> **spauldingsmails said:**
> If you are having trouble running iriverter with java 1.6 and are getting the following error at the terminal;

!!! no swt-pi-gtk-3236 in java.library.path

open the iriveter script;

sudo gedit /usr/bin/iriverter

and add the path to the jni directory to your library path (in red);

-Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib[COLOR="Red"]:${exec_prefix}/lib/jni[/COLOR]

This fixed the problem for me, hope it fixes it for you too.


Works like a charm on my Gusty 32bits with java 1.6
Thank you!

---

### Post by gbinal on 2008-04-05
This pretty much sums up the above comment, but the code is laid out and yes, I was having the same problems and this addressed it.  

[http://ubuntuforums.org/showpost.php?p=2855567&postcount=5](http://ubuntuforums.org/showpost.php?p=2855567&postcount=5)

---

### Post by transporter_ii on 2008-04-27
Just installed 8.04 today. Iriverter was one of the first things I installed, and I swear it worked. However, it stopped working later on in the night (or it never worked and I just thought it did).

Tried the code fixes, but still got errors. I tried this (from: [https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237](https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237))

Replace this part in /usr/bin/iriverter with the following:

java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib:/usr/lib/jni -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.thestaticvoid.iriverter.ConverterUI $*

And it started right up and appears to be working. Sorry if this post duplicates information, but I couldn't get it to work with the fixes already on here...or I just missed it or did something wrong.

---

### Post by Vivaldi Gloria on 2008-04-28
I installed Hardy and iriverter didn't work. The change below fixed it. Thanks.

> **rocksocke said:**
> open a terminal and type

```
sudo gedit /usr/bin/iriverter
```

find the line where it says (at least on my amd64 gutsy):

```
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar 
```

and change it to (changed text is red)

```
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib[COLOR="Red"]:${exec_prefix}/lib/jni[/COLOR] -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar 
```

save the file and exit. it should work now.

---

### Post by vincencollins on 2008-05-26
export LD_LIBRARY_PATH=/usr/lib/jni/ works for me but appending to the Djava.library.path doesn't.  Does anyone know why this might be the case?

---

### Post by VanguardOutlander on 2008-05-28
This fix also worked for me! Awesome.

Is this a fix that needs to rolled into an updated iriverter package? :)

---

### Post by Keerghan on 2008-07-04
Thanks :popcorn:

---

### Post by christopher.newell on 2008-07-12
This solution also worked for me, but I had to take one other action.  I have Java 6 installed, but I was using a different java version.  I had to use:```
sudo update-alternatives --config java
```to change the Java I was using.  I'm curious to know, if I didn't make the changes outlined in this thread, could I have just switched my Java version to the old one to get iriverter to work?

---

