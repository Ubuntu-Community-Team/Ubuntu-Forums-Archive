---
title: "nettool to improve performance?"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by BikeHelmet on 2009-11-05
Hi. :) I have a NAS with onboard ethernet:
```
RTL-8110SC/8169SC Gigabit Ethernet
driver	=	r8169
driverversion	=	2.3LK-NAPI
```

I stumbled across nettool, and decided to check what was being offloaded.

```
ethtool -k eth0
Offload parameters for eth0:
Cannot get device flags: Operation not supported
rx-checksumming: on
tx-checksumming: off
scatter-gather: off
tcp segmentation offload: off
udp fragmentation offload: off
generic segmentation offload: off
large receive offload: off
```

Apparently almost nothing.

I searched google for info on these options, but found nothing explaining what they do. I searched for my NIC's name and all the terms, but couldn't find anything useful.
```
rx-checksumming: on
Specifies whether RX checksumming should be enabled.
```

So, does anyone know how I find out what options my NIC supports? I'd like to get more speed out of it, or maybe less CPU usage.

Oh, and this is a headless NAS. If I have to lug it up from the basement to fix the ethernet, I'll get grumpy. :D

Cheers, if anyone knows!

---

