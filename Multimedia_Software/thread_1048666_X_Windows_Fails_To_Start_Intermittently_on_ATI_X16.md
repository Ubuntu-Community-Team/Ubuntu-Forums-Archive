---
title: "X Windows Fails To Start Intermittently on ATI X1650"
date: 2009-01-23
forum: Multimedia Software
---

### Post by Strike Team on 2009-01-23
My PC has a Core 2 Duo CPU, Gigabyte GA 965P-S3 motherboard and ATI X1650 display adapter. OS is Ubuntu 8.10, kernel version 2.6.27-9-generic.

X Windows only starts about 50% of the time, otherwise the PC attempts to change screen modes then comes up with a full-screen TTY command prompt.

Looking in /etc/X11, xorg.conf was last updated on January 15th. xorg.conf.failsafe was last updated today.

Xorg.conf and xorg.conf.failsafe are identical:

-------------------------------------------------
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
----------------------------------------------------

I haven't attempted to install drivers yet, I want to get this sorted first. Where do I go from here? All thoughts and ideas appreciated.

---

### Post by Strike Team on 2009-01-24
Problem solved - I installed the driver and it works fine now.

This is the sort of bug that needs sorting if Ubuntu is ever going to really be able to replace Windows for the average, non-technical user. Unlike Ubuntu, XP does function reliably using the basic in-built VGA driver. I hit a similar problem a while ago, when Ubuntu refused to recognise a serial mouse unless xorg.conf was manually edited. By contrast, the mouse worked perfectly under XP.

---

