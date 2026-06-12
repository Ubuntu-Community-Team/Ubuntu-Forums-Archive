---
title: "Network wireless setting reports &quot;wirless firmware missing&quot;"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by 1maddog on 2013-01-22
Did a windows (XP SP3) install of Ubuntu 12.04 which, as far as I can tell, went ok except for when I set up the wireless network. After entering all the necessary info to setup the wireless connection not only did it  not connect but there did not appear to be any attempt to connect. Went to the settings/network/settings page and it reports that it's on, the hardware address and also says "firmware missing".

I reboot and select windows xp and after that loads the wireless connects up to the network as expected. Then reboot to Ubuntu and still get "firmware missing".

Any thoughts on what's going on and how to get the wireless working?

Thanks...

---

### Post by ubfan1 on 2013-01-23
From a wired connection, try adding the package linux-firmware-nonfree
   sudo apt-get install linux-firmware-nonfree
That gets much firmware that cannot be included directly in the distribution.

---

### Post by 1maddog on 2013-01-24
> **ubfan1 said:**
> From a wired connection, try adding the package linux-firmware-nonfree
   sudo apt-get install linux-firmware-nonfree
That gets much firmware that cannot be included directly in the distribution.

Outstanding! about 10 seconds after the install finished the wireless connected with out any drama.

Thanks!

---

