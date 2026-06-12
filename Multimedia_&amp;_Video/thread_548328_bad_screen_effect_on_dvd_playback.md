---
title: "bad screen effect on dvd playback"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by auralay on 2007-09-11
Greetings
I have a Dell Inspiron 510m with lintel 855GM graphics.
All is fine and I can use the full 1280 x 1024 resolution.
BUT except when I try to play DVDs.
 the display is covered in a matrix of black dots- it's like trying to watch through a net curtain. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
This happens in window and full screen modes.
My xorg.conf shows

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection

I have downloaded all the codecs using Automatix and Easyubuntu
I tried updating the i810 driver as shown here
[http://ubuntuforums.org/showthread.php?t=269052&highlight=855+graphics](http://ubuntuforums.org/showthread.php?t=269052&highlight=855+graphics)
This has no effect.
I looked at the 915resolution program but this doesn't seem to address the problem.

Please help! Thanks, jg.

---

### Post by auralay on 2007-09-11
Sorry - should have said I am using Feisty + latest updates.

---

