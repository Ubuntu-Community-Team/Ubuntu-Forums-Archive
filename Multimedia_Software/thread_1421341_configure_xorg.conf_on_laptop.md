---
title: "configure xorg.conf on laptop"
date: 2010-03-04
forum: Multimedia Software
---

### Post by salva99 on 2010-03-04
Hello to all

I conected a tv to my laptop [compaq c770]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01412643&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3696215&lang=en") but it just show the desktop in black & white.
I solved it with this command
```
xrandr --output TV1 --set mode PAL
``` because my tv is PAL and the mode was setting as NTFS
But every time I connect de tv to my laptop I must entry that code.

I'm using Ubuntu 9.10 and I didn't find the file xorg.conf. I created it with that command ```
X -configure
``` and editing the xorg file:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
	Load  "dri2"
	Load  "record"
	Load  "dbe"
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
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: : integer, : float, : "True"/"False",
        ### : "String", : " Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# []
        #Option     "SWcursor"           	# []
        #Option     "ColorKey"           	# 
        #Option     "CacheLines"         	# 
        #Option     "Dac6Bit"            	# []
        #Option     "DRI"                	# []
        #Option     "NoDDC"              	# []
        #Option     "ShowCache"          	# []
        #Option     "XvMCSurfaces"       	# 
        #Option     "PageFlip"           	# []
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"

##I added it---- start
	Option "TVStandard" "PAL"
	Option "TVOutFormat" "SVIDEO"
	Option "ConnectedMonitor" "TV1"
##end

	BusID       "PCI:0:2:0"
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
```

It doesn't work. Somebody know what I am doing wrong?

---

