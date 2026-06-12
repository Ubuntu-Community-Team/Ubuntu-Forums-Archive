---
title: "dual monitor with toshiba tv wl66"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by dejanpan on 2007-10-12
Hi there, 

i have a "Trident Microsystems CyberBlade XPAi1" graphic card and would at first like to get dual-monitors (2 different desktops) over the VGA 2nd output running on my toshiba laptop. I've modified xorg.conf file whose section with monitors' setup now looks like this:
........................
Section "Device"
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Driver		"trident"
	Option "XAANoOffscreenPixmaps"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
       Identifier "Dev1"
       Driver "trident"
      BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-90
	VertRefresh	43-90
EndSection

Section "Monitor"
    Identifier "tv" 
    Option "DPMS"
    HorizSync 28-90
    VertRefresh 43-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XPAi1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
    Identifier "TV Screen"
    Device "Dev1"
    Monitor "tv"
    DefaultDepth 24
    SubSection "Display"
    Depth 24 
    Modes "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#	Screen		"Default Screen"
	Screen 		"Default Screen"
	Screen 		"TV Screen" LeftOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Alps Touchpad"
EndSection
...............................................................
Can anybody tell me what I am lacking above that it does not work? All I can get is a clone of my principal desktop and that also without any "tv monitor" lines.

Further more, the 2nd display should be a Toshiba WL66 Lcd Widescreen TV (1366x768, equvivalent to 16:9 ratio) and when connected I can only get it in the 1024x780 resolution (eq. to 4:3 ratio). Does anybody have any clue how to get it run in a full-screen mode, i.e. 1366x768?

greets, D.

---

