---
title: "Widescreen Acer Monitor"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by TooEarly on 2007-07-15
I just bought a new 19inch Acer Widescreen monitor.
I have an ATI Radeon 9200 graphics card (old I know..)

My monitor is plugged into my graphics card through the DVI port. I don't know if that have an significance but might as well say it.

I plugged it in thinking that everything was going to work perfectly! 
But nope, I plug it in, loads fine. I get to the KDE screen and it starts up and every time I move my mouse or do something it flickers. I'm using the Radeon drivers. The quick solution was to do the dpkg-reconfigure xserver-org and use the vesa drivers. That works fine, but when I try to play video's it's all choppy. 

Also I tried to do my own Modeline in my xorg.conf and turn DDC to "false" but when I did that it didn't display anything. Which doesn't make sense. 

I don't know what else to do..

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"radeon"
	BusID		"PCI:0:8:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	31.0-80.0
	VertRefresh	56.0-75.0
	Option		"DPMS"
	Option		"DDC" "false"
	Modeline	"1440x900" 136.8 1440 1536 1688 1936 900 903 909 942
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x960"
	EndSubSection
EndSection

```

---

