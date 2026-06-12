---
title: "WiFi compatiblity help."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by melenor on 2009-01-14
Alright I just got a wireless card and before i open it, i want to know if it will work with ubuntu without any problems.
it is. 
Encore Electronics 802.11n Wireless PCI Adapter ENLWI-N

---

### Post by Patsoe on 2009-01-14
> **melenor said:**
> Alright I just got a wireless card and before i open it, i want to know if it will work with ubuntu without any problems.
it is. 
Encore Electronics 802.11n Wireless PCI Adapter ENLWI-N

[http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=1&pid=269#DOWNLOAD](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=1&pid=269#DOWNLOAD)

They provide a Linux driver package from their website. If you open the zip file, you'll find Ralink drivers for the RT2860 chip, so I assume that's what's in there. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210725](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210725)

... suggests that it will be supported just fine in the future, but if you want to use it right now, you'll have to build the driver yourself.

---

### Post by melenor on 2009-01-14
thanks i might go out and find one that works now

---

