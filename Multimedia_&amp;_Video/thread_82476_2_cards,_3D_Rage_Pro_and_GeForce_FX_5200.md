---
title: "2 cards, 3D Rage Pro and GeForce FX 5200"
date: 2005-10-26
forum: Multimedia &amp; Video
---

### Post by samjam on 2005-10-26
My new graphics card is not "detected" and I can't make it capture.

I have an Nvidia NV34 [GeForce FX 5200] that was working since breezy install, all fine, with the official nvidia drivers.

Because the nvidia drivers don't support capture-while-X (or something) I also installed an ATI 3D Rage Pro TV card with TV tuner and svideo in/out

This card isn't "noticed" at bootup time, but lspci shows:
0000:02:02.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro (rev 5c)

I've tried modprobeing aty128fb, atyfb, radeonfb, flglrx and no joy.
Some of them stay loaded but dmesg -c doesn't hint anything being recognized so, and modprobe bttv etc doesn't add an /dev/video? devices, so therefore nothing sees the device.

Sadly xorg-driver-fglrx conflicts with my nvidia-glx so I can't have 2 x sessions (why?)

And what spell should I invoke so I can use v4l or bttv stuff to be able to capture video input from this card?

Sam

---

### Post by fragmental on 2005-11-03
the rage pro does not use the fglrx driver.  The ati driver built into xorg might work.  Are you sure the rage pro tv has a tv tuner? svideo in/out does not necessarily mean it has a tv tuner, it only means that it can capture or output through svideo.  If you have a vcr with svideo you can watch tv with that, maybe.  Are you sure it's not just svideo out?  Most cards just have svideo out.

the only ati cards I know of with tuners are tvwonders.

---

### Post by samjam on 2005-11-13
[QUOTE=fragmental]the rage pro does not use the fglrx driver.  The ati driver built into xorg might work.  Are you sure the rage pro tv has a tv tuner? svideo in/out does not necessarily mean it has a tv tuner, it only means that it can capture or output through svideo.  If you have a vcr with svideo you can watch tv with that, maybe.  Are you sure it's not just svideo out?  Most cards just have svideo out.

the only ati cards I know of with tuners are tvwonders.[/QUOTE]

I was wanting to watch composite video, but I couldn't load the x drivers wiuthout unloading my nvidia drivers due to ubuntu confdlicts, but I bought a capture card here: [http://www.ubuntuforums.org/showthread.php?p=488252#post488252](http://www.ubuntuforums.org/showthread.php?p=488252#post488252)

---

