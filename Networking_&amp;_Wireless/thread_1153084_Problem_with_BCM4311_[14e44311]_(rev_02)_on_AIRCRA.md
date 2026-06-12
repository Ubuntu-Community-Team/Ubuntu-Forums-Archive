---
title: "Problem with BCM4311 [14e4:4311] (rev 02) on AIRCRACK-NG"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by ltcosta on 2009-05-08
[SIZE=3]I can't inject with this card and i don't know why...

this is my lspci :[/SIZE]

03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1374]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 1a-00-d4-ff-ff-73-6d-59
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

[SIZE=3]And i try to get started:[/SIZE]

[SIZE=2]airmon-ng start wlan0:[/SIZE]

Interface            Chipset                            Driver

eth1                     Unknown                             wl


What should i do to make my wireless card can inject? Please, help me!

Thanks

---

### Post by ltcosta on 2009-05-08
Hey guys...
i Just made it!!!!

First i set my default driver as desable.
And than i installed B43-fwcutter...

That's it!

Thanks...

---

