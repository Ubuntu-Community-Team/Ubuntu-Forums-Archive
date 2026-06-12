---
title: "[fglrx] Cann`t set 1280x960 screen resolution"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by xixx on 2007-03-09
My system: ubuntu edgy, video card: ATI RADEON 9600pro, video drivers: fglrx 8.34.8. After installation of fglrx i cann`t set the 1280x960 screen resolution (this problem was on older fglrx versions too), but if i set back standard ati drivers everything is ok. I trying to set 1280x960 throw modeline in xorg.conf, but it doesn`t work... And in xorg logs file evereything  is ok, without any errors...

This is a part ofmy xorg.conf:

Section "Monitor" 
Identifier "DELL D1226H" 
Option "DPMS" 
HorizSync 30-95 
VertRefresh 50-160 
Modeline "1280x960" 167.84 1280 1368 1576 1952 960 960 963 1011 +hsync +vsync 
EndSection 

Section "Screen" 
Identifier "Default Screen" 
Device "ATI Technologies, Inc. RV350 AP [Radeon 9600]" 
Monitor "DELL D1226H" 
DefaultDepth 24 
SubSection "Display" 
Depth 24 
Modes "1280x960" 
EndSubSection 
EndSection

---

### Post by petaskeeta on 2007-05-12
Bump, i'm having the same exact problem

Feisty, fglrx 8.34.8 on a Radaeon 9800 pro

Can't get 1280x960 to work at all.

Tryed to do a ModeLine as well. Here are some of my settings:

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	# V-freq: 85.00 Hz  // h-freq: 85.99 KHz
	Modeline "1280x960" 167.84  1280 1368 1576 1952   960  960  963 1011 
EndSection

ection "ServerFlags"ection "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth		1
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
EndSection
```

---

