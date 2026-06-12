---
title: "Radeon X600 Pro - Big Desktop?"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by bowenweb on 2007-07-11
I've been struggling now for several days to get my ATI X600 Pro video card to produce a 'big desktop', and I'm spent.  Right now, my monitors are mirrors of each other, but I want one large desktop that spans both screens.  This is as close as I've gotten.  

The Viewsonic LCD is my main monitor, and looks best (in WinXP) at 1280x1024.  The secondary KDS-V7P CRT looks better (again, in XP) at 800x600.  

Here's my current xorg.conf (I have a few of them :) ):

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Screen0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "KDS VS-7p"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier	"VIEWSONIC"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Mode2" "1280x1024"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]secondary"
	Driver		"fglrx"
	BusID		"PCI:1:0:1"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"KDS VS-7p"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]secondary"
	Monitor		"VIEWSONIC"
	DefaultDepth	24
	
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "0"
EndSection
```

I'm new to Linux/(K)Ubuntu, but learning by trial and error!  Thanks in advance for any advice!!

---

