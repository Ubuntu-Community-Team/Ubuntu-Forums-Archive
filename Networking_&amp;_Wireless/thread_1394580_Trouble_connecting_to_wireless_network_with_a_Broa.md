---
title: "Trouble connecting to wireless network with a Broadcom BCM4312 b/g"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by Werekill on 2010-01-30
Hi, I've updated the b43 driver for my wireless card, but it still won't connect. Can anyone help me with this?

```
  description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
```

Everything else works perfectly (including, obviously, the wired connection) but this.

---

### Post by bkratz on 2010-01-30
> **Werekill said:**
> Hi, I've updated the b43 driver for my wireless card, but it still won't connect. Can anyone help me with this?

```
  description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
```

Everything else works perfectly (including, obviously, the wired connection) but this.


See this thread especially post 7. It is about your same card
BCM4312 802.11b/g

[http://ubuntuforums.org/showthread.php?p=8539988#post8539988](http://ubuntuforums.org/showthread.php?p=8539988#post8539988)

---

### Post by Werekill on 2010-01-30
Thanks, it worked perfectly! ^_^

---

### Post by bkratz on 2010-01-30
> **Werekill said:**
> Thanks, it worked perfectly! ^_^

Congratulations

Please go to the thread tools and mark as solved [solved] just in case it helps someone else.

---

