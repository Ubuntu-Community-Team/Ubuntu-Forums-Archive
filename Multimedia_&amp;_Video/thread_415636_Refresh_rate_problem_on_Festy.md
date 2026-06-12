---
title: "Refresh rate problem on Festy"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by barmazal on 2007-04-20
Graphics card : Nvidia 6600GT AGP
Monitor: LG Flatron F700p

Restricted Modules enabled, resolution is fine but refresh rate is quite low

this is my xorg.conf related stuff

```

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-80
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection
```


as you can see Monitor undefined + 	Driver	"nvidia"  (don't know if it should be nv or nvidia)

How i get proper refresh rate like 85hz as i had before?

many thanks

---

### Post by shawnrgr on 2007-06-03
try running "nvidia-settings" in a terminal. also driver should be set to "nvidia" if you have nvidia-glx or legacy drivers installed.

---

### Post by Nythain on 2007-06-03
look up your monitors specs and possibly change the horizsync and vertrefresh values... the seem kind of low, you should be able to get higher than 60hz

---

