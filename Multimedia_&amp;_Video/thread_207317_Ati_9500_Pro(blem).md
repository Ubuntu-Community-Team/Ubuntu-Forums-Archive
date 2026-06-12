---
title: "Ati 9500 Pro(blem)"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by mevan on 2006-07-01
Hello!

I have recently done a clean install of Ubuntu 6.06 and I have a problem with GL acceleration. Whenever a 3D application starts (including screensavers) it runs for 2 seconds and then the computer freezes. It comes up again only with hardware reset!!! My card is an Ati 9500 Pro (ati radeon 300-based) and it works OK under Ubuntu 5.10 and windows XP

```
mevan@Deimos:~$ glxinfo | grep direct
No ctx->FragmentProgram._Current!!
direct rendering: Yes
mevan@Deimos:~$

```

This is my xorg.conf file:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L1915S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R300 AD [Radeon 9500 Pro]"
	Monitor		"L1915S"
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

Any suggestions?? I have thought about installing an ATi prop. driver but I'd like to know if there is another solution

---

### Post by whatever on 2006-07-01
the freezing is a bug in the reverse engineered r300 dri.
if you need stable accelerated opengl you have to use fglrx (the proprietary ati driver).

fglrx install: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by mevan on 2006-07-01
I see.. I will install the fglrx driver.. Do you suggest a specific version, or should I try the latest?

Thanx!

---

