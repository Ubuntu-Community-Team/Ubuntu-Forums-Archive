---
title: "TV out cloned, how to get two different resolutions?"
date: 2008-07-15
forum: Multimedia Software
---

### Post by pterosky on 2008-07-15
I got an ATI Graphic card and the image on the TV is connected and fine. But the resolution is too high -- it is also in the 1280x1024 mode like the monitor.

Can I configure xorg.conf so that I have 1280x1024 resolution on the monitor and 1024x768 on the TV, in cloned mode?

---

### Post by markbuntu on 2008-07-15
If you are using the fglrx driver you can try typing 

aticonfig --help

this will give you a list of configuration options not avialable in the Catalyst Control Center that will let you do that.

Some tvs also overscan by default which causes the video from your computer to be bigger than the screen. You can usually turn that off in the setup options in the tv.

---

### Post by pterosky on 2008-07-16
Thanks for your suggestion markbuntu!

I ran the following commands:```

sudo aticonfig --initial
sudo aticonfig --tv-overscan=on
sudo aticonfig --tv-geometry=75x70
```

Result if I run ```
sudo aticonfig --tv-info
```
> The TV Format is "PAL-B"
The TV geometry is "75x70+0+0"
The horizontal position limits are [-6, 6]
The vertical position limits are [-6, 6] 
TV overscan mode is enabled

The resulting xorg.conf file:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "cn"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "TVOverscan" "on"
	Option	    "TVHPosAdj" "0"
	Option	    "TVVPosAdj" "0"
	Option	    "TVVSizeAdj" "70"
	Option	    "TVHSizeAdj" "75"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection
```

Sadly, it doesn't fix my problem. The TV image isn't smaller...

Can you see what's wrong with my xorg.conf?

---

### Post by markbuntu on 2008-07-16
You need to turn the tv overscan off at the tv. There is probably some menu item in the tv setup somewhere.

---

### Post by pterosky on 2008-07-17
It is an old school television, I don't think it has the option of turning the overscan off.

I did manage to move the image a few pixels to the right and down with this command
```
sudo aticonfig --tv-geometry=50x50+6+6
```
The size didn't change though...

I have resigned to just hit "Screen Resolution" and switch to 1024x768, until I get another graphics card.
Thanks for trying!

---

### Post by markbuntu on 2008-07-17
You should also set aticonfig --tvoverscan=off

Are you using the latest 8.6 driver from ATI. There was some problem in selecting NTSC and PAL formats in the older drivers that is now fixed.

If you want to give it a try, the directions are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Use method 2.
If you want to read the release notes first, they are here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

and here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

Just so you can get an idea of the cumulative fixes and enhancements since the 8.4 driver from the repos.

There are also some tweaks you can do, not related to tv out but good anyway:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by pterosky on 2008-07-21
I am using the ATI accelerated hardware driver that is suggested by the Ubuntu system.

I tried with both --tvoverscan=off and on, still no success.

I appreciate your effort, but I think will just resize the screen size, until I buy another graphics card. Would Nvidia be a wise choice?

---

