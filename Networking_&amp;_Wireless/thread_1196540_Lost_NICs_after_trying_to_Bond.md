---
title: "Lost NICs after trying to Bond ???"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by Data-Base on 2009-06-25
Hi,

I have **Intel Pro/1000PT PCIe DualPort Server Adapter (2x 1000BaseT), PCI Express x4 Network Card**

when first time I booted Ubuntu 9.04 it was recognized and worked

but I did try the instructions in [http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)  to build network bonding (Link Aggregation) it did not work

so I deleted the settings (Marked them away) and now I do not see the NICs again !!!

any help?

---

### Post by Caligari on 2009-06-27
I just did this exact howto yesterday with the quad port intel pro card.

ifconfig -a should show you your missing ports.

As for getting the howto to work, it was originally written for 6.04, I'm running 8.04 on the computer I did the howto on, and I see you're running 9.04.  For the most part, the howto is strait forward, there are a couple of changes in the locations, if I recall correctly:
the aliases file is located in /etc/modprob**e**.d/aliases
the i386 file portion of the howto is not very clear, this will change based on the type of install that's done, I'm running an 64bit version of ubuntu server, so I think the file I had to edit was /etc/modprob**e**.d/arch/x64-86
The ls command will help you find the proper directory, type 'ls /etc/modprobe.d/arch' and only one file should be listed.

Best of luck,
Caligari

---

