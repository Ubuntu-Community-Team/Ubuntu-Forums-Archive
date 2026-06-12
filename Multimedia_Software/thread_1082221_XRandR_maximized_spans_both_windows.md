---
title: "XRandR maximized spans both windows"
date: 2009-02-27
forum: Multimedia Software
---

### Post by intru on 2009-02-27
After days of frustrations I finally have a decently working dual monitor setup with my Radeon HD4850 on Hardy 64bit edition. I'm using the latest ATI drivers in combination with XRandR. Using a little script I automatically run 'xrandr --output DFP2 --auto --right-of DFP1'.

The only problem with this setup is that when I maximize an application it will span both monitors. I would like it to only span the active monitor (like with BigDesktop). Using BigDesktop is unfortunately not an option due to [this problem]("http://ubuntuforums.org/showthread.php?t=1058944").

Anybody has a clue how to fix this? I'm using this xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
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
	Option	    "CorePointer"
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
		Virtual   2560 1024
	EndSubSection
EndSection

```

---

### Post by intru on 2009-03-02
Anybody who knows a fix for this? It's really annoying. A lot of programs start up on half of both of my screens, and dragging and resizing them all the time gets quite frustrating. There must be more people with this problem?

---

### Post by relix on 2009-03-06
I can confirm this problem, using 8.10 and HD3470, and the latest driver from the Ati site. I've tried for hours changing settings without getting any further.

---

