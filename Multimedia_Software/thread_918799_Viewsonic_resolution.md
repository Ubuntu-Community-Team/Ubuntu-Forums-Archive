---
title: "Viewsonic resolution"
date: 2008-09-13
forum: Multimedia Software
---

### Post by stans on 2008-09-13
I've just installed 8.04 and would like to improve the resolution on my Viewsonic PF790. I've tried the 'gksu displayconfig -gtk' command but it appears that a driver is required. 

I cannot find the working combination of resolution and refresh rate.

Does anyone have this model of display working correctly ?

Thank you...

---

### Post by mc4man on 2008-09-13
try this instead > sudo displayconfig-gtk No space, or it it wasn't that install restricted drivers

your monitor is listed, after setting you may need to adjust the new xorg.
Look for a line after the mode line about virtual, it usually gets set to last listed resolution which will make it hard to see login screen.

For **some nvidia cards** you may need to add a line to get full refresh rate choices. It's better to check refresh rate from the monitor itself, usually under 'viewmeter'
** possible** line for refresh
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
        [COLOR="Red"]Option "DynamicTwinView" "False"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"ViewSonic"
	Modelname	"ViewSonic A90f+"
	Horizsync	30-86
	Vertrefresh	50-150
```

login screen setting
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		[COLOR="Red"]Virtual	1280    1024[/COLOR]

```

---

### Post by stans on 2008-09-13
Thanks for your input.

'viewmeter' ? I've looked all over my system and don't see anything like it. Do I need to install it ?

The samples you provided - are those for a PF790 ? I did also try the alternative to gksu but it looks just the same. It also wanted a driver.

The last Ubuntu I installed (6.06) took a LOT of monkeying around to get the resolution right.

---

### Post by mc4man on 2008-09-13
> viewmeter' i was refering to checking/confirming the res. and refresh *from the monitor itself*. I have a90f's and it (viewmeter) is accessed from buttons on front of monitor. (not familiar with your model though on mine button 1 opens settings, then scroll to it, ect.
Only mentioning because the reported refresh rate can be incorrect (from within ubuntu

---

### Post by stans on 2008-09-13
My monitor only provides positioning, width, etc. I regret now not having saved the xorg.conf from the running Debian system I just overlaid. 

I'll figure it out... eventually..

---

### Post by stans on 2008-09-13
Incredible how much of a challenge this is. What do I tell my friends when describing how much better linux is than windows when it cannot even detect my monitor ?

I'm in full and complete defense of linux vs. windows... but the casual user would have given up.

---

### Post by forumtalker on 2009-09-04
I'vejust stumbled on your comments and must agree.I'm new to Linux and would love to exit windows.  I installed Ubuntu 8.1 in January on a spare machine and loaded the updates,one of which must have had a bug which disabled boot entirely.I managed to recover but was disheartened. I've just decided to try again with 9.04 and all went well apart from the resolution on my Viewsonic 19" wide screen being limited to a hopeless 800.There seems to be no easy way to get it to 1068 or above.I want an OS that allows me to enjoy my computing experience without having to lift the bonnet and fiddle with the spark plugs. That's where windows seems to score, sadly. I'm at the point of chucking in the towel for a second time and hoping that when it comes the Google Linux OS is more user friendly.:confused:

---

### Post by oygle on 2009-09-27
See [http://ubuntuforums.org/showthread.php?t=1274232](http://ubuntuforums.org/showthread.php?t=1274232) for a solution to the ViewSonic 19", and NVidia graphics card.  :)

---

### Post by stans on 2009-10-04
I gave away the monitor some months ago to release some of the tabletop area... it is a HUGE monitor. It was given to me several years ago for the same reason. I now haved a 21' AOC lcd that is easily detected by the Ubuntu install process.

The main weakness of Linux in general is lack of hardware support. Most things do work well, but every once in awhile you encounter a real hassle. Currently I'm battling with a usb mouse problem... and will wait for 9.10 as there doesn't appear to be a solution.

---

### Post by waynemcl on 2009-12-18
I found this thread, while looking to get 1280x1024 running on my ViewSonic e70 17" (VIA KM266). I solved it by taking a standard xorg.conf and tweaked the VertRefresh from 50 to 48.5:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     48.5-160
EndSection


Hope this helps anyone else looking for this. Cheers.

---

