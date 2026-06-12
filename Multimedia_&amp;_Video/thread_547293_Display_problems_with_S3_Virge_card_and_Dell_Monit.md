---
title: "Display problems with S3 Virge card and Dell Monitor"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by bovardc on 2007-09-09
I recently installed Ubuntu 7.04 on my PC with an S3 Virge video card and Dell E173FP LCD monitor.

Initially, I could only get 640X480 and 800X600 screen resolutions, but with some forum searching I added the Horizontal and Vertical rates to my xorg.cong file.  Now I have a full list of resolutions to choose from, but now I get tons of screen artifacts flickering each time the screen redraws.  The values I put into the config file match the specs from Dell, so now I'm at a loss.  Below are the relevant sections from my xorg.conf file. 

 Can anyone help?

Thanks!

Section "Device"
	Identifier	"S3 Inc. 86c325 [ViRGE]"
	Driver		"s3virge"
	BusID		"PCI:0:9:0"
EndSection

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
	HorizSync       31-80
        VertRefresh     56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c325 [ViRGE]"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

