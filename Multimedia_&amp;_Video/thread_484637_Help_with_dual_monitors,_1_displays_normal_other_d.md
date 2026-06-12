---
title: "Help with dual monitors, 1 displays normal other displays 1 line of code"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by darth rave on 2007-06-26
I am trying to setup Dual monitors using Xinerama and it just isn't working :(
I have an Ati radeon x1300 and an integrated nvidia Geforece 6150 LeE and an Hp f15103 monitor and my default HP vs1e monitor

The line the secondary monitor (hp f1503) is showing says

```

RV515PRO 102-A67618-10 A12 Hynix DDR2 BIOD 600e/396m Channel AB

```

Here's my xorg.conf file 

```


Section "ServerLayout"
	Identifier     "Multihead"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" LeftOf "Screen0"
	InputDevice    "Configured Mouse" "CorePointer"
	InputDevice    "Generic Keyboard" "CoreKeyboard"
	Option		"Clone"		"off"
EndSection

Section "ServerFlags"
Option "xinerama" "true"
Option "DefaultServerLayout" "Multihead"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "record"
	Load  "xtrap"
	Load  "dbe"
	Load  "glx"
	Load  "GLcore"
	Load  "dri"
	Load  "extmod"
	Load  "type1"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "freetype
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"
	#DisplaySize	  330   270	# mm
	Identifier   "Monitor0"
	VendorName   "HWP"
	ModelName    "HP vs17"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    30.0-61.0
	VertRefresh  50.0-76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "HWP"
	ModelName    "HP f1503"
	HorizSync	30-61
	VertRefresh	50-76
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "C51 PCI Express Bridge"
	BusID       "PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card1"
	Driver      "vesa"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV515 PRO [ATI Radeon X1300/X1550 Series]"
	BusID       "PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth    24	
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"
	EndSubSection	
	
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultDepth    24	
	SubSection "Display"
		Depth	16
		Modes			"1024x768"	"800x600"
	EndSubSection	
	
	SubSection "Display"
		Depth	24
		Modes			"1024x768"	"800x600"
	EndSubSection
EndSection

```

please help me, I have been trying this since Friday, I have read like every tutorial out there

Thanks in advance

---

