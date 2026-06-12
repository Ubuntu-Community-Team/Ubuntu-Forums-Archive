---
title: "etherwake on other vlans"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by netman4201 on 2009-11-01
What udp port does etherwake use to send wol?

---

### Post by Kokopelli on 2009-11-01
WOL occurs at the datalink layer, not the network layer.  So it does not use UDP or ports.  The WOL packet is broadcast on a specific network segment and associated with a computer by MAC.

There are applications that can perform a WOL from a remote subnet but the port assigned is arbitrary as far as the WOL packet is concerned.  Looking at the man page for etherwake though, it is not such a program.

---

