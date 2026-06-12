---
title: "Wireless works but confused with info about pci card?"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by IronFox on 2008-12-03
Im using a Belkin f5d9010 but when I use lshw -C network I get this:
```
*-network
       description: Wireless interface
      [B] product: RT2600 802.11 MIMO
       vendor: RaLink[/B]
       physical id: 1
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:3f:92:e0:04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=143.43.185.245 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg

```

Whats the product and vendor about?  should it be Belkin for vendor and F5D9010 for the product? Also Im using the rt61pci driver and only connecting at 1Mb/sec, anyway to make it faster? When I pop in my friends Linksys wpc3000n, I connect at 54Mb/sec using the wl driver.

---

### Post by spcwingo on 2008-12-03
The output you're seeing is referring to the chipset of your wireless card.

---

### Post by IronFox on 2008-12-04
I had a hunch that was it.  But Im connecting at 1Mb per sec, am i using the right driver or do i have to tweek something to get it to work properly?

---

### Post by spcwingo on 2008-12-04
You probably need better firmware.  Broadcom cards do the same thing (54Mbps cards connect at 11Mbps) before firmware upgrade.  You would pretty much have to somehow get the source and compile it yourself...but, you might be able to avoid this if you can get ndiswrapper to work with your card.  If ndiswrapper is a no-go then have a look-see at this:

[http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/](http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/)

---

### Post by IronFox on 2008-12-04
Ndiswrapper worked like a charm! Connecting at 54Mb/sec!  Thanks!

---

