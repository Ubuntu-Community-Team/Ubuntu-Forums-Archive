---
title: "All full screen games and movies sluggish"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by biohypnotix on 2007-08-02
No matter which ATI drivers I use, the default bundled with Ubuntu or the restricted ones my frame rate is suffering in full screen mode for games and movies. In games I have around 10 frame rate at max resolution of 1280x1024 which is unplayable (even 2d games) and full screen movies flickers and jumps around and are unwatchable. The card works fine under Windows XP so I'm sure I'm missing something in Ubuntu. Any help would be great, I used google and searched these forums, but being a newbie maybe I overlooked something.

O/S: Ubuntu Feisty 7.04
CPU: 1.3 GHz
RAM: 2 GB
GFX: ATI Radeon 9600 (256MB)

Movies: All formats (DVD, DivX, etc.) (Using VLC)
Games: Any full screen game (3D and 2D)

lspci

> 
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)



xorg.conf

> 
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"A70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"A70"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection


---

### Post by gerbman on 2007-08-02
What does```
fglrxinfo
```output?

---

