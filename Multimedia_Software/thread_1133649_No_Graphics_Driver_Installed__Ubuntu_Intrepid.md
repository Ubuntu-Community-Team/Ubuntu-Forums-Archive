---
title: "No Graphics Driver Installed // Ubuntu Intrepid"
date: 2009-04-23
forum: Multimedia Software
---

### Post by mattcantgetsome on 2009-04-23
Hello, recently I have been attempting to fix my screen resolution problems. I have noticed that Ubuntu automatically starts up with an incorrect resolution at the start-up screen, and remains until I open the "Screen resize and rotate" program, only then does it go to the correct setting. I've tried to remedy this by auto-starting the KRandR-Tray program at startup, but it causes a sudden jump in the graphics, as well as the resolution still being incorrect at the initial startup. Call me picky, but...

Anyway, I've heard that I can simply edit the x.org file, which I tried. But when I open it up, there is no graphics card detected. Well, nothing specific, anyway. This is the whole file:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

There's nothing specific listed here, and that worries me... should it? I have noticed that a lot of the games I have installed via Synaptec don't work correctly due to buggy graphics, which causes them to constantly crash. Here's some specs:

Intel 910GL onboard graphics card
Ubuntu Intrepid
KDE 4
Pentium 4 processor

Anyone know what's going on with this? I would appreciate some assistance, thanks

Matt

---

### Post by markharding557 on 2009-04-23
what are the games you tried to run if they need opengl then you need ati or nvidia these are well supported on linux

---

### Post by plroit on 2009-04-25
I have the same problem,
please anyone, help

I have intel 945 express chipset (on my thinkpad t60)
with intel 950GMA graphic chip

I also try to use a dual monitor setup
with a SyncMaster 2253BW

My xorg.conf looks almost the same
> 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Please help!

---

### Post by Monotoko on 2009-04-25
Try running:

```
glxinfo | grep "OpenGL"
```

from the terminal and post the output here

---

### Post by plroit on 2009-04-25
The output is here:
> 
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10
OpenGL extensions:

---

