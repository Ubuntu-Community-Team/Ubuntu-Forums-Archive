---
title: "Minecraft crashing under hybrid graphics card =("
date: 2012-04-27
forum: Multimedia Software
---

### Post by ajscholten on 2012-04-27
So I'm VERY new to ubuntu and just got Precise today and am now trying to play Minecraft. It worked under 32bit Oneiric with only a small graphics error during game play. Now that I have installed Precise though it just gives me an error when trying to start Minecraft. As I mentioned in the title I am running a hybrid graphics card.
```
LWJGL Version: 2.8.3
org.lwjgl.LWJGLException: X Error - disp: 0x7f69bc1c5ff0 serial: 24 error: BadRequest (invalid request code or no such operation) request_code: 154 minor_code: 14
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:316)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:782)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:871)
    at org.lwjgl.opengl.Display.create(Display.java:782)
    at net.minecraft.client.Minecraft.a(SourceFile:204)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:722)
org.lwjgl.LWJGLException: X Error - disp: 0x7f69bc1c5ff0 serial: 31 error: BadRequest (invalid request code or no such operation) request_code: 154 minor_code: 14
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:316)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:782)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:871)
    at org.lwjgl.opengl.Display.create(Display.java:782)
    at org.lwjgl.opengl.Display.create(Display.java:764)
    at net.minecraft.client.Minecraft.a(SourceFile:236)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:722)
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f6a2573fc58, pid=17690, tid=140093898135296
#
# JRE version: 7.0_03-b147
# Java VM: OpenJDK 64-Bit Server VM (22.0-b10 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea7 2.1.1pre
# Distribution: Ubuntu precise (development branch), package 7~u3-2.1.1~pre1-1ubuntu2
# Problematic frame:
# C  [libX11.so.6+0x33c58]  XQueryExtension+0x28

```This is with Java 7, but Java 6 did the same thing.

```
$ lspci -v | grep -A 10 -B 1 VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 04ca
    Flags: bus master, fast devsel, latency 0, IRQ 55
    Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

--

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] (prog-if 00 [VGA controller])
    Subsystem: Dell Device 04ca
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7b20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7b00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

```Help? :(

---

