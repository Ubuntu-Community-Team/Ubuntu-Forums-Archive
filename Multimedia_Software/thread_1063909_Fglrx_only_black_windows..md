---
title: "Fglrx only black windows."
date: 2009-02-08
forum: Multimedia Software
---

### Post by Cobra_Fast on 2009-02-08
Hello,

i just upgraded from 8.04 to 8.10 and i was very happy to see this:
```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.8087 Release

```

and this:
```

$ glxinfo | grep direct
direct rendering: Yes

```

BUT all 3D applications i start open up in a black window and even if i wait a while nothing appears.

glxgears gives me 1100 to 1800 FPS but only a black window.

No errors in */var/log/Xorg.0.log* and no errors in *dmesg | grep fglrx*

At last my xorg.conf:
```

Section "ServerLayout"
	Identifier     "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "aticonfig-Screen[1]" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "vbe"
	Load  "i2c"
	Load  "ddc"
	Load  "bitmap"
	Load  "extmod"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier  "Generic Keyboard"
#	Driver      "kbd"
#	Option	    "XkbRules" "xorg"
#	Option	    "XkbModel" "pc105"
#	Option	    "XkbLayout" "de"
#	Option	    "XkbVariant" "nodeadkeys"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier  "Configured Mouse"
#	Driver      "mouse"
#	Option	    "Name"		"Razer Copperhead"
#	Option	    "Vendor"		"Razer"
#	Option	    "CorePointer"	"true"
#	#Option	    "Protocol"		"ExplorerPS/2"
#        #Option      "ZAxisMapping"	"4 5"
#        Option      "Device"      	"/dev/input/mice"
#        #Option      "Buttons"       	"7"
#        #Option      "ZAxisMapping"  	"6 7"
#        #Option      "ButtonMapping" 	"1 2 3 6 7"
#	Option	    "Resolution"	"2000"
#	Option	    "SampleRate"	"1000"
#EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "SwapScreens" "off"
	Option	    "SWCursor"	  "1"
	#Option	    "HWCursor"	  "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "SWCursor"	  "1"
	#Option      "HWCursor"	  "off"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth	24
		Virtual 1280	1024
		Modes	"1280x1024@85"	"1280x1024@80"
		#Option	"HWCursor"	"off"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		#Viewport   0 0
		Depth     24
		Modes	"1280x1024@60"
		#Option	"HWCursor"	"off"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
#	Option		"AIGLX"		"off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

and an uname -a:
```
Linux gaming 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

---

### Post by Cobra_Fast on 2009-02-08
Bump

---

### Post by Cobra_Fast on 2009-02-09
Bumpedybump ...
I really need 3D!

---

### Post by Cobra_Fast on 2009-02-10
Bumpedybumybumpumpbump ... !

---

