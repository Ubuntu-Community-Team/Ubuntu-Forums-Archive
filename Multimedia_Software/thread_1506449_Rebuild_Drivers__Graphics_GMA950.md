---
title: "Rebuild Drivers / Graphics GMA950"
date: 2010-06-10
forum: Multimedia Software
---

### Post by chackett99 on 2010-06-10
Hi All,

I built a Boxee box last year on Ubuntu .. maybe like 9.0x something.  I can't remember.  I spent a bunch of time tweaking settings and drivers to get everything working.

One evening, there was a large update and my wife got tired of waiting and just turned the box off mid-update.  Box wouldn't boot, and I didn't have time to mess with it.  I left it for probably 8 months or more.

Somehow I am able to breath some life into the box, and I start updating the system.  Now I'm on 10.04 and things are looking good with the exception of my graphics configuration.

I have the GMA950 Intel Integrated graphics  (from dmesg):

[   19.011531] agpgart-intel 0000:00:00.0: Intel 945G Chipset

Running glxgears only gives:

chris@htpc1:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
chris@htpc1:~$ 


I have tried running the dpkg-reconfigure to rebuild my xorg.conf, but it doesn't seem to be working.

I am guessing I need to rebuild / reconfigure my Intel driver, but I'm not sure how to do that.  Can someone point me in the right direction?

Thanks!
Chris

---

