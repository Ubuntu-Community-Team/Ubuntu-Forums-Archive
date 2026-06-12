---
title: "Problem with Broadcom Wireless -10.04-"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by KanjaGeek on 2011-11-19
Hey, I'm on an Acer Aspire 64-bit laptop with a dual booted Linux 10.04 32-bit. I can't get the wireless card to work on this laptop, but I can get it to work on the Toshiba laptop beside me. I need this so I can upgrade from 10.04 to the latest release. Can anyone help? I've looked around and have found posts, but none have succeeded in helping me. When I do sudo llshw -C network I get *-network UNCLAIMED, network controller, Broadcom Corporation. So that's my wireless.

---

### Post by wojox on 2011-11-19
What does this say:
```
lspci | grep -i net
```

---

### Post by KanjaGeek on 2011-11-19
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)

---

