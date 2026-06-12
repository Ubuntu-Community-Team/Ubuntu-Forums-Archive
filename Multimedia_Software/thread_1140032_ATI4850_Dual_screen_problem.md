---
title: "ATI4850 Dual screen problem"
date: 2009-04-27
forum: Multimedia Software
---

### Post by killerasp on 2009-04-27
i have a ATI4850 on Ubuntu 9.04. just installed the latest ATI drivers with no problems and ran aticonfig with dual-head config. but now, my screen is showing some weird issues. each of my screen is now an independent desktop. each screen has its own task bars, its down application list, etc. i cant drag apps from one screen to another. i can move my mouse from one screen to another and open apps in each of the displays. virtual desktops are independent of each other. i can be in virtual desktop 2 on screen 1. but on screen 2, i can be in virtual desktop 1 all at the same time. 

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen       0  "aticonfig-Screen[0]-0"
	Screen       1  "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
	Option 	    "CloneDisplay" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

#Section "Screen"
#	Identifier "Default Screen"
#	Device     "Configured Video Device"
#	Monitor    "Configured Monitor"
#	SubSection "Display"
#		Virtual   3200 1200
#	EndSubSection
#EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Modes "1600x1200"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Modes "1600x1200"
		Depth     24
	EndSubSection
EndSection


```


Any suggestions. i just want to span my desktop across both screens.

---

### Post by Boris32 on 2009-04-27
Hi,

Unfortunately, the propriety drivers for ATI are not very good. In order to get the dual screen to work properly, you'll need to deactivate the ATI supplied driver and use the open source driver.  (System->administration->Hardware drivers).

Once you've done this, you can use the Display configuration tool (System->preferences->Display) to setup dual screen. (You may need to log out and log back in again).

I hope this helps you.

---

