---
title: "Dual head config doesn't stick."
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by Phreakin on 2007-09-11
I almost hate to post ANOTHER thread about ATI dual head issues but i'm running out of patience. I have an ATI X-850 with dual head enabled. Here's the important part of my current config:

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Centermode" "off"
	Option	    "PseudoColorVisuals" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
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

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

As of right now, I have both monitors running in a cloned config after every startup. I can only get dual head by using the ATI CCC utility from the desktop. It will set the display to the correct settings until I reboot. At that time, it goes back to being cloned. I thought for some reason it may be an issue that for some reason it wasn't writing the config to xorg.conf but even doing sudo amdcccle and running it has no effect.

Also doesn't show up when running fglrxinfo:

```

phreakin@soundwave:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT
OpenGL version string: 2.0.6747 (8.40.4)

```

Anyone have a clue?

---

### Post by Phreakin on 2007-09-12
Anyone? Pretty please? :P

---

