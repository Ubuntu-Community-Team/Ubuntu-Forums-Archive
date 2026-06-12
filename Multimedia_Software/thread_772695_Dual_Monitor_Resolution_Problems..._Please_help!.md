---
title: "Dual Monitor Resolution Problems... Please help!"
date: 2008-04-28
forum: Multimedia Software
---

### Post by parahost on 2008-04-28
I am new to ubuntu and I cannot change my resolution on my dual monitors. I want my resolution to be 2048x768. (1024x768 for each panel).

Here are my specs:

Card: Radeon 9600
Driver: ATI supplied driver
OS: Ubuntu 8.04
Monitors: Two SyncMaster 740bx
Current Resolution: 2560x1024


My current setup is BigDesktop. when I go to system->preferences->screen resolution I only have the options 2560x1024, 1280x1024, 1280x768, 1024x768, and it goes down from there.

Here is my xorg.conf file. I have read and tried to change so many things using trial and error and I cannot get to that resolution. When I change stuff it normally doubles the resolution (I was adding a virtual command in there). If you could help I would greatly appreciate it!

```


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
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
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x1024+1280x1024,1024x768+1024x768"
	Option	    "EnableMonitor" "crt1,tmds1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by parahost on 2008-04-28
Anyone? Any help is appreciated

---

### Post by off1 on 2009-03-28
I have the same question. 

Anyone???

THANX

---

