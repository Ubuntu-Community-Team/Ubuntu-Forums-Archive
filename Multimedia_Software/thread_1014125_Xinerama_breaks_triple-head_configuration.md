---
title: "Xinerama breaks triple-head configuration"
date: 2008-12-17
forum: Multimedia Software
---

### Post by Mattventura on 2008-12-17
After solving my initial problem ([here]("http://ubuntuforums.org/showthread.php?t=1012451")), I can use 3 monitors, however, I cannot drag windows onto the left monitor due to Xinerama not being enabled. However, when I enable Xinerama, it only uses the middle and right monitors, and it considers it to be one large screen (the login window is stretched between them). Is there a way to use 3 screens with Xinerama or something entirely different?

---

### Post by usererror on 2008-12-18
Have you had any luck with this?  I am considering switching to Linux on my PC at work, but I enjoy my three monitors.  Need to be able to drag windows though.

---

### Post by Mattventura on 2008-12-18
Well, I read through the aticonfig help and managed to set up my layout manually. However, I now have 3 completely separate displays, and again, Xinerama (for some reason) breaks the left display but allows me to drag windows between the center and right monitors. My new xorg.conf looks like this (without Xinerama):

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" LeftOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "Off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
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

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:8:0:0"
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


```

Also, here is a line of output that might be related (screen 2 is the left one:
```
(EE) fglrx(2):MultiView is not supported on the first adapter; this screen will not shutdown.
```

Could it be expecting all four monitors (two monitors on each GPU) to be attached to the card in order for Multiview/Xinerama/Whatever to work?

---

### Post by markbuntu on 2008-12-18
What are you using for video cards?

---

### Post by Mattventura on 2008-12-19
I am using a 4850 X2 as my video card. It is a dual GPU card with 4 DVI ports, 2 for each GPU.

Here is my current xorg.conf (with Xinerama off):

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" LeftOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-1" LeftOf "aticonfig-Screen[1]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "Off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
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

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:8:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:8:0:0"
 	Screen	1	# Changing this produces different results; see below
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

Now, changing the "Screen 1" part with the comment next to it and putting xinerama on or off produces different results.

Here are some outputs from X with the different configs (these are retyped, not copied, so there may be typos):

Using "Screen 1",  with Xinerama Off produces no atypical errors, and all monitors work.

Screen 1, Xinerama On:

```

(EE) fglrx(2): MultiView is not supported on the first adapter; this screen will not shutdown.
(EE) fglrx(2): Preinit failed
(EE) fglrx(3): Quitting secondary screen -- no monitor specified
(EE) fglrx(3): Preinit failed

```

Again, the right two work, the left two don't work.

Xinerama Off, screen set to 3:
It says:
```
(EE) fglrx(1): Screen 1 deleted because of no matching config section.
```
Which is odd, because screens 0,1, and 2 work, but screen 3 doesn't.

Screen set to 3, XInerama On:
```

(EE) fglrx(1): Screen 1 deleted because of no matching config section.
(EE) fglrx(2): MultiView is not supported on the first adapter; this screen will not shutdown.
(EE) fglrx(2): Preinit failed

```

Has anyone gotten 3 monitors to work with 2 separate ATI cards? I figured that configuring 3 monitors on one card would be easier than doing 3 monitors on 2 cards.

I have also tried rearranging the setup, doing things such as putting the primary monitor on one GPU and and two others on the other GPU. Still no luck.

Also, something that I noticed is that when a display appears to not be working, sometimes the backlight will still be on, indicating that it has signal, but nothing is being displayed.

Additionally, has anyone managed to use an ATI card and an Nvidia onboard at the same time?

---

### Post by Mattventura on 2008-12-19
Edit: double post

---

### Post by markbuntu on 2008-12-19
Are you using the latest 8.12 driver from ati?
It has a new xinerama option in the catalyst control center that can only be used with separate x sessions running.

I am interested in this because i am considering getting another HD3650 to go with the one I have and another 24 inch monitor to go with the 24 and 19 I already have. My goal is to have the two 24 in big desktop and the 19 as a side monitor running on its own X session with xinerama so I can move things across to it.

I am thinking what i want to do is not so different from what you are trying.

---

### Post by Mattventura on 2008-12-19
I am using the newest drivers (8.12). I have downloaded them directly off ATI's site. I have also tried the big desktop option. It basically produces the same result. I can have the two on the right as a big desktop and the one on the left as a separate display, but turning Xinerama on leaves me with the two on the right as one big desktop.

Anyway, the way I am getting my xorg.conf is by doing these commands for three monitors:
```
aticonfig --initial=dual-head -f --adapter=0
aticonfig --initial --adapter=1
```

Then I edit xorg.conf to move the monitors around, and for four monitors:

```

aticonfig --initial=dual-head -f --adapter=0
aticonfig --initial=dual-head --adapter=1

```

---

### Post by markbuntu on 2008-12-19
So, let me try to understand what is going on. With xinerama you have the two right screens as big desktop and the left one as separate or is the left one turned off?

It may be that the driver writers were not expecting three screen setups for xinerama. You can talk to the ati devs, there are a few long running threads at phoronix forums where they are active and you can always file a bug report at ati. They seem to jump right on those and fix a lot of thems within the next release or 2.

---

