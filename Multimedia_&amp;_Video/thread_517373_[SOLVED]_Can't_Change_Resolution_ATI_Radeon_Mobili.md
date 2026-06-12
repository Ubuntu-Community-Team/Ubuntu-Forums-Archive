---
title: "[SOLVED] Can't Change Resolution: ATI Radeon Mobility X700"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by jmstevenson on 2007-08-04
A portion of my Ubuntu partition recently got corrupted. I reformatted, reinstalled and upgraded from edgy to feisty in the process. Everything works fine save monitor resolution. With the default install, I was able to change resolutions, but anything over 1024x768 caused lots of problems. I switched to fglrx, as is recommended and now anything over 1024 simply doesn't appear as an option in the screen resolution control panel. (fwiw, I can only switch between 640, 800 and 1024). I spent some time on the forums looking for answers and made some changes to xorg.conf based on recommendations in some other posts but nothing seems to work.  When I was using fglrx on edgy, I was able to use higher resolutions, so what gives? I'm including the relevant portion of my xorg.conf file below. Any help would be much appreciated as the laptop I'm using (Gateway 8510gz) has a pretty big display and 1024 is just too low to be useful.

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier "Generic Monitor"
        Option "DPMS"
        HorizSync 31.5-91.1
        VertRefresh 60-100
        Modeline "1680x1050@60" 162.00 1680 1704 1792 2136 1050 1201 1204 1249 +hsync +vsync
        Modeline "1440x900@60" 162.00 1440 1464 1552 2136 900 1201 1204 1249 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280×960@60"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280×960@60"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280×960@60"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280×960@60"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

---

### Post by iamvinhamese on 2007-08-05
i have the same problem with the same exact laptop. i couldnt stand the 1024x768 so i uninstalled. someone please help jmstevenson so you can help me

---

### Post by jmstevenson on 2007-08-07
Here's the fix; I discovered it myself trying different things in xorg.conf. The resolutions  declared in the "Monitor" and "Screen" sections should match. So if you have this:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31.5-91.1
VertRefresh 60-100
Modeline "1680x1050@60" 162.00 1680 1704 1792 2136 1050 1201 1204 1249 +hsync +vsync
Modeline "1440x900@60" 162.00 1440 1464 1552 2136 900 1201 1204 1249 +hsync +vsync
EndSection

You need this:

Section "Screen"
SubSection "Display"
Depth 24
Modes "1280×960@60" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

This allows you a max res of 1280x960 @ 24 bits, 60Hz

---

