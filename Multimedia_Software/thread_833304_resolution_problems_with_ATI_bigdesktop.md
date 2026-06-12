---
title: "resolution problems with ATI bigdesktop"
date: 2008-06-18
forum: Multimedia Software
---

### Post by iamfletch on 2008-06-18
I have followed [http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174") and have struggled to get both monitors working with the correct resolutions.

I have a x1800 ATI radeon.
A dell 22" DVI wide-screen 1680x1050 (E228WFP)
and a dell 19" VGA (plugged in using a DVI converter) screen 1280x1024 (E193FP)

I have got fglrx 8.493 on Ubuntu hardy 8.04.

My first screen 1680x1050 displays fine, the other screen is in 1024x768 and no matter what Options i add/change in xorg.conf it wont change.

Also when i look at screen resolution it says 3360x1050 (other settings are 2048x768 and all the other standard resolutions), i guess this is supposed to be 2960x1050.

Here is my xorg.conf file.
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
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	HorizSync    31.4 - 80.0
	VertRefresh  56.0 - 75.0
	ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
	ModeLine     "1280x1024" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	#Option	    "VendorName" "ATI Proprietary Driver"
	#Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "0x0+0x0,1024x768+1024x768,1680x1050+1280x1024"
	Option	    "EnableMonitor" "crt2,tmds2i"
	Option	    "ForceMonitors" "crt2,tmds2i"
	Option	    "OverlayOnCRTC2" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1280X1024"
	EndSubSection
EndSection

```

---

