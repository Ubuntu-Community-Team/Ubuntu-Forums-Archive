---
title: "Enabling Dual ATI HD3870"
date: 2008-08-30
forum: Multimedia Software
---

### Post by SeaborneClink on 2008-08-30
I'm having a hard time enabling my 2nd ATI HD3870.
Two monitors, each one is plugged into Port0 on separate video cards.


xorg.conf is as follows
```

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:3:0:0"
EndSection

```
```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

```
```

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

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	Monitor    "aticonfig-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```



aticonfig --lsa as follows
```

* 0. 01:00.0 ATI Radeon HD 3870
  1. 03:00.0 ATI Radeon HD 3870

```

So obviously the drivers installed correctly and the computer recognizes that they are both there, however only one shows up in the Catalyst Control Center

How do I go about enabling the 2nd card located at PCI BUS 03:00

---

### Post by overdrank on 2008-08-30
Hi and welcome, I do not have a ATI at the moment but can you detect them in the display configuration, use the command ```
gksu displayconfig-gtk
```

Moved to Multimedia & Video :)

---

### Post by SeaborneClink on 2008-08-30
Thanks for moving my post to the prober section. :redface:

gksu displayconfig-gtk responds with this
[img]http://f1-f12.org/images/ubuntu/displayconfig-gtk.png[/img]

---

### Post by SeaborneClink on 2008-08-31
Bumping for help =\

---

### Post by SeaborneClink on 2008-09-01
Bump again. This is the only thing keeping me from wiping my windows partition. :frown:

---

### Post by SeaborneClink on 2008-09-04
Bump

---

### Post by SeaborneClink on 2008-09-06
*sigh* :frown:

Am I ever going to get to the bottom of this?

---

