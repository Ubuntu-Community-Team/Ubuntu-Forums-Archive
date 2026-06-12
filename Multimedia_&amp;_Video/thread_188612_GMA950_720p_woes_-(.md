---
title: "GMA950 720p woes :-("
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by Thingi on 2006-06-04
I can't seem to get 1280x720 working in dapper..... 915 resolution won't help because 1280x720 isn't even a valid mode using this util. How do I achieve 1280x720? 

I know my custom modeline works ok, it's been used before on breezy on a ppc mac mini.

Here's my current xorg.conf, it seems to be completely ignored my res is always set to 1280x1024 - my monitor will display it but it's 4:3 and not the native res of my widescreen lcd monitor/tv (via VGA port).

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

Section "Module"
	Load       "dbe"   # Double buffer extension
    	SubSection "extmod"
      	Option   "omit xfree86-dga"   # don't initialise the DGA extension
	EndSubSection
	Load	"type1"
	Load	"freetype"
#	Load	"glx"
#	Load	"dri"
#	Load	"i2c"
#	Load	"bitmap"
#	Load	"ddc"
#	Load	"int10"
#	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
#	Driver		"vesa"
	VideoRam	32768
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"NEXGEN NL27"
#	Option		"DPMS"
	HorizSync	30-64
	VertRefresh	56-75
	Modeline "1280x720" 74.160 1280 1352 1392 1648 720 725 730 750 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"NEXGEN NL27"
	DefaultDepth	24
	
	SubSection "Display"
		Depth		24
		Modes		"1280x720" 
		ViewPort 	0 0 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

# Section "DRI"
#	Mode	0666
# EndSection


help!!!!!!!!!!! please!!!!!!!!!!!

thingi

---

### Post by Thingi on 2006-06-04
Well I think I've setup 915resolution correctly now. 

I added "/usr/sbin/915resolution 5c 1280 720 32" to my /etc/init.d/bootmisc.sh

and altered my xorg.confi to this:-

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	VideoRam	65536
	BusID		"PCI:0:2:0"
Option "ForceBIOS" "1280x1024=1280x720"
EndSection

Section "Monitor"
	Identifier	"NEXGEN NL27"
	Option		"DPMS"
	HorizSync	30-64
	VertRefresh	56-75
	Modeline "1280x720" 74.160 1280 1352 1392 1648 720 725 730 750 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"NEXGEN NL27"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x720" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Yet still xwindows still absolutely insists on booting into a 1280x1024 mode ](*,) 

Any ideas?

---

