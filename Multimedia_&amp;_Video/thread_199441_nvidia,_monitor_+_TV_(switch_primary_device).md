---
title: "nvidia, monitor + TV (switch primary device)?"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by casperlingus on 2006-06-18
I went through the HOW-TO in one of the other forums for setting up dual-display.  I'm sure this was answered somewhere in the 21 pages of replies, but I really don't have time to go through it.  Simply put, I just want to know if there is a command I can put in xorg.conf which will switch the primary output of the video card.  Perhaps there's a configuration setting elsewhere.

I'm using a GeForce 6600, and for some reason it believes the SVIDEO connection is the primary one.  Using my regular xorg.conf, I have to physically disconnect the svideo cable from the TV to get it to display to the monitor.  When using dual monitors, everything works except that it puts my primary desktop on the TV.  I've tried a variety of things, but no matter what I do, the login screen pops up on the TV and my normal desktop is on the TV as well.

This really can't be as hard as hard as it seems...

Casper...

---

### Post by casperlingus on 2006-06-18
Of course someone is going to ask for my xorg.conf... my bad

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
   Option      "Buttons" "7"
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
        screen      0
	BusID		   "PCI:1:0:0"
        Option      "RandRRotation" "on"
EndSection

Section "Device"
	Identifier	"Device[1]"
	Driver		"nvidia"
        Screen      1
        Option      "TVOutFormat" "SVIDEO"
        Option      "TVStandard"  "NTSC-M"
        Option      "ConnectedMonitor" "Monitor[1]"
	BusID		   "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" # Samsung 19" LCD 
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Monitor"
        Identifier "Monitor[1]" # TV
        HorizSync 30-50
        VertRefresh 60
EndSection


Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen" 
   	Identifier "Screen[1]" 
   	Device "Device[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	   Screen 0		"Screen[0]" 
	   Screen 1		"Screen[1]" LeftOf "Screen[0]"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by SentientFluid on 2006-06-18
Mind sharing the link to the How-To for getting Dual displays to run at all? I have 2 17" monitors that work fine in XP, but I have no clue how to set them up to work in Dapper. :(

---

### Post by casperlingus on 2006-06-19
[http://www.ubuntuforums.org/showthread.php?t=98456](http://www.ubuntuforums.org/showthread.php?t=98456)

Upon second glance, this HOWTO is for setting up a **TV** as a second monitor (if you have an NVidia card).  However, after having gone through it to set up the TV, it looks like it would be easy to adapt to a regular dual-monitor setup.  Although I'm sure there's another dual-monitor setup guide somewhere that could be followed for the less-experienced.

Casper...

---

### Post by casperlingus on 2006-06-21
Bump.

This really can't be that hard.... is it???

---

### Post by rumli on 2006-08-20
Try putting a ```
Option "UseDisplayDevice" "DFP, CRT"
``` in the "Device[0]" Device section.

And put a ```
Option "UseDisplayDevice" "TV"
``` in the "Device[1]" Device section.

See this page for more documentation on the UseDisplayDevice and ConnectedMonitor options.

---

