---
title: "dual monitors radeon 9700 help"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Inquisitr on 2007-08-26
hey I just got Compiz fusion working and I've been trying to get my second monitor going now as my next challenge.

I've tried the guide at 
[http://ubuntuforums.org/showthread.php?t=301961](http://ubuntuforums.org/showthread.php?t=301961)

but all that did was make my resolution really small and still with the second monitor only giving a cloned display.

here's the relevant sections of my xorg.conf


```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"L70B"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"L70B"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


Any help at all would be appreciated, I've tried every guide I can find on getting this working.  Hell even if I have to start fresh get dual monitors working and then get compiz working I won't mind.

---

### Post by Inquisitr on 2007-08-27
shameless bump, still can't get dual monitors working

---

### Post by Inquisitr on 2007-08-27
Bump again

---

