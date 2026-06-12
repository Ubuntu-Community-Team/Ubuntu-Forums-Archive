---
title: "Im having trouble playing Minecraft on Ubuntu 11.04 Natty Narwhal."
date: 2011-05-31
forum: Multimedia Software
---

### Post by ThyEpik on 2011-05-31
When i log-in to the minecraft launcher my screen goes black. Can anyone help me?

---

### Post by ferulebezel on 2011-06-17
The applet wouldn't even start with open java.  I installed sun java and have the exact same problem.

---

### Post by mexicanseaf00d on 2011-06-17
Do you have OpenGL available? I think it needs some basic acceleration to work.

---

### Post by rachel1.0 on 2011-06-20
Run it from terminal with

```
java -jar minecraft.jar
```

And see if there are any errors. I was running into some errors a while ago, when I first run Minecraft in Maverick, and a google search told me to download bleeding edge version of the native binaries.

Check out the error message that comes to terminal when the screen goes black.

Cheers,

Rachel

---

### Post by Bacon_Cake on 2011-06-24
I have the same problem, but I cannot even play it in browser. I think the Java permissions are messed up. Where do I find them?

---

### Post by mexicanseaf00d on 2011-06-25
```
sudo update-alternatives --config java
```

Choose the sun version, maybe its not set properly.

---

### Post by greenblob on 2011-10-12
I used the automatic shell script to install minecraft. I think Java works fine, as I have no web browser problems, and minecraft starts fine, menus and GUI are fine, but when I start the screen everything is just blank, it's completely black, other than the inventory.

Any ideas?
I'm using a 128MB ATI graphics card which supports open GL and acceleration.

I get this error:
```
$ minecraft [COLOR="Red"]the command I use[/COLOR]
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
	at java.lang.ProcessImpl.start(ProcessImpl.java:81)
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
	... 1 more

```

---

### Post by cernikred on 2012-01-01
Using the 
Code:
```
java -jar minecraft.jar
``` with the /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java java selection from the Code: ```
sudo update-alternatives --config java
```. My launcher works fine until I log in, then the whole thing turns black and adds onto m terminal saying Code: ```
sam@Falcon:~$ java - jar minecraft.jar
Unrecognized option: -
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.
sam@Falcon:~$ java jar minecraft.jar
Error: Could not find or load main class jar
sam@Falcon:~$ java.jar minecraft.jar
java.jar: command not found
sam@Falcon:~$ java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:1029)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.forkAndExec(Native Method)
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:135)
    at java.lang.ProcessImpl.start(ProcessImpl.java:130)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:1021)
    ... 1 more
27 achievements
174 recipes
Setting user: <USERNAME>, -1351797700117757918
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/sam/.minecraft/bin/natives/liblwjgl.so: libjawt.so: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1924)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1821)
    at java.lang.Runtime.load0(Runtime.java:792)
    at java.lang.System.load(System.java:1059)
    at org.lwjgl.Sys$1.run(Sys.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:132)
    at net.minecraft.client.Minecraft.a(SourceFile:187)
    at net.minecraft.client.Minecraft.run(SourceFile:644)
    at java.lang.Thread.run(Thread.java:722)

``` The added bit is after 27 achievements. Any help?

---

