---
title: "Movie plays LAG in full screen"
date: 2008-04-25
forum: Multimedia Software
---

### Post by gnaishes@g33ks on 2008-04-25
as i mentioned above.. my movie playing be it in totem, vlc or mplayer will be very very lag if i played it in fullscreen mode, but, it played smoothly in normal un-zoom mode..
wut is the cause of the prob ?

Thanks in advanced
Regards,
Roger.

---

### Post by zergling on 2008-04-25
Hi,
Did you try to enable the cache under mist in mplayer?
What driver do you use to render the video? Did you try to use openGL?
Are this video by any change in H264? If yes, do you have an HD 5400rpm?
Bye and let me know :D
Ciao!

---

### Post by gnaishes@g33ks on 2008-04-25
i just enabled it as in ur post.. mplayer prob solved.. but d aspect ratio is still the same as normal even i played it in full screen.. 
on the other hand,how cn i set it in totem or vlc..
Thanks
Regards,
Roger.

---

### Post by gnaishes@g33ks on 2008-04-26
btw.. i got the problem sorted..
it's d fglrx problem after all..
sori n thanks for all d help
Regards

---

### Post by zergling on 2008-04-26
NP gnaishes
I am very glad that you were able to solve your problem :D
Ciao and take care :)

---

### Post by nadoudidou on 2008-05-04
How did you fix this please?
I'm stuck :/

Edit:
I removed xserver-xgl and made few changes in the xorg.conf

> Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility X1400"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Option		"HPD"	"swap"
	Option		"monitor-PANEL_LCD1/LVDS"	"Default Screen"
	Option		"RROutputOrder"	"PANEL_LCD1/LVDS"
	Option          "TexturedVideo" "1"
	Option          "VideoOverlay"  "0"	
	Option      "OpenGLOverlay"     "on"	
	Screen	0
EndSection

Also, composite is on.

So compiz is working, as well as videos in full screen without lagging.
Firefox scrolls smoothly now.

*The only thing that's left to make this solution perfect is to get videos not to flicker anymore in windowed mode.*

Note that they dont flicker when I disable texturisedvideo. In that case videos get more pixelized and only work in vlc (as somehow other programs can't find the video source).



EDIT:
Ok so it's solved! :D
[http://forum.compiz-fusion.org/showthread.php?t=1152](http://forum.compiz-fusion.org/showthread.php?t=1152)
> o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
> o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

---

### Post by mocatz187 on 2011-01-24
I had this problem after an update.
Goto system/administration/hardware drivers then search for new drivers. See if your driver was disabled or your 3D acceleration is disabled. Enable it.
This solved my problem. I hope it solves yours.

I originally found this post a couple weeks ago but didn't feel the solution applied to me so i kept digging and the fix was really easy. just want people to know how to fix it if they should arrive at this posting with a problem like mine.

---

### Post by Bill Gates Foundation on 2012-03-07
12.04 and VLC with NVIDIA 300 on xserver video driver software.....


vlc game me fullscreen problems but movie player was fine....

here is how i fixed it.......

>          
                  In Tools > Preferences > Video > Output change the Default to X11, save and restart vlc.
 


---

