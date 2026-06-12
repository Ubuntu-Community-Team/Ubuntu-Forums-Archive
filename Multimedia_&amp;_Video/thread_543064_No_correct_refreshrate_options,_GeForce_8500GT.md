---
title: "No correct refreshrate options, GeForce 8500GT"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by MockY on 2007-09-04
I have a GeForce 8500GT and a NEC Multisync 97F.

Even though I use correct drivers and I added the correct HorizSync and VertRefresh from the monitor manual. I want to run in 1280x1024 but no matter what I do, I can't come over 61Hz using Vesa and 60 Using Nvidia. I have tried everything I know and researched, but yet I have to ask for help.

Anyone?

```
Section "Monitor"
	Identifier	"MultiSync 97F"
	Option		"DPMS"
	HorizSync	31-70
	VertRefresh	55-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GeForce 8500"
	Monitor		"MultiSync 97F"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

