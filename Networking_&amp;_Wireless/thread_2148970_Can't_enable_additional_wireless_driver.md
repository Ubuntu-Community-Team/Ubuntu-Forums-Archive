---
title: "Can't enable additional wireless driver"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by ouner on 2013-05-27
Hello,

I installed xubuntu 13.04 64 bit on my Lenovo G780. However both wired and wireless are not working. 

Before installing I used my live-usb and I was able to use wireless after enabling the additional Broadcom BCM 4313 driver from the ubuntu software centre.

Post installation however I cannot follow the same steps to enable this additional driver. It appears in the same place, but when I attempt to enable it and apply it simple switches back to "Do not use this device" with no error message or feedback given. 

What do I need to do in order to enable this driver ? Once it is enabled and I have internet connectivitity, I think it should not be too hard to find the driver for the wired network driver......

Any help much appreciated, thanks.

---

### Post by ouner on 2013-05-27
Ok, I have the wireless working at least so far.

All I did was download the bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64  and install that alongside its dkms dependency.

All good so far, just need to find the correct driver for my wired connection.

---

