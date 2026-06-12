---
title: "How to make display resolution bigger than 1024x768"
date: 2009-06-15
forum: Multimedia Software
---

### Post by bastones on 2009-06-15
Just installed Ubuntu on Mac Mini Core Solo, all seems to work fine except my screen resolution ( on my non-Apple flat screen 15" ) is stuck at a maximum of 1024x768, there's no bigger resolution setting in Display preferences. Is there any way I can make it any bigger - on my laptop Ubuntu resolution is set at 1280x800 or something, which is the sort of resolution I'd like. If it helps, here's my xorg.conf file contents:

> Section "Device"
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

In Display current settings are, if you need to know them:

Res 1024x768(4:3) (biggest option avail)
Refresh rate 60Hz (no other option)


Thanks.

---

### Post by bastones on 2009-06-16
anyone?

---

### Post by planetLars on 2009-06-16
see [http://ubuntuforums.org/showthread.php?t=1013209]("http://ubuntuforums.org/showthread.php?t=1013209") (post #5 and #6) but note [http://ubuntuforums.org/showthread.php?t=1187965]("http://ubuntuforums.org/showthread.php?t=1187965").

Find the ideal resolution and perhaps rate settings for your display (online manual, Windows driver inf) and add the mode to xrandr if xrandr alone doesn't show the best mode for you.

Regards

Lars

---

