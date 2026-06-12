---
title: "TV-out on ATI Radeon 9250 with integrated ATI Radeon HD4200, Karmic"
date: 2010-04-06
forum: Multimedia Software
---

### Post by samcan on 2010-04-06
Hello,

My motherboard has an integrated ATI Radeon HD4200. I have the closed-source drivers installed for that video card, and a generated Xorg.conf:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
	Option      "HSync2" "75.0"
	Option      "VRefresh2" "60.0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200"
	EndSubSection
EndSection


```

The problem is, I'm trying to put an ATI Radeon 9250 in as a secondary video card. I'd like to be able to use both the CRT and TV-out. I know that only the open source driver works with the 9250 on Karmic, but I'm okay with that. I'm having troubles however, getting the proper xorg.conf. I looked at the page [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting), however, it's not working.

Matters are complicated by the fact that both the video cards are ATI-manufactured. Does anyone have any suggestions?

Thank you.

samcan

---

