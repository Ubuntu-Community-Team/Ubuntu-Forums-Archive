---
title: "Help, Voodoo3 3000 detects as NV15 [GeForce2 GTS/Pro]!"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by ironstorm on 2006-02-17
Hi, 

I'm trying to get an old AGP Voodoo3 3000 to run Xorg in accelerated mode.  

I'm hitting a strange problem in that my Voodoo3 is recognized as an *Nvidia Corporation NV15 [GeForce2 GTS/Pro] rev 163* (it says this when you do an lspci)...  

I can run Xorg using the "nv" driver, but accel doesn't work at all.  When I try using either the "tdfx" or "glide" drivers @ 1024x768/16bit Xorg fails to start saying it "(EE) No devices detected. / no screens found"...

I'm wondering if there is some kernel configuration I need to do to get it recognized as a Voodoo3 again...  Anyone know a fix for this?

Cheers,
-G

---

