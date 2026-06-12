---
title: "Radeon X1300 Hardy Heron Issues/Problems"
date: 2008-12-26
forum: Multimedia Software
---

### Post by cjspartacus on 2008-12-26
So, I've been running around the internet trying to find a solution for this, and I think I've only succeeded in making the problem worse.  Anyway, here's what happened.  I upgraded to Hardy a while back now, and when I did, compiz stopped working.  I never got around to attempting to fix it until now.  My system specs are listed in the title.

In attempting to fix it, I did some fiddling with xorg.conf and also moved a link because it was suggested that the link was outdated and needed to be updated or something like that.  For a long time I was getting a segmentation fault (without a core dump).  Anyways, the link update was accomplished with the following command:

[HTML]sudo mv /usr/lib/xorg/libGL.so.1 /tmp/[/HTML]

Things worked until I rebooted.  Now, whenever I run fglrxinfo I get the following output:

[HTML]display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

Segmentation fault[/HTML]


I tried reinstalling ATI Catalyst Control Center, but all that did was succeed in updating the xorg.conf file to:


[HTML]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection[/HTML]




So that is where I'm at right now.  Any specific ideas or help would be greatly appreciated.

---

