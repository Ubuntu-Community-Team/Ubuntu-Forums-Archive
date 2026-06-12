---
title: "Trouble with Xinerama"
date: 2009-12-20
forum: Multimedia Software
---

### Post by brigzzy on 2009-12-20
Hey everyone, I hope I'm putting this in the right forum.  

I'm having a problem with setting up dual monitors on my 9.10 system.  I have two Radeon HD 4870s, and a monitor plugged into each of them.  It seems that after a lot of tampering with my xorg.conf file, I've managed to get Xinerama working, but everything looks kind of... bad.  I get lag when I drag windows around, and I have no compiz effects.  If I disable Xinerama, I can have to seprate X enviroments, with compiz running in each one, but I can't share windows between them.  A lot of googleing has revealed that this is kind of a hit and miss sort of problem, and some people can get it configured, but some can't.  So before I give up, I thought I'd ask here first.  Below is a copy of my xorg.conf file.  Thank you in advance :)

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen-1" 0 0
	Screen      1  "aticonfig-Screen-2" RightOf "aticonfig-Screen-1"
	Option	"Xinerama"	"True"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor-2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device-2"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen-1"
	Device     "aticonfig-Device-1"
	Monitor    "aticonfig-Monitor-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen-2"
	Device     "aticonfig-Device-2"
	Monitor    "aticonfig-Monitor-2"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Brigzzy

---

### Post by schmolch on 2009-12-21
There is nothing wrong with your configuration.
Xinerama disables compiz and slows down everything.

---

