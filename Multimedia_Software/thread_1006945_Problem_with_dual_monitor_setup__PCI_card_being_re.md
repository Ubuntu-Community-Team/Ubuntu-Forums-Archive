---
title: "Problem with dual monitor setup / PCI card being read"
date: 2008-12-09
forum: Multimedia Software
---

### Post by NYCE on 2008-12-09
Hello,

I've been searching and trying solutions when I have time since Sunday. At this point I haven't gotten anywhere. 
This is a fresh install of Ubuntu 8.10 on a Dell Dimension  5150. I'm using the built in intel card for primary monitor and trying to use an ATI card for my second monitor. Built in and PCI ATI card are as follows:



```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
03:02.0 VGA compatible controller: ATI Technologies Inc Rage 128 RK/VR

```

The ATI card right now is not working at all. The monitor light is still orange, it's also not showing up under preferences > screen resolution

sudo gedit /etc/X11/xorg.conf gives the following:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Referred to a lot of links that didn't help. Many going back as far as 05 so some of the informaiton was no longer valid. I also tried to follow some of the information that was applicable here [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) but that didn't work. Also I'm not even sure that applied as my second monitor doesn't even work as of yet. Any feedback or information to help my search would be appreciated.

Also know it's not the newest card or anything but will suit for what I want to use it for which is nothing intensive.

---

### Post by NYCE on 2008-12-11
After searching around some more I found a command Xorg -configure

With that it populated more information about my system, but then it just gave a blank screen on my main monitor and still nothing on the second. Looking at the xorg.conf it had different busids for my card then when I put lspci | grep VGA. I changed it to the information that is shown when running that command and my main monitor came on and still nothing for the second. With main monitor it showed "(ee) no devices detected."

I tried to search for that and said my monitor info was probably wrong. I tried to edit but still no luck.

This is last thing I ended up with.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
	Load  "xtrap"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName "Plug'n Play"
	ModelName "Dell E193FP"
	Option       "DPMS"

	HorizSync 30-83
	VertRefresh 56-76
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName "Plug'n Play"
	ModelName "Dell E193FP"
	Option       "DPMS"

	HorizSync 30-83
	VertRefresh 56-76
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:00:02.0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "Display"            	# <str>
        #Option     "PanelWidth"         	# <i>
        #Option     "PanelHeight"        	# <i>
        #Option     "ProgramFPRegs"      	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
	Identifier  "Card1"
	Driver      "r128"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage 128 RK/VR"
	BusID       "PCI:03:02.0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Also tried different drivers for the cards. Still no luck. At this point I'm just going to put XP back on this computer as I've exhausted everything I can think or found with what I searched for. 

A Mac is still my main comp. We'll see what happens.

---

