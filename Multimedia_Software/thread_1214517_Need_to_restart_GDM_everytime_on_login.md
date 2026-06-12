---
title: "Need to restart GDM everytime on login"
date: 2009-07-16
forum: Multimedia Software
---

### Post by Zer0Nin3r on 2009-07-16
Searched and searched and couldn't find anything.  Here's a short rundown.

[LIST]
[*]Enabled compiz on my Toshiba U405d Laptop running an ATI Radeon HD 3100 graphics card
[*]Installed the drivers
[*]Was having problems getting the GDM to load
[*]Uninstalled the drivers
[*]Experiencing "blank" screen with only a movable cursor
[*]Can only get a working desktop if I restart the GDM from a terminal
[/LIST]

That's where I am at right now.  I now recently installed the ATI 9.6 Catalyst drivers in hopes of fixing this problem.  I still can't get a desktop without going to shell and restarting the GDM.  After that everything works fine until a reboot or shutdown.  Tried running the command:

```
aticonfig --initial-f
``` 

Ran a check with:

```
aticonfig --initial=check
```

It's installed.  So something must not be configured right with the screen.  When looking at my xorg.conf file everything looks legit.  Any thoughts?

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Zer0Nin3r on 2009-08-07
*bump*

---

### Post by Zer0Nin3r on 2009-08-29
*Bump*

---

