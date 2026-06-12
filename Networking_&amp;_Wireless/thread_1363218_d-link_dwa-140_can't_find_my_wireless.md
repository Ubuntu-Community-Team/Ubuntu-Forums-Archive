---
title: "d-link dwa-140 can't find my wireless"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by zeezam on 2009-12-24
I just bought a asrock ion 330 and try to connect to my wireless with my dlink dwa-140. I find some wireless networks via network manager but I can't find my own wireless network.
This has worked before with mya dwa-140 on other computers.

If I try to connect to a hidden network (even if the network isn't hidden) with my ssid and password it doesn't work.

Any ideas?

---

### Post by bkratz on 2009-12-24
> **zeezam said:**
> I just bought a asrock ion 330 and try to connect to my wireless with my dlink dwa-140. I find some wireless networks via network manager but I can't find my own wireless network.
This has worked before with mya dwa-140 on other computers.

If I try to connect to a hidden network (even if the network isn't hidden) with my ssid and password it doesn't work.

Any ideas?



This thread is probably worth looking at.  

[http://ubuntuforums.org/showthread.php?t=1333255](http://ubuntuforums.org/showthread.php?t=1333255)

Pay  particular attention to post #15, (there are two versions of the DWA-140)

---

### Post by zeezam on 2009-12-24
> **bkratz said:**
> This thread is probably worth looking at.  

[http://ubuntuforums.org/showthread.php?t=1333255](http://ubuntuforums.org/showthread.php?t=1333255)

Pay  particular attention to post #15, (there are two versions of the DWA-140)

Thanks you!

blacklist rt2800usb in /etc/modprobe.d/blacklist.conf did the trick for me!

---

### Post by graabein on 2009-12-24
> **zeezam said:**
> Thanks you!

blacklist rt2800usb in /etc/modprobe.d/blacklist.conf did the trick for me!

I also have DWA-140 (Rev.B2) on a clean install of Ubuntu 9.10 but the adapter won't start up.

**lsusb** command in terminal says: *Bus 002 Device 002: ID 07d1:3c0a D-Link System*

What should I do? [Link]("http://ubuntuforums.org/showthread.php?p=8539476#post8539476").

---

### Post by corny on 2010-05-12
for Rev B with RA3070 look at second part of [http://doc.ubuntu-fr.org/dwa-140](http://doc.ubuntu-fr.org/dwa-140)

consider also [ftp://www.dlinkla.com/pub/drivers/DWA-140/QIG_DWA-140_v1.00_For_LINUX.pdf](ftp://www.dlinkla.com/pub/drivers/DWA-140/QIG_DWA-140_v1.00_For_LINUX.pdf)

---

