---
title: "Does OS radeon driver support my Radeon 9800 Pro?"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by gkiller on 2006-09-28
Hello,

I have a Radeon 9800 Pro graphics card (R350 chip). At the moment I am using the fglrx proprietary drivers, but they are really crappy: Xv does not work correctly, slow video playback.

So I would like to try the open source 'radeon' driver. But I have read that they might not support 3D acceleration for my card. Does the driver included in Dapper support my Radeon 9800 Pro? And if not, will the Edgy version do that?

I really want to get rid of the fglrx drivers, but I need 3D and video acceleration. My next graphics card will definitely be an Nvidia one.

---

### Post by dbd on 2006-10-20
I don't think so, however, I'm not sure.

Everywhere I have read says that it does not (apart from one place that said there was 'experimental' support).

I currently have these drivers installed with my 9800 Pro and some things I thought would need 3d support work, and some don't!
For example, Beryl works fine, as do some of the OpenGl xscreensavers, however, other OpenGl xscreensavers are very slow, and the openGl mode of Globulation does not work.
Video playback is fine, so it might be worth you installing these drivers just for that. (In gmplayer I had to change the video driver to xv, but all other video players I have tried work fine "out of the box").

But could someone else answer the question please? Since I want to know if my problems (such as Globulation not working in OpenGL) are due to me badly configuring my system, or are simply because those drivers don't support 3d stuff properly.

Thanks

Oh, and might be worth me posting some of my xorg.conf:
> Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
Option "DRI" "true"
 Option "ColorTiling" "on"
 Option "EnablePageFlip" "true"
 Option "AccelMethod" "EXA"
 Option "XAANoOffscreenPixmaps"
 Option "RenderAccel" "true"
 #Option "AGPFastWrite" "on" <- If this is enabled X won't start
EndSection


> Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

