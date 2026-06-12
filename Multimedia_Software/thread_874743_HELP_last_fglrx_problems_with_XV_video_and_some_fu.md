---
title: "HELP last fglrx: problems with XV video and some full-screen applications"
date: 2008-07-30
forum: Multimedia Software
---

### Post by segalion on 2008-07-30
When I updated to hardy and last fglrx driver (8.6 and 8.7 installed from AMD web), I´ve been in troubles with the XV video and some full-screen applications.

The XV problem is that seems that it is working (xvinfo reports to be usable with something like "avivo"). But when I play videos (xine, gxine, mplayer...) with XVideo (forced) the video appear in my two screens (TV and laptop) simultaneously, and has some horizontal sync effects problems (soft flickering). Its not so fluent video and the color seems to be less intensive than older drivers...
With older ubuntu-fglrx versions (and windows and other OS and ever I can remember) XVideo (or "overlay" mode, hardware videorender assisted) only works on one screen at a time (aticonfig ovon=0|1 to conmute).
I think that this is something similar with the windows VMR directX-7 and directX-9 that work worst than precessor.


The full-screen problem is more dramatic: The image is almost unavailable due to hard syncs problems (like errors in modeline configuration). It is hard flickering image.

Applications that fails are:
- Stellarium in full-screen
- F-spot in presentation mode
- Sinatra in full-screen
- mupen-64 with ricevideo plugin (full and windowed).

PD. 
- DRI is working fine.
- I´ve tested lots of "aticonfig" and xorg.conf ..., and Xorg.0.log doesnt report any problem... Tested too the uma and sideport bios memory config...

I´ve been read a lot of forums, and I cant find any solution...
Please if anybody can help me....

My config is HP8000z laptop , ATI Xpress X200M with 1440x900 and 1024x768 and clone TVout.

---

### Post by segalion on 2008-08-01
I´ve found the solution to the first problem (XVideo).

As Jim say in his great post [http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

The problem is that new ATI drivers set the AVIVO XVideo Render (3D engine) as "default" in Xorg config, instead of older and classic 2D engine XVideo render. 
Maybe the avivo (or TexturedVideo) could be better in modern ATI cards (specially to make compiz+videorender compatible), but not seems to has good quality for video in a Xpress 200M. Maybe someone can post some xorg options that solve the "sync problems" specially in movement scenes.

There aren`t aticonfig command to disable this AVIVO config, called "TexturedVideo" option in xorg.conf, so you need to edit /etc/X11/xorg.conf

Option "TexturedVideo" "off"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

save, and restart de computer, and then test with "xvinfo" and see classic videorender adaptor instead of AVIVO.

The second problem remains the same.
Please if anybody can helpme...

---

### Post by the_X_files on 2008-08-01
I have problems with the new drivers too..

---

### Post by segalion on 2008-10-13
bump.
Same problem with Catalyst 8.8 and 8.9 
Anybody can help?

Thanks.

---

### Post by lavinog on 2008-11-12
How much memory do you have? Some people have had problems with using 4g of memory.

I have a desktop with an xpress 200 and a laptop with an xpress 200m.
Both are using fglrx 8-7 and work fine.
I have had some problems with 8-6 and 8-8, but 8-7 seemed to work.


Future fglrx drivers should be supporting motion compensation, but I am pretty sure the current drivers don't.

my xorg.conf is pretty plain:
```


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
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

### Post by segalion on 2008-11-18
Only 1 GB. I´ve tried UMA and Sideport bios memory configuration with no diference.

The only thing that works is the "export LIBGL_ALWAYS_INDIRECT=true".

I will try next 8.11 fglrx...

---

### Post by lavinog on 2008-11-18
> **segalion said:**
> Only 1 GB. I´ve tried UMA and Sideport bios memory configuration with no diference.

The only thing that works is the "export LIBGL_ALWAYS_INDIRECT=true".

I will try next 8.11 fglrx...

I think the "export LIBGL_ALWAYS_INDIRECT=true" is no better than removing the driver.

8-11 fixed my issues

---

### Post by CHaoSlayeR on 2008-12-04
Hi there,

I've had a similar problem but even worse: it hardlocked my system when trying to view a video with xv!!! My solution was to configure (if you have DRI at least) mplayer to use "gl:yuv=3". That way it worked even better compared to the xv of previous drivers. With my rather old HD 2400 I can even view matroska videos in full HD resolution in fullscreen with under 25% CPU usage average (well, some peaks over 50% but no lags, no flicker, everything's all right).

I would agree with lavinog not doing the "LIBGL_ALWAYS_INDIRECT" option because it would just use the CPU instead of the GPU (which always is used to be preferred as it can handle that type of processing much more efficiently). If xv doesn't work for you just try another video out module until you find some that looks good, scales nice and uses the least CPU power.

Hope I could help.

Greetz,

C]-[aoZ

---

### Post by segalion on 2008-12-17
> **lavinog said:**
> I think the "export LIBGL_ALWAYS_INDIRECT=true" is no better than removing the driver.

8-11 fixed my issues

I have tried fglrx 8.12 and solved the problem too.
Thanks.

---

