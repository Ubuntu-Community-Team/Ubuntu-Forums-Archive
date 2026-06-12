---
title: "fglrx ignores xorg.conf settings"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by ac4000 on 2006-09-17
In my xorg.conf, I have explicitly defined only two video modes for each of the heads in my Radeon 9800 Pro, but no matter what I do, fglrx seems to ignore those settings and load with its own ideas (these messages followed by a list of Modeline statements that are *not* what I told it:
```

(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 30 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)

```
I've been searching for an answer to this for about a week now and I still can't seem to resolve it.  Many solutions to similar problems seem to involve setting modes and a bug in fglrx, but I've tried the mode settings and the bug supposedly relates to a different version of the driver.  I've tried all of these to no avail:
```

        Option          "MonitorLayout" "NONE,NONE"
        Option          "NoDDC"
        Option          "UseEdidFreqs" "0"
        Option          "IgnoreEDID" "on"
        Option          "TMDS" "0"
        Option          "HSync2" "15-93"
        Option          "VRefresh2" "38-150"

```
My xorg.conf is in the next post.  Any ideas?  I feel like pulling my hair out!  I really, really, *really* don't want to say this was easier in Windows, but at this point, it definitely was.  Please help me change that!

---

### Post by ac4000 on 2006-09-17
Here's my xorg.conf; thanks for looking!

```

# SERVER FLAGS
Section "ServerFlags"
  Option "Dont Zoom"
	Option		"NoDDC"
	Option		"UseEdidFreqs" "0"
	Option		"IgnoreEDID" "1"
	Option		"TMDS" "0"
EndSection


# LAYOUT
Section "ServerLayout"
	Identifier	"Projector On"
	Screen		"Desktop Screen"
	Screen		"Projector Screen" Above "Desktop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerLayout"
	Identifier	"Projector Off"
	Screen		"Desktop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


# VIDEO CARD HEADS
Section "Device"
        Identifier      "ATI R350 NH [Radeon 9800 Pro] (Primary)"
        Driver          "fglrx"
        Option          "MonitorLayout" "NONE,NONE"
	Option		"NoDDC"
	Option		"UseEdidFreqs" "0"
	Option		"IgnoreEDID" "on"
	Option		"TMDS" "0"
	Option		"HSync2" "15-93"
	Option		"VRefresh2" "38-150"
	Option          "VideoOverlay" "on"
	Option          "OpenGLOverlay" "off"
	Option          "OverlayOnCRTC2" "1" # true? on?
        BusID           "PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
        Identifier      "ATI R350 NH [Radeon 9800 Pro] (Secondary)"
        Driver          "fglrx"
        Option          "MonitorLayout" "NONE,NONE"
	Option		"NoDDC"
	Option		"UseEdidFreqs" "0"
	Option		"IgnoreEDID" "on"
	Option		"TMDS" "0"
#	Option          "VideoOverlay" "off"
#	Option          "OpenGLOverlay" "on"
#	Option          "OverlayOnCRTC2" "0"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection


# MONITORS
Section "Monitor"
	Identifier	"Princeton SENergy 714"
	VendorName	"Princeton"
	ModelName	"SENergy 714"
	Option		"DPMS"
	HorizSync	24-82
	VertRefresh	55-77
	# Recommended
	Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
	# Maximum
	# Modeline "1280x1024@69" 140.00 1280 1312 1840 1872 1024 1044 1056 1076
EndSection

Section "Monitor"
	Identifier	"Sony VPH-1272Q"
	VendorName	"Sony"
	ModelName	"VPH-1272Q"
#	Option		"DPMS" "false"
	HorizSync	15-93
	VertRefresh	38-150
	# Film x2 (48 fps); V-freq: 48.00 Hz  // h-freq: 47.45 KHz
	Modeline "1280x960@48" 79.77 1280 1312 1608 1640 960 980 988 1009 -hsync -vsync
EndSection


# SCREENS
Section "Screen"
	Identifier	"Desktop Screen"
	Device		"ATI R350 NH [Radeon 9800 Pro] (Primary)"
	Monitor		"Princeton SENergy 714"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Projector Screen"
	Device		"ATI R350 NH [Radeon 9800 Pro] (Secondary)"
	Monitor		"Sony VPH-1272Q"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x960@48" "1280x960"
	EndSubSection
EndSection


# FILES
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


# MODULES
Section "Module"
	Load	"bitmap"
	Load	"dbe"
#	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection


# INPUT
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection


# DRI
Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ac4000 on 2006-09-18
I think I've found the problem (though not a solution) and it's pretty obscure, which is why most people probably can't address it.  I'm posting here in the hopes that it might help someone else (well, at least the knowledge might be useful).  There appears to be a bug in the fglrx driver and that bug has been there for quite some time.  ATI hasn't bothered to fix it.  Essentially, in dual-head setups, the driver ignores any custom modeline settings and reads (incorrect) EDID data.  This is more than just a little annoying when the specific modes you want are not supported (e.g., 1280x960@48Hz).  You can read all about it [here]("http://ati.cchtml.com/show_bug.cgi?id=160") (the summaries of the problem are toward the end).

So that's the issue; now if you'll allow me a bit of editorializing:  I've used ATI cards for probably more than 10 years and, for Windows, I quite liked them.  After giving up Windows for good, however, and seeing the mess ATI calls fglrx, I'm pretty sick of it and I'd have to say it's probably preferable to dump them and go for a company that actually tests its drivers.

---

### Post by Icarosaurus on 2006-11-19
I had the same issue setting custom video modes: the solution was to revert from fglrx 8.30 to 8.28 (the default fglrx of edgy).
Actually I did a new intallation of the whole Edgy...but for other causes.

You're right: it seems ATI doesn't actually tests it's drivers for linux.
I noticed that my Radeon 9600 doesn't go well with new Catalyst drivers under Windoz too. So I use an old version of drivers.

Moreover I tested Quake 4 under linux...and video drivers don't seem to work as they do in Windoz....

---

