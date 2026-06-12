---
title: "Fixing resolution to 1400x1050 in ThinkPad T60"
date: 2008-12-08
forum: Multimedia Software
---

### Post by lukajuri on 2008-12-08
Hi, folks.

I am using Intrepid and have big problems setting up to the native resolution of my ThinkPad T60. This is 1400x1050, but Intrepid insists, no matter what I do, that the max resolution is 1024x768.

I have an ATi card, am using ATI proprietary drivers and my xorg.conf is:

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1400x1050" "1440x900"
	EndSubSection
EndSection

Any suggestions?

---

### Post by Ryangarve on 2008-12-28
I'm having the same issue, any thoughts?

---

### Post by pdtpatrick on 2009-01-05
I'm having the same problem and have researched .. no answer thus far. xrandr shows the highest i could go is 1024x768 and the drivers are installed properly.. however if you change the resolution to anything higher, xserver reconfigures and when u reboot it goes back to 1024x768 :( .. this is kinda annoying. 

Im using 8.04 LTS .. i wonder if the problem is fixed in 8.10

---

### Post by pdtpatrick on 2009-01-05
BTW the drivers are the Intel 945GM which lshw and lspci show its installed and loads up fine at startup. Just cannot get the display to go any higher.

---

### Post by phooky on 2010-12-26
I ran into this the other day. I had been running successfully with 1400x1050, and after doing some magic with a projector lost the ability to go above 1280x1024.  Apparently the monitor configuration had set my virtual display size to 2680x1024.  The trick is to bring it back up to something large enough to contain 1400x1050.

If you had your display working in high resolution and lost it after playing with your projector/VGA settings, you can probably just copy your last /etc/X11/xorg.conf backup over your current copy.  (Every time the mode utility makes changes here it creates a backup of the form /etc/X11/xorg.conf.timestamp.)

You can also just edit your xorg.conf file and change the "Virtual" line to read:

Virtual 2424 1050
(Mine is currently at 2048 2048, which seems to work fine, too.)

Roundabout solution that I used because I had no idea what I was doing:
* created a modeline entry using "cvt 1400 1050"
* added it with xrandr --newmode
* attached it to panel with xrandr --output LVDS --addmode 1400x1050_60.00
* switch to the new mode in the monitor configuration
* logout/restart X

---

