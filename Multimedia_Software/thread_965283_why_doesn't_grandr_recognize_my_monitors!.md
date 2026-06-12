---
title: "why doesn't grandr recognize my monitors?!?"
date: 2008-10-31
forum: Multimedia Software
---

### Post by anystupidname on 2008-10-31
I have a Dell P991 and M993S which are two very similar CRTs. At one point, grandr and gnome's System>Prefs>Screen Resolution utility identified the M993S properly but never the P991 and I've been messing with xorg.conf and now both monitors are "unknown". Since adding the monitor sections in xorg.conf, the appropriate resolutions are available for the M993S even though it is "unknown"... The P991 has very few resolutions available and they are for a widescreen monitor instead of a 4:3 which the P991 is... Any assistance would be much appreciated...

I attempted to work from this:
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

here is my xorg.conf

```

Section "Monitor"
	Identifier	"L"
	Option		"LeftOf" "R"
	VendorName   "Dell"
	ModelName    "Dell P991"
	HorizSync    30.0 - 107.0
	VertRefresh  48.0 - 120.0
	Gamma        1
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Monitor"
	Identifier	"R"
	Option		"RightOf" "L"
	VendorName   "Dell"
	ModelName    "Dell M993s"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
	ModeLine     "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	ModeLine     "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
	ModeLine     "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	ModeLine     "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"S0"
	Device	"D0"
	SubSection "Display"
		Modes	"1600x1200@75" "1280x1024@75" "1024x768@85" "800x600@85"
		Virtual	3200 1200
	EndSubSection
EndSection

Section "Device"
	Identifier	"D0"
	Driver		"radeonhd"
EndSection

```

---

### Post by Dougie187 on 2008-10-31
You have an ATI Radeon card right? Isn't there a proprietary config utility for those?

---

### Post by anystupidname on 2008-10-31
You are likely thinking of aticonfig. I don't see how that would help with monitor detection though.

---

