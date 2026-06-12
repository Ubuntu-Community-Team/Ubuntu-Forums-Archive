---
title: "sample xorg.conf file for use"
date: 2010-04-16
forum: Multimedia Software
---

### Post by caymahallesi on 2010-04-16
I needed an example of xorg.conf file and I couldn't find one that is working. Here is mine after getting working;


Section "Device"
        Identifier "Card0"
	BoardName "Intel-mobile-video"
	VendorName "Intel"
	Driver "Intel"

EndSection

Section "Monitor"
        Identifier      "Monitor0"
	HorizSync 38-75
	VertRefresh 50-75

EndSection

Section "Screen"
        Identifier      "Screen0"
        Monitor         "Monitor0"
        Device          "Card0"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x768" "1024x768" "800x600"
	EndSubSection


EndSection

---

