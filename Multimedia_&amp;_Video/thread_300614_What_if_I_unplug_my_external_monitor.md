---
title: "What if I unplug my external monitor?"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by risknet on 2006-11-15
Hello,

I am using Ubuntu 6.10 on my HP laptop with an external 19inch wide monitor.  Currently, the resolutions are set up as follows:

1440 x 900
1024 x 768
800 x 600

This external monitor is always connected to my laptop, and I will always get 1440 x 900 resolution.   But, what if I unplug this external monitor from the laptop and reboot the system?   Am I able to the following available resolution, 1024 x 768, automatically?

My HP laptop's max resolution is 1024 x 768.   

Thank you for your help in advance.

== risknet ==

---

### Post by CowzRule on 2006-11-16
If you post a copy of your "xorg.conf" file we'll be able help you alot easier. That will tell us how everything is set up and what options to add or change.
Also, take a look at [this post]("http://www.ubuntuforums.org/showthread.php?t=221174")

---

### Post by risknet on 2006-11-16
This is my setting in xorg.conf file.

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
 	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by CowzRule on 2006-11-16
In this section:```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
 	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  	Modeline [COLOR="Red"]"1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync[/COLOR]
EndSection
```Try changing the line in red to:```
[COLOR="Blue"]"1024x768_85.00"  106.47  1024 1280 1440 1520 904 932 1024 768 -HSync +Vsync[/COLOR]
```

---

