---
title: "Problems building Intel graphics drivers"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by brundles on 2008-03-09
Can anybody help with building the Intel graphics drivers?

Having had a few attempts using the [Intel instructions](http://intellinuxgraphics.org/install.html) I've had two lots of resulting behaviour - the first being glxinfo reporting that direct rendering fails with a problem with libGL and the second being glxinfo (and anything else that uses glx like MythTV) core dumping.

This is driving me around the bend!

I'm sure I'm missing something obvious, but not having much luck so far :(

---

### Post by AnythingBut on 2008-03-16
I just grabbed the latest git and compiled the DRM/Mesa/Intel stack today.  After wrestling a bit, I've got things kind of working.  glxinfo reports direct rendering and glxgears runs fine at 1300+fps.

My guess is that you might have installed some files in the wrong place so that you have version mismatches with files that went unreplaced.  Making sure everything went in the right place was the toughest part of the install.  I carefully bounced betwen [Intel's instructions]("http://intellinuxgraphics.org/install.html") and [these]("http://dri.freedesktop.org/wiki/Building") while checking where Ubuntu packages normally put the files to eventually get it right.

But not everything is working for me.  Compiz, in particular, is giving me problems.  All I get is a white screen.  Also, glxinfo and glxgears report "Failed to initialize TTM buffer manager.  Falling back to classic."  I might play around with it more later.  Maybe you can help me out once you get your dri/drm working.

---

### Post by brundles on 2008-03-22
Well so far, I've tried the old instructions at intelgraphics, the instructions on the other link you gave me along with the [new instructions linked to from intelgraphics](http://wiki.x.org/wiki/Development/git) and still end up with glxinfo (along with anything else glx based) coredumped :(

In terms of file locations I've got libdrm rebuilt and updated in /usr/lib and the DRI drivers provided by MESA in /usr/lib/dri.

I'm beginning to wonder if it might be something chipset related (the motherboard has the new G35 chipset) that's upsetting MESA but not sure.

The system runs happily enough with the latest libdrm and Intel xf86 drivers but as soon as I try and build MESA it falls over :(.

Any suggestions? (Please! :) )

*Edit:* What version of Ubuntu are you using? Something I noticed on the dependancies section of the DRI wiki you posted the link for is that it refers to xserver 1.5 as a requirement. Gutsy only runs 1.3 so I'm wondering if it just won't build on Gutsy without rebuilding xserver first :(

---

