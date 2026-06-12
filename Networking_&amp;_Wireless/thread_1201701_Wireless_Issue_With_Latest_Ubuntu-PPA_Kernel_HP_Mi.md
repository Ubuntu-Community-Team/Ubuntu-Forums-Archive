---
title: "Wireless Issue With Latest Ubuntu-PPA Kernel HP Mini 2140"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by awells527 on 2009-07-01
I have an HP Mini 2140, and I am running the latest Ubuntu-PPA kernel because of bug 376728.  When I am running the standard kernel, wireless works without a problem through the restricted drivers manager, but when I use the non-standard kernel, the wireless option is not available, and the driver doesn't show up, even though I see the hardware is detected (see below).

Is there a reason why the latest kernel isn't working with the restricted driver program?  I shouldn't have to reinstall the package, as it is installed and working when I boot into the other kernel.  I'm thinking that I have a module to load or blacklist.

Uname -r: 2.6.29-02062905-generic

lspci | grep Broadcom\ Corporation: 08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

---

### Post by Valde_91 on 2009-07-21
Hi Awells527!

I'd the same problem, but I followed this how to from str3zz for compile the necessary modules in the 2.6.29.x kernel.

[http://ubuntuforums.org/showthread.php?t=1088743&page=3](http://ubuntuforums.org/showthread.php?t=1088743&page=3) 

Now the wireless is working well on my HP 2140.

bye bye Valde_91

---

