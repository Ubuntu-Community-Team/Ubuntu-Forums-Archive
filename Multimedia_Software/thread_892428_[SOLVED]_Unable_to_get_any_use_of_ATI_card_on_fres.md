---
title: "[SOLVED] Unable to get any use of ATI card on fresh install of Hardy"
date: 2008-08-17
forum: Multimedia Software
---

### Post by greenknight117 on 2008-08-17
I have just reformatted with fresh install after I followed an unofficial ATI wiki and completely trashed my previous install. Many threads and Ubuntu help just say to go to restricted drivers in sys/admn and select ATI. I have no restricted drivers listed in my menu. I have installed ATI binary driver and fglrx control and still have not made it anywhere. here is my xorg.conf:
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

This is my card:

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)

I am going to rely on the official forums so that I don't trash my settings again. I hope there is help!

---

### Post by overdrank on 2008-08-17
Hi and welcome, the driver that comes install with Hardy should work. There is no support for ATI cards older than the 9500 by ATI. If you are trying to use compiz (desktop effects) then you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
You may also use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
``` there you can view what driver is being used and adjust the resolution.

---

### Post by Kevbert on 2008-08-17
Same card... Here's my xorg.conf display settings which work fine:
```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection
```

---

### Post by greenknight117 on 2008-08-17
I will just have to do without affects

---

### Post by greenknight117 on 2008-08-17
i guess i have to work on wifi now

---

### Post by greenknight117 on 2008-08-17
sorry trying to figure things out

---

