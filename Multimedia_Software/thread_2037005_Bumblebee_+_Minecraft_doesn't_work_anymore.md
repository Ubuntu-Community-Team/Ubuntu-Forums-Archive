---
title: "Bumblebee + Minecraft doesn't work anymore"
date: 2012-08-03
forum: Multimedia Software
---

### Post by Spitfire777 on 2012-08-03
Hi,

After a long time I started playing minecraft again. I have Nvidia hybrid gaphics and it usually works very well with bumblebee.

But Minecraft does not work anymore with bumblebee. It works only without the optirun prefix. With the optirun prefix, the screen turns black.
I've tried the OpenJDK and the Sun-JDK.

Here's the output:
```
michael@michael-K53SV:~$ optirun minecraft
27 achievements
195 recipes
Setting user: XXXXXXXXXXXXXXX, 9087237244783087111
LWJGL Version: 2.4.2
org.lwjgl.LWJGLException: Could not choose GLX13 config
        at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
        at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
        at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
        at org.lwjgl.opengl.Display.create(Display.java:854)
        at org.lwjgl.opengl.Display.create(Display.java:784)
        at net.minecraft.client.Minecraft.a(SourceFile:224)
        at net.minecraft.client.Minecraft.run(SourceFile:516)
        at java.lang.Thread.run(Thread.java:722)
org.lwjgl.LWJGLException: Could not choose GLX13 config
        at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
        at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
        at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
        at org.lwjgl.opengl.Display.create(Display.java:854)
        at org.lwjgl.opengl.Display.create(Display.java:784)
        at org.lwjgl.opengl.Display.create(Display.java:765)
        at net.minecraft.client.Minecraft.a(SourceFile:233)
        at net.minecraft.client.Minecraft.run(SourceFile:516)
        at java.lang.Thread.run(Thread.java:722)

```

---

