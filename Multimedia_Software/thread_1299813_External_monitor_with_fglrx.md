---
title: "External monitor with fglrx"
date: 2009-10-24
forum: Multimedia Software
---

### Post by 01mf02 on 2009-10-24
Hi, I'm having problems with the fglrx driver and multiple screens: I have attached an external monitor via DVI to my laptop and would like the laptop screen to power off, therefore having everything displayed on the external monitor exclusively.

I configured fglrx so far as to display everything on the external monitor only, however the laptop screen (which should be disabled) now displays very strange effects: Sometimes it is mostly black, then the whole screen goes white and slowly fades to black, sometimes it displays colored stripes from top to bottom - it's almost like a screensaver. :)

Here is my xorg.conf:
```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
EndSection

Section "Monitor"
	Identifier   "0-LCD"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
	Option	    "Monitor-DFP2" "true"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-LCD" "0-LCD"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-LCD" "0-LCD"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Unfortunately I wasn't able to create a clean xorg.conf, because the X server didn't start without an existing xorg.conf and dpkg-reconfigure didn't do the trick as well.

My questions:
- Is this a common bug or is there at least a setting to power off the laptop screen manually? I tried xrandr, but I didn't get that to work.
- How to create a generic xorg.conf from scratch?

Thanks for your help!


P.S.: This happens with Ubuntu Karmic Beta with the newest version of fglrx from the official Ubuntu repositories.

---

### Post by cilynx on 2009-10-25
This isn't going to be of much help, but: Yes, it's a common bug.  My laptop screen does all kinds of neat things when switching between single/dual/external only.  

I've found that closing the lid and opening it again often gets rid of the graphic wonkyness.

---

### Post by 01mf02 on 2009-10-26
Hi cilynx, thanks for your answer! I too noticed closing the lid solved my problem at least two times. In that case I just hope new drivers that fix these problems will be available soon ...

---

### Post by markbuntu on 2009-10-26
Are you using the catalyst control center to do that??

---

### Post by 01mf02 on 2009-10-27
Yes, I'm using the Catalyst Control Center. Btw., trying to run it via the usual Applications menu results in a message that the command can't be found - I have to run "sudo amdcccle" manually.

---

### Post by markbuntu on 2009-10-28
Do you have the displays set up as independent before you disable the laptop screen?

---

### Post by 01mf02 on 2009-10-30
Hmmm, I don't really know - how to set the displays independent?

Unfortunately I currently don't have my external screen around, but if I recall correctly, in the Catalyst Control Center there were two rectangles, one bigger for the external screen and one smaller for the laptop screen. I just dragged the laptop rectangle to that area that says "Drag here to deactivate" (or something like that, I have a German system), and after a restart I experienced said behaviour.

Do I have to do something else before?

---

### Post by markbuntu on 2009-10-30
If the external display is cloned to the internal one that could be a problem when the internal display is deactivated. The latest fglrx (9.10) has fixed a number of issues with configuring multiple screens. You could try that.

---

### Post by 01mf02 on 2009-11-05
So, I installed Ubuntu 9.10 now (no beta anymore, yay :p) and it seems to ship a new fglrx version (btw, is there a quick way to find out its version number via the terminal?), however my problem still remains.

I attached a screenshot which demonstrates my current configuration as displayed by the Catalyst Control Center.

---

### Post by 01mf02 on 2010-01-07
It seems I have solved the problem: My current configuration is running my laptop with its cover closed, only slightly lifting it when switching it on. I've configured the fglrx driver (newest version!) to display only on the connected external monitor.

A friend also told me that the GNOME application "Display settings" could change the screens used for display on the fly, which I will try as soon as I have access to an external monitor again. (Currently on vacation. :D)

---

### Post by cilynx on 2010-01-07
Yes, Display Settings is working pretty well these days.  My only annoyance is that it doesn't remember screen placement.  At work, I run the laptop display and an external display where the bottom of the screen is a solid 4-inches higher than the bottom of the laptop display.  It's easy enough to setup the diagonal and hit Apply, but it would be nice if it remembered it in the first place.  (And yes, I am well aware that if I really want that functionality, I should write it.) ;)

---

