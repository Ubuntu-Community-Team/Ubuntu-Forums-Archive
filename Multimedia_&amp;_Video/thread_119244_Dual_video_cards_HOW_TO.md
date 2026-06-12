---
title: "Dual video cards HOW TO???"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by jasondbA on 2006-01-19
Hi all;
I have a AGP and PCI video card installed in my PC. Both use the Nvidia Drivers. My problem is that all i get after i have edited my xorg.conf file is the bios info on the second display, full time, it never changes from that. The other display works fine. I am trying to get Xinerama working. Here is relevent part of my xorg.conf file. if somebody could help me out with this little issue please. Oh the AGP one is the one with the issues.
Thanks in advance.
> 
Section "Device"
	Identifier	"primary"
	Driver		"nv"
	BusID		"PCI:0:10:0"
EndSection

Section "Device"
	Identifier	"secondary"
	Driver		"nv"
	BusID		"AGP:1:0:0"
EndSection

Section "Monitor"
	Identifier	"crt"
	HorizSync	61
	VertRefresh	120
EndSection

Section "Monitor"
	Identifier	"tft"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"first"
	Device		"primary"
	Monitor		"tft"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
EndSection





Section "Screen"
	Identifier	"second"
	Device		"secondary"
	Monitor		"crt"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"first"
	Screen		"second" RightOf "first"
	Option		"Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


---

