---
title: "DisplayLInk and Ubuntu 11, still green screen"
date: 2011-09-12
forum: Multimedia Software
---

### Post by sageek on 2011-09-12
've justed returned to my lovely Ubuntu after some years of non-linux OS.

Anyhow, I have a Toshiba L630 14C Laptop, Ubuntu seemed to be recognizing must of the hardware, although I'm using 2 external screens besides the laptop screen (which I want to turn off).

As the moment, the USB display adepter is recognized, he even gets green right away, though I can't insert him into the xorg.conf since the X crashes, the issue is that the screen, using the USB adapter doesn't send his EEID and then X doesn't know how to use it. I tried to override EEID and it still didn't work. Since two of the screens are the same, i tried 'tricking' it by copying the EEID file from the VGA (recognized) screen to the usb connected one, it kinda worked since the other screen was recognized though the display was not good, he couldn't refresh his self and you could see pixels when you move the mouse.

At the moment I have the DisplayLink drivers installed, green screen, though he doesn't sends the EEID what making the X not to start properly.

Any ideas guys?

---

