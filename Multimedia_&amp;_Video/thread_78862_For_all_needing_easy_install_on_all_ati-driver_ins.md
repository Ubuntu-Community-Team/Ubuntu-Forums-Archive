---
title: "For all needing easy install on all ati-driver install"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by allupinya on 2005-10-19
This, is the best and fastest way i have found to get them right every-time!:D 
I am now 3-d "golden" on 2 ATI and Ubunto 5.10 loaded machines!

Go to [this]("http://ubuntuforums.org/showthread.php?t=75428") thread

Install them just like he says.
Down at the end where he says to "Change the ATI to FGLRX means in the begining of fglrxconfig
It look like it defaults to ATI. Go down the list and choose fglrx instead...

The only two things i add is, to use the:   frame buffer= "yes"   and also config monitor in "simple" mode
I installed it three times on each machine, to make sure...
Machine 1.
Intel plll 750 1 gig ram ..Via chipset and ATI AIW-9200, also i got multi monitor support:D "Its my video and web server"

Machine 2.
AMD 3.2 barton...ATI X800 XT PE...nvidia chipset, lan, soundstorm.
Also have dual monitor support

Worth a try.
only took me 5 mins on each machine

gears (planetary)  Went from 179 fps to over 2000 fps

Good luck hope it helps.;)

---

### Post by allupinya on 2005-10-19
well after waking up and playing some call of duty.
The new drivers do pretty well..
Quick edit Oh and for al you resolution guys...1600X1200 @ 85 Hz

Here is the  Xorg.conf it it can help anyone.

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
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
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
	VideoRam	262144
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

