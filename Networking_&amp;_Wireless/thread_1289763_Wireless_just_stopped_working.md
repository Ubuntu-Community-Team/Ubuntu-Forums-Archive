---
title: "Wireless just stopped working"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2009-10-12
Here is some info on my card:

```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Subsystem: Dell Device [1028:000b]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 16-00-cf-ff-ff-44-a5-d5
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl

```

The wireless was working fine. After unchecking "Enable Wireless" in the nm-applet context menu, I have not been able to re-enable it. It seems that nm-applet no longer sees any wireless network.

I tried clicking "connect to hidden network" and then entered my home network info, but that didn't work either.

lsmod reports that wl is in fact loaded.

I suspect this problem has something to do with NetwrokManager, but I really don't even know how to approach it.

---

### Post by witeshark17 on 2009-10-12
Does your keyboard have a wireless card button? It may look like a small graphic of a radio tower, and it is meant to disable wireless functions as you may need to on a plane, for example. Hitting it again should turn the wireless card back on if that it the cause.

---

### Post by dbbolton on 2009-10-12
I tried reinstalling network-manager and restarting. It seems to be working now.

---

### Post by witeshark17 on 2009-10-12
Glad to see you got it sorted :)

---

