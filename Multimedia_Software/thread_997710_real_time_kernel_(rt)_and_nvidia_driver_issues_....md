---
title: "real time kernel (rt) and nvidia driver issues ..."
date: 2008-11-30
forum: Multimedia Software
---

### Post by Bucky Ball on 2008-11-30
Hi all. I have installed Ubuntu Studio with kernel 2.6.24-22-rt (real time).

Took me awhile to figure out why I was hitting a black, totally unresponsive screen instead of the login screen after booting. Turns out the real time kernel doesn't like the nvidia-glx-new driver I was using with my regular Ubuntu install (I have just loaded the appropriate packages for Studio rather than the whole shebang - I don't care for Studio's desktops or themes and want the packages already in Ubuntu straight).

So ran the rt recovery kernel and lets me know there is a problem with Xserver and I should fix and try again, so choose option 4 in the recovery process; 'Fix XServer'.

This re-writes me a 'vanilla' xorg.conf file, which is fine because the kernel now boots without a problem and all Studio packages seem to be operational (almost, but that is another story!).

My problem and question is this: Someone on another thread mentioned that once the rt kernel is installed and running, you can reinstall the nvidia-glx-new driver, and all should be good. Not in my case. Exactly the same round-about I am afraid. Just wondering if anyone has discovered a fix for this or if I wish to use the rt kernel and benefit from the low latency for audio work, I must sacrifice the benefits of my nvidia card.

All ideas and suggestions gratefully accepted and appreciated and thanks in advance ... :)

ps: doubt that it makes much difference in this case, but I have a GeForce 6200TC (dated but suits my purposes fine).

---

### Post by markbuntu on 2008-11-30
This same problem happened to me with the ati fglrx driver but reloading the driver or the driver kernel packages worked for me so I figured it would work with the nvidia drivers also since it seemed to be exactly the same problem. I am sorry it did not work.

I did notice that there are a bunch of kernel packages specific for nvidia in the update which i ignored. it is possible that these may fix your problem.

One thing you should do before loading the rt kernel is set your Desktop Visual Effects to none (disable compiz) since compiz depends on the driver for compositing and when you reboot into your previous session you will get a black screen if the driver fails. You can also log in to the xfce script or gnome safe mode to avoid this and fix the driver problem.

---

### Post by Bucky Ball on 2008-12-03
> **markbuntu said:**
> 
One thing you should do before loading the rt kernel is set your Desktop Visual Effects to none (disable compiz) since compiz depends on the driver for compositing and when you reboot into your previous session you will get a black screen if the driver fails. You can also log in to the xfce script or gnome safe mode to avoid this and fix the driver problem.

I reckon this is exactly what happened. No screen. Compiz is off now and things are working fine. I'll look into the nvidia rt kernel option and try some of your other ideas.

Thanks for the tip ...

> **markbuntu said:**
> You can also log in to the xfce script or gnome safe mode to avoid this and fix the driver problem.

How exactly?

---

