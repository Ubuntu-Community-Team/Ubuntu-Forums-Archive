---
title: "Broadcom BCM4312 - is this normal?"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by TBABill on 2010-12-02
I have helped quite a few people get their BCM4312 and other Broadcom devices running in Ubuntu and I have just accepted that I have to install the STA driver for my device post-install on several different machines, each with the same device. But last night I did something a bit different and just want to know if it is normal.
 
I ran the LiveCD like normal on 10.04 but I took the steps to install the Broadcom STA driver in the live session via the CD. Once it installed I went to a terminal and did ```
sudo modprobe wl
``` and it was ready to go. I got online and things were perfect.
 
So then I did a fresh install and upon completion my driver was installed without any need to plugin to my router, download updates and install the driver. It just worked and I never did plug into anything from boot up of the LiveCD to fully updated system.
 
Is that normal? Does it also work the same in 10.10? If this is a common behavior, many users have been stuck doing the same steps I was using (installing the driver after install) instead of just activating before install and having a ready system after the install completed.
 
Thanks!

---

### Post by TBABill on 2010-12-03
Disregard. This DOES NOT work with Ubuntu. I mistakenly assumed the Ultimate Edition and Ubuntu installs were identical (just with different software, looks, themes, apps, etc). But not so. Ultimate has the Broadcom STA (wl) driver on the DVD but Ubuntu does not. Apologies for the oversight.

---

### Post by pdc on 2010-12-04
folks have held out the 2.6.37 kernel has having a driver built-in for the BCM4312; 

[http://news.opensuse.org/2010/12/02/opensuse-announces-fourth-development-milestone-with-kernel-interactivity-patch/](http://news.opensuse.org/2010/12/02/opensuse-announces-fourth-development-milestone-with-kernel-interactivity-patch/)

OpenSuse has this kernel in its latest test release: milestone 4: would you be willing to see how a liveCD of this OpenSuse goes, in detecting your broadcom?

---

