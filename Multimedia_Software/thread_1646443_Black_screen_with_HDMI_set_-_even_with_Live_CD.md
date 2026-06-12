---
title: "Black screen with HDMI set - even with Live CD"
date: 2010-12-15
forum: Multimedia Software
---

### Post by astembridge on 2010-12-15
I picked up an Emerson 32" HDTV set from Wally world last night - works great as a standard TV set.   

Next, I hooked up a new box with a MSI 785GTM-E45 motherboard, which has a built in HDMI port.   Ubuntu 10.10 is installed.  The system boots to GRUB, and after making my selection, the system starts to post.. after a few moments the screen goes black and I lose control.   

I rebooted into failsafe - same thing.

So next I grabbed my Ubuntu 10.10 Live CD, configure BIOS to boot from that.. the Live CD starts to load, but flashes to a black screen during post.  Just like from my default installation. 

So no matter how I try to load Ubuntu with this HDTV set, I get a black screen. 

To confirm the HDMI port is working, I temporarily swapped primary drives with my XP box.  The system was able to boot into windows with the HDTV set, so I am confident the port is functional. 

I've tried everything I know.. even booted failsafe with a different monitor, cleared out the installed graphics driver -- still get the black screen. 

I'm at my wits end.   Really want to use Ubuntu for my media center. 

Any suggestions on getting beyond the black screen during post?

---

### Post by astembridge on 2010-12-16
I think I'm allowed to bump after a day.. 

Anyone have a solution?

---

### Post by astembridge on 2010-12-18
SOLVED.

I installed the proprietary ATI hardware driver, rebooted and now have HDTV working.

---

