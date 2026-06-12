---
title: "1280x1024 in Xubuntu?"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by kombucha on 2007-07-01
I can't figure out how to set a resolution of 1280x1024 in Xubuntu... with the same xorg.conf, I was running at that resolution in Kubuntu, so there must be some other roadblock between xorg.conf and the display settings page, which gives me some 1280x... options but no ...x1024 options. Any ideas?

Here's the relevant chunk of xorg.conf:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync 	30-70
 	VertRefresh 	50-130
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Thanks!

---

### Post by Clay_Banger on 2007-07-13
open the terminal and copy and paste this in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
select the ati driver then select using the space bar, the resolutions in that list that you wish to use.
Then reboot.

---

### Post by kombucha on 2007-07-23
I'm not going to lose any other configuration this way, like xorg.conf settings?

---

