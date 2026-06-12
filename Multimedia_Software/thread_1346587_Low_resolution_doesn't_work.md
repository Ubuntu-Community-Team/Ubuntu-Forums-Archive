---
title: "Low resolution doesn't work"
date: 2009-12-05
forum: Multimedia Software
---

### Post by ripedar on 2009-12-05
Hi i have tried game Solar Wolf. When i started it my screen went black and control light on monitor start flashing. So i just pressed CTRL+ALT+Backspace and got back to desktop. I tried it again and it happens again. But i tried ALT+Enter. Game went from fullscreen to window mode and worked normal. Tried it on other game with low resolution and same problem. Can't play them fullscreen if they're under or 800*600 resolution. How to fix it? I didn't have this problem under windows on this computer. (Same hardware and monitor)

How to enable low resolutions?

here is my xorg.conf
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Mouse0" "CorePointer"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#	InputDevice    "Keyboard0" "CoreKeyboard"
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
	Load  "glx"
	Load  "record"
	Load  "xtrap"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Identifier  "Keyboard0"
#	Driver      "kbd"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#	Identifier  "Mouse0"
#	Driver      "mouse"
#	Option	    "Protocol" "auto"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "ZAxisMapping" "4 5 6 7"
#EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor0"
	VendorName   "IBM"
	ModelName    "IBM T750"
	HorizSync    30.0 - 81.0
	VertRefresh  55.0 - 75.0
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
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NV31 [GeForce FX 5600]"
	BusID       "PCI:1:0:0"
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

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

---

### Post by xc3RnbFO8P on 2009-12-05
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=1226901]("http://ubuntuforums.org/showthread.php?t=1226901")

---

