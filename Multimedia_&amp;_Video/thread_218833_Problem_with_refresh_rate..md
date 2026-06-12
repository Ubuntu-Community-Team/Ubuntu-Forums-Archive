---
title: "Problem with refresh rate."
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by Nasef on 2006-07-19
First time Ubuntu user. So I'm having a little tough time getting the refresh rates right for my monitor. 

I've installed Ubuntu yesterday, on one of my home PCs as a try out. I've a 17" Samsung 753s [CRT] monitor and my AGP is Nvidia FX5200. I've always used a screen resoluation of 1280x960@72Hz when I was on Windows XP. So after insalling ubuntu I found out that it'd only allow me to use 1280x960@60Hz, it dose not gives me any other options for refresh rate under that resoluation, however I've choices like 1152x864@75Hz etc. etc. 

Can any one help me resolve this issue with refresh rate that I'm facing ?

My "xorg.conf" 
-------------
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
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
---------------------------------------------------

Any help would be appriceated.

---

### Post by tseliot on 2006-07-19
Try this:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

