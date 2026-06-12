---
title: "again - lost wifi after running updates - how to prevent this?"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by blueberries on 2011-11-30
hello,

i run ubuntu 11.10 on msi wind u100. last upgrade broke my wifi, but compiling the driver myself solved it (ralink rt2860).
now i just ran the usual updates and lost the wifi again (lshw -> network UNCLAIMED).
im not a newbie, but in this area dont understand much, wud be very glad for some assistance in understanding what exactly goes wrong each time, and how can i prevent it from happening so often.. 

thank you,
bb.

---

### Post by ratcheer on 2011-11-30
It is because you have to use a wifi driver that is outside of the normal kernel-supported driver set, as do I. The Linux kernel intends for us to use the rt2800pci driver, but that driver does not work for us. So, every time the kernel is updated, we have to recompile and reinstall the rt2860 driver.

As far as I know, there is no way to prevent this. Maybe someday, the kernel will support our (very common) chipset with a driver that actually works for it.

Tim

---

### Post by blueberries on 2011-11-30
:(

thx anyway!
bb

---

