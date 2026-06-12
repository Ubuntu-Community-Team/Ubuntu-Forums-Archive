---
title: "Edgy Beryl/AIGLX and xscreensaver flicker"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by mbeierl on 2006-11-09
I've replaced gnome screensaver with xscreensaver and now I notice that all the screensavers flicker.

It's almost as if beryl/aiglx and the screensaver are fighting for what is to be displayed on the root panel.  Sometimes the screensaver shows and the next moment the screen is blank.

Anyone else seen this weird effect?  I'd like to get back to working screensavers again :)

---

### Post by CheeseEatingBulldog on 2006-11-09
I have the exact same problem. Looks like the same reason why one can't use GL apps when running XGL/Beryl.

---

### Post by hikaricore on 2006-11-09
Lucky you :P gnome-screensaver hardlocks my xserver while beryl is running.

---

### Post by mbeierl on 2006-11-10
Weird!?!  I rebooted (again - because there's a bug in i810 which prevents vt switching so I can't hibernate:() and suddenly the effect is gone.

What I did notice was that the overlay for frames/etc directly interfered with the screensaver.  But now, magically, the screensavers all look good **AND** I have wobbly windows!

---

### Post by jomtois on 2006-11-22
Don't know about any one else, but I did the following and it got rid of the flickering in GL screensavers (have not tried on games like nexuiz yet):

```
sudo gedit /etc/X11/xorg.conf
```

Go to the Section "Device" portion.
```

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
	Option		"backingstore" "true"
#	Option		"EnablePageFlip" "true"
	Option		"SubPixelOrder" "none"
	Option		"AccelMethod" "EXA"
	Option		"RenderAccel" "true"
	Option		"AGPMode" "8"
	Option		"ColorTiling"   "on"
	Option		"DynamicClocks" "on"
	Option		"mtrr" "on"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	option		"DRI" "true"
	option		"GARTSize" "64"

EndSection
```

I commendted out the Option "EnablePageFlip" "true" (or you could set to false).  That seemed to fix it.

Kubuntu Edgy Eft, AIGLX, Radeon 9600, using radeon opensource drivers.

Beryl works fine (minus the water effects which are not supported unless you use fglrx (I had memory probles with fglrx)).

Hope this helps someone.

---

