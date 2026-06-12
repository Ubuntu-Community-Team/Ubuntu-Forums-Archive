---
title: "Black Border around output with ATI 9100 IGP"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by arsenic0 on 2007-11-27
So i have everything working for the most part but i am having one issue that i need help with.

System Specs
Asus Pundit R
ATI 9100 IGP
Ubuntu 7.1

Hooked up through the VGA Connector to my Samsung 56" 1080p DLP's VGA/PC input(max res 1920x1080@60hz)

I have the card outputting at 1920x1080@60hz, but i have a small black border maybe 1 inch all around my output.  So i need to sort of "stretch" the image to fit the rest of the screen.  With my TV i am able to adjust the left/right/up/down positioning but not stretch or skewing.  Whats funny is this is the exact opposite problem i had on my other PC with an Nvidia card hooked up to this TV from DVI->HDMI..it overscanned quite a lot and i had to make modelines to shrink it to fit the screen properly.

Any help you can give to stretch this bad boy out would be great, oh and no matter what resolution i set it too i have this border.


Included below is my Xorg.conf, i am unsure why 1920x1080 is not listed in the modes, its what Ubuntu says i am running at right now. And as i said above the border is always there regardless of res, so if i can get rid of it i can figure out if i am really at 1920x1080 after.

Section "Files"
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
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon 9100 IGP"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SAMSUNG"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon 9100 IGP"
	Monitor		"SAMSUNG"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by arsenic0 on 2007-11-27
And my Xorg log

I couldnt attach the whole thing due to the file limit, but this is the last section that seemed most important :)

---

