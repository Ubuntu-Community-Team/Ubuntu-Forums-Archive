---
title: "[solved] Wake on Lan - Ubuntu 8.10 Intrepid"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by umatchan on 2009-03-30
I have a P5GCMX -1333 mbd and Ubuntu 8.10 x32. Also have a PCI Gigabit card. Wake on lan did not work neither did resume via keyboard/usb mouse...

After scouring all over, I finally found this post

[https://lists.linux-foundation.org/pipermail/linux-pm/2007-November/015551.html](https://lists.linux-foundation.org/pipermail/linux-pm/2007-November/015551.html)

basically you just do a cat on /proc/acpi/wakeup , find the device you want to Wake on and just say 

echo "USB1" > /proc/acpi/wakeup (where USB1 is your device name). Works great!!

Also on the MBD I had to update the jumper switch settings that controls Wake On...

---

