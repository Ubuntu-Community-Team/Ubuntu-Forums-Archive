---
title: "Youtube Red Flashes"
date: 2009-07-19
forum: Multimedia Software
---

### Post by cooper77z on 2009-07-19
Lately, whenever I try to watch a youtube video there are intermittant little flashes of red quotation marks. It's really irritating and I was wondering if this is somthing wrong with my video set up or if this is some kind of new adobe encryption. I wonder if I just downloaded the video with youtube -dl if the flashes would go away when I watched the youtube video with totem.

---

### Post by n00ti on 2010-04-07
editing /etc/X11/xorg.conf fixed it for me:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" 
	EndSubSection
EndSection

---

