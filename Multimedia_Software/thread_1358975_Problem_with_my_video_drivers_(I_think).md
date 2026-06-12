---
title: "Problem with my video drivers (I think)"
date: 2009-12-19
forum: Multimedia Software
---

### Post by brigzzy on 2009-12-19
Hey all

So I'm having a problem with what I think is my video drivers.  I have 2 ATI Radeon 4870s, with a monitor plugged into both.  After some tweaking to my xorg.conf file, I was able to get both working, but I'm not sure if my video drivers are working right.  I'm getting lag when I drag windows around, and with the login animation (I should say that I'm running 9.10, 64 bit).  I also can't enable compiz.  I've tried installing the latest drivers from the ATI site, and the restricted drivers from Administration -> Hardware Drivers in the menu.  Can anyone shed some light on my problem?  Below is my xorg.conf.

```

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

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen-1"
	Device     "aticonfig-Device-1"
	Monitor    "aticonfig-Monitor-1"
	DefaultDepth	24
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

Section "Module"
	Load  "glx"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "1"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen-1" 0 0
	Screen         "aticonfig-Screen-2" 1680 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device-1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

Section "Device"
	Identifier  "aticonfig-Device-2"
	Option	    "Monitor-DFP2" "1-DFP2"
	BusID       "PCI:2:0:0"
	Driver	"fglrx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

```

Thanks you for your time.

---

