---
title: "resolution stretched and very ugly"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by eewald on 2006-07-15
Hello, 
I have installed Ubuntu Dapper on a new laptop which has wide screen. But monitor only works on a 1024x768 resolution, which, as you understand, makes everything on a screen appear stretched. Circle drawn in Inkscape is oval, faces on pictures appear fat etc. 

And yet I have written 1152x768 on my xorg.conf file, but I receive no error messages nor proper resolution... ](*,). 

Here is a section of my xorg.conf file: ```

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-57
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by bigken on 2006-07-15
in the treminal run dpkg-reconfigure xserver-xorg and select your resolution using the space ;)

---

### Post by tseliot on 2006-07-15
> **bigken said:**
> in the treminal run dpkg-reconfigure xserver-xorg and select your resolution using the space ;)

using "sudo" is required unless you boot in recovery mode. Therefore you should type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by elettronicha on 2006-07-15
I'm not a gnome user, but maybe, once you've modified xorg.conf, you have to choose the correct resolution in the gnome system preferences.

---

