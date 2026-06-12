---
title: "eth0 &amp;  1 randomly dropping for 30sec or more"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by Servious on 2011-08-09
Once or twice an hour or every few hours the interface will drop off. When this happens and comes back up and ssh sessions i have open will sit there and lag for 15-20 sec while, i assume, the connection is re-established. Any sessions i have open to the mySQL database will be dropped and I'll be given error messages associated with loosing connection to the SQL server.

I have run a constant ping against the server and when the interface seems to drop off I'll get 10 or so host unreachable and it'll then start to reply again.

This happens with both eth0 and eth1 on this Dell Poweredge 850 running 11.04. 

I have done a "sudo lspci -v" on both the server acting up and another Natty box that doesn't have this issue but the same hardware. They both are using the same driver versions though it seems certain options are slightly different between the two.

Working Server: 
```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
        Subsystem: Dell Device 01b6
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data <?>
        Capabilities: [58] Message Signalled Interrupts:Mask-64bit+ Queue=0/3 Enable-
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Kernel driver in use: tg3
        Kernel modules: tg3

```

Broken Server:
```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
        Subsystem: Dell Device 01b6
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [58] MSI: Enable- Count=1/8 Maskable-64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Kernel driver in use: tg3
        Kernel modules: tg3

```

This is really starting to drive me bonkers. I've checked the cable, it's a pre-made with both ends looking good. I even swapped it out for a fresh home made cable and the problem still persists. Any help or guidance would be greatly appreciated.

---

### Post by Servious on 2011-08-11
I'm still having this issue.

I pulled the drives and placed them into another Dell PowerEdge 850 to see whether it could possibly be a hardware or NIC controller issue but the problem still persists. I have no issues from my servers (same hardware) that were originally 10.04 that were upgraded to 11.04 with just a "do-release-upgrade -d"

Anyone have any ideas?

---

