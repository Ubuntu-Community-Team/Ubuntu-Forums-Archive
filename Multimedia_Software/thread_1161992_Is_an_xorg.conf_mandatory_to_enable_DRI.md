---
title: "Is an xorg.conf mandatory to enable DRI ?"
date: 2009-05-17
forum: Multimedia Software
---

### Post by Jean-Marc Liotier on 2009-05-17
I use a Radeon HD 2600 XT AGP (RV630) with the radeonhd driver. Everything has been work well in 2D for a long time, but now that there are good Linux games I'm beginning to want 3D acceleration.

glxinfo says "direct rendering: Yes" but "OpenGL renderer string: Software Rasterizer" which means that there is no hardware rendering (but the slideshow-speed FPS in games was clue enough about that...)

Even though glxinfo says "direct rendering: Yes", Xorg says 'Direct rendering turned off by default. Use Option "DRI" to enable'. But I use no xorg.conf - is one necessary for enabling DRI ? Are DRI and direct rendering the same thing ?

I'm guessing that I'll have to create a minimal xorg.conf just to enable the DRI option and let HAL take care of the rest with autodetection. What is the minimum configuration I can get away with in xorg.conf just to enable DRI option and let the rest be detected automagically ?

---

### Post by gradinaruvasile on 2009-05-19
I dont know how u can use the radeonhd driver without enabling it from xorg.conf because as far as i know the default driver is the "radeon". Installing the xorg-driver-radeonhd-whatereriscalled package does not enable the radeonhd because is not officially supported as far as i know. On a X1600 (RV530) i had much better performance with "radeon". It might differ for your card...

You can generate a new xorg.conf with

sudo dpkg-reconfigure -phigh xserver-xorg

in a terminal.

And then 

sudo gedit /etc/X11/xorg.conf

make it look like 

Section "Device"
        Identifier      "Configured Video Device"
        [COLOR="Red"]Driver          "radeonhd"
        Option          "DRI"     "1"
        Option          "AccelMethod"   "EXA"[/COLOR]
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Install driconf with

sudo apt-get install driconf

in a terminal. This will add a control panel in the system->preferences menu - you might disable the low impact fallback setting - it is said it might help speeding up the rendering (on my x1600 didnt make a difference though). 
And the "method to limit rendering latency" set to "busy waiting for the graphics hardware" helped me to gain 300 fps (10%) in glxgears with the "radeon" driver - no difference with the "radeonhd".

The above Driver line explicitly demands the use of the radeonhd driver - without this line the default "radeon" opensource driver will be used.

The AccelMethod "EXA" line is not mandatory ,but it seems to be faster than the default (XAA) rendering. It is said it may create problems, but worked fine for me.

I might add that the default "radeon" driver scored 2x the score of "radeonhd" in glxgears on a RV530 (X1600) card...

DRI should anyway be enabled by default. Check your xorg log.

And i would recommend installing updated drivers from here:

[https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/~tormodvolden/+archive/ppa")

by adding the repository.

You should restart the X server after updating your xorg.conf and drivers.
If your resolution will not be detected  correctly on startup, log out and log back again. This happened to me when i switched the drivers (my screen was cropped to something like 1024x768 fron 1280x1024 as it should have been - i could not see the menus at all). You can access the menu with Alt+F1 if you cannot reach the menubar with the mouse pointer.

Also you might look at this:

[http://xorg.freedesktop.org/wiki/RadeonFeature]("http://xorg.freedesktop.org/wiki/RadeonFeature")

Testing version drivers - THESE ARE NOT STABLE VERSIONS - USE THEM FOR TESTING PURPOSES ONLY:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

---

### Post by Jean-Marc Liotier on 2009-05-21
> **gradinaruvasile said:**
> I dont know how u can use the radeonhd driver without enabling it from xorg.conf because as far as i know the default driver is the "radeon".

I simply removed the xserver-xorg-video-ati and xserver-xorg-video-radeon packages, leaving only xserver-xorg-video-radeonhd. So X has no other choice.

> **gradinaruvasile said:**
> 

You can generate a new xorg.conf with

sudo dpkg-reconfigure -phigh xserver-xorg

in a terminal.

And then 

sudo gedit /etc/X11/xorg.conf

make it look like 

Section "Device"
        Identifier      "Configured Video Device"
        [COLOR="Red"]Driver          "radeonhd"
        Option          "DRI"     "1"
        Option          "AccelMethod"   "EXA"[/COLOR]
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


Ok - I'll try that.

> **gradinaruvasile said:**
> 
Install driconf with

sudo apt-get install driconf


I had already done that - but since DRI is not enabled, driconf won't let me do anything useful.


> **gradinaruvasile said:**
> 
DRI should anyway be enabled by default. Check your xorg log.


```
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2

(II) RADEONHD(0): Direct rendering turned off by default. Use Option "DRI" to enable.

(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
```

So it definitely looks like I need to enable DRI manually...

> **gradinaruvasile said:**
> 
And i would recommend installing updated drivers from here:

[https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/~tormodvolden/+archive/ppa")

by adding the repository.


> **gradinaruvasile said:**
> 
Also you might look at this:

[http://xorg.freedesktop.org/wiki/RadeonFeature]("http://xorg.freedesktop.org/wiki/RadeonFeature")

Testing version drivers - THESE ARE NOT STABLE VERSIONS - USE THEM FOR TESTING PURPOSES ONLY:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

I'll look at those repositories and see if an updated radeon driver improves my situation.

Thank you for your advices !

---

