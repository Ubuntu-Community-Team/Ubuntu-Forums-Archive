---
title: "Yet another Ati driver problem..."
date: 2009-03-30
forum: Multimedia Software
---

### Post by johneporro on 2009-03-30
Hi everyone. First i would like to apologize for yet another one of this anoying threads.

The problem here is that I've been trying to make the ATI proprietary drivers to work, with no efective results. Already tryied with the manual install, activate the one's that with ubuntu and EnvyNG.
 I can get them installed, but can not get them to work what so ever. 

Heres some info: 

fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: **RADEON X800 GTO**
OpenGL version string: 1.4 (2.1.8087 Release)

xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

(Yes, this is all there is on xorg.conf)

If neef for more info, just ask. Thanks and sorry for my not-soo-good english (not my native lenguaje)

---

### Post by Entity` on 2009-05-18
My problem is this:
Whenever I install either the proprietary driver for my 4850, I get a nasty screen flicker and my 3rd cpu pegs out.  Worse, I can't change resolutions without the effect becoming worse or permanent.  I think this may have something to do with my xorg.conf file as it only shows this:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```

Im not sure thats right.

Right now Im trying to manually install the new 9.5 drivers, but the sh command returns a "cant open file" when I try to configure the ati_driver.run file.

Any help is greatly appreciated.

---

