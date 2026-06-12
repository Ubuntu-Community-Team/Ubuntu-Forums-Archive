---
title: "Unable to set screen resolution"
date: 2008-08-11
forum: Multimedia Software
---

### Post by davethewave83 on 2008-08-11
I read the article at [http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) but my xconf already contains a wide list of resolutions. These resolutions are not showing up under my system prefs, screen resolutions. It only goes up to 1024x768. I need a higher res to configure dtc, because the dtc configuration gui goes off screen in 1024x768 and cannot be scaled smaller. Can anyone tell me how to get a higher resolution than 1024x768 please? 
These are all the modes available in my xorg: 
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Toshiba"
	Modelname	"Toshiba DP782M, Equium 17-inch Monitor"
	Horizsync	30.0-82.0
	Vertrefresh	50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
```
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"1024x768@85"	"1024x768@60"	"832x624@75"	"1024x768@43"	"800x600@60"	"1152x864@75"	"800x600@85"	"1280x1024@75"	"800x600@75"	"1280x960@60"	"800x600@72"	"1280x1024@60"	"800x600@56"	"1280x960@75"	"640x480@85"	"1400x1050@60"	"640x480@75"	"1400x1050@75"	"640x480@72"	"1600x1200@65"	"640x480@60"	"1600x1200@60"
	EndSubSection
EndSection

```

So any ideas why it won't show up in my resolution settings please let me know :)

---

### Post by davethewave83 on 2008-08-13
No takers? :)

---

### Post by UltraAnders on 2008-08-16
I am by no means an expert ... I still have a problem with my setup, but x.org might be deciding the modeline is invalid. Post the contents of /var/log/Xorg.0.log and I (or more likely someone else more clever!) might be able to help.

I've found verbose logging very useful:
[http://ubuntuforums.org/showpost.php?p=5553849&postcount=6](http://ubuntuforums.org/showpost.php?p=5553849&postcount=6)

Are you using dual-screens?

---

