---
title: "DWA-552 is being buggy"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by leilei1 on 2012-01-04
So I'm currently using a Dlink DWA-552 PCI wireless card and for some random reason the wireless card either works or it doesn't. 

Sometimes when I start up my computer the network manager detects no wireless devices. When I run ifconfig and iwconfig the wireless card doesn't show up either. Yet when I run lspci the card is there.


This is what the card is lacking in lspci when it doesn't work.
```

    Capabilities: [44] Power Management version 2
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```My current assumption is that this is a bug in the ath9k driver, but if there's something I can do that will make the card work whenever it doesn't load that would be much appreciated.

---

### Post by sdowney717 on 2012-01-04
[http://ubuntuforums.org/showthread.php?t=1903935](http://ubuntuforums.org/showthread.php?t=1903935)
If you cant get it to work properly for $5 you can buy this usb wireless n device.
Load the driver and it works well.
Been using it and all is fine.

---

