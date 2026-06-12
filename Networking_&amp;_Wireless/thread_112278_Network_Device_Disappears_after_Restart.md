---
title: "Network Device Disappears after Restart"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by cheuschober on 2006-01-04
Hi. Ended up disabling ipv6 because I was getting some terribly slow browsing times and had to restart. Post-restart my wireless device disappears!

Output from an lshw -C Network is as follows: 
```
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@01:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:cfff0000-cfffffff irq:22

```

I have the latest madwifi-ng driver installed and it worked well before the restart. I would blame the disabled ipv6 however I've actually had problems like this before (unexplained unclaimed devices) that have at times magically (it seems) resolved themselves ... this time, it seems not.

Any thoughts?

~C

---

### Post by cheuschober on 2006-01-04
Just thought I'd bounce since my last post was sorta during sleepytime for many.

Best,
~C

---

