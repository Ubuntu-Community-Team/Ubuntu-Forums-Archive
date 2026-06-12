---
title: "ndiswrapper issue"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by celticbhoy on 2010-11-17
Ok, here the problem.

I have a very very old compaq laptop running Xubuntu fiesty and want to use a Belkin USB wireless G network adaptor with it, and am attempting to use ndiswrapper to load the driver. But I think I am missing a step somewhere (its been about 2 years since I first set this up).

If I install the driver with ndiswrapper and then list it says using alternate driver zd1211rw. I have added this to the nblacklist file at /etc/modprobe.d, and tried again. Still the same, I have deleted the zd1211rw directory from /lib/modules/2.6.20-15-generic/kernel. But still the same.

HOW DO I STOP THIS DRIVER LOADING??????

P.S. I have no internet to use hardwired.

---

