---
title: "wide screen problem"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by rajeshphadke on 2007-08-31
I have:

Motherboard: DG33FB
ViewSonic LCD Wide Screen : VG1921wm

KuUbuntu 7.04

Display detected as VESA

Unable to get Wide Screen resolution working.

Can someone help?

---

### Post by jclmusic on 2007-08-31
open a terminal and run ```
sudo gedit /etc/X11/xorg.conf
```

find the "screen section". it should look like this by default (ur video card will probably be different):
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"E19T5W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1024x768" "832x624" "800x600" "720x400" 
	EndSubSection
EndSection
```

replace all of those numbers with just the resolution u want, so it looks like this (using my resolution of 1400x900 as an example):

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"E19T5W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection
```

---

### Post by rajeshphadke on 2007-09-06
Hi,

Tried settings suggested by you.  Problem is xorg over rides these settings and still continues with 1024x768, 800x600 etc.

Can you Help?

Thanking You.

Yours Sincerely,

Rajesh

---

### Post by Gremlinzzz on 2007-09-06
[http://www.spickles.org/archives/2006/10/31/95/](http://www.spickles.org/archives/2006/10/31/95/)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by rajeshphadke on 2007-09-14
Problem Still there.  Tried to install back  ported .deb but not getting installed on 64 bit system

---

### Post by BlueFusionX on 2007-10-08
(deleted)

---

