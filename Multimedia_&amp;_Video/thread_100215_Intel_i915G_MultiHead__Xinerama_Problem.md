---
title: "Intel i915G MultiHead / Xinerama Problem"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by notW1seman on 2005-12-07
Hi all,
I am running 5.10 version and madly trying to get xinerama on my intel graphics board.
it is the intel I915G, with VGA Port  and an additional DVI Port - board.
Monitors are two flat screens, an FSC P17-1 and a HP 1740 (17" TFT monitors with a max of 1280x1024)

I already searched about this topic in this forum, but i am obviously still missing a thing.

When starting x, i get the error message "You must have a MonitorLayout defined for use in a DualHead or Clone Setup"
At the bottom, you find the graphics stuff of my xorg.conf
One thing i am not perfectly sure is whether the screen 0 and 1 devices are the DVI and VGA ports opr vice verse. as the two connect tft screen have more or less the same features it shouldn't matter too much, i suppose.

I am an X newbie (i used to work on ibm's aix and suse linux just in a non-x server environment) - and want to start migrating my ms windows to ubuntu. nevertheless, dualhead is important for me.

thanks a lot for any suggestions,
claudius

Section "Monitor"
	Identifier	"P17-1"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"HP1740"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"DVIDevice"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Screen 0
EndSection

Section "Device"
	Identifier	"VGADevice"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Screen 1
EndSection

Section "Screen"
	Identifier	"DVIScreen"
	Device		"DVIDevice"
	Monitor		"HP1740"
	DefaultDepth	24
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"VGAScreen"
	Device		"VGADevice"
	Monitor		"P17-1"
	DefaultDepth	24
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection



Section "ServerLayout"
	Identifier	"Multihead"
	Screen		"DVIScreen"
        Screen          "VGAScreen" Rightof "DVIScreen"
	InputDevice	"Generic Keyboard"
        InputDevice	"Configured Mouse"
        Option          "clone" "off"
        Option          "Xinerama" "on"

EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by notW1seman on 2005-12-07
jaja, i should've tried some hours more....
so: i finally was able find the MonitorLayout stuff and solved the problem.
After trying some parameters, this is what helped:
- removed the Open "ConnectedMonitor" in the two device section
- Added: Option "MonitorLayout" "CRT,DFP" in the screen 0 device section.
(figuring the right combination of CRT,DFP MFC etc.etc. took me some time and nerves)

then, my assumption the screen 0 is the DVI and screen 1 is VGA port was wrong. it is - as always -the other way round.
hence, the "main" screen with login window and gnome menus is the monitor connected to the VGA port, so the DVI port is for the secondary screen.

seems that in ms windows there is a possiblity to change that (easier) as my main screen there is the one connected to the DVI.

however, i am happy for the moment. if i find a possibility to change main output to dvi i will post an update.

have fun. be save.
claudius

"ubuntu rocks"

---

### Post by starscalling on 2005-12-10
you should be able to define one display as rightof or leftof the other

---

