---
title: "No Driver Line in xorg.conf"
date: 2009-01-28
forum: Multimedia Software
---

### Post by krt on 2009-01-28
Having installed the "nvidia binary xorg driver (new)",  "nvidia x server settings" as well as "hardware drivers",  I got a notice that said "/etc/X11/xorg.conf" Device Section "Configured Video Device" must have driver line.

Since my video is not optimum (text rendition when on line in FF where "appearance" font controls have no effect), I am posting the relevant sections of xorg.conf, because I have not a clue as to what to do to clean up the video. "Configured Video Device" apparently is not sufficient.
--------------------------------------------
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
--------------------------------------------
Any suggestions as to what to do here would be greatly appreciated. Video card is nvidia FX5200.

Thank you,

krt

---

