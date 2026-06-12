---
title: "Network drops suddenly"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by djmental on 2012-11-25
Hi guys,

I've got a problem with my networkadapter. Sometimes (once a month) the networkconnection is suddenly timed out. If I look in the /var/log/syslog I see the following message: 

ubuntu kernel: [   13.592479] atl1c 0000:03:00.0: irq 24 for MSI/MSI-X

In dmesg I see the exact same message, but with no errors at all.
It's an Atheros AR8132 / L1c Gigabit Ethernet Adapter, and I'm using kernel 2.6.32-44-generic.

The only thing I can do is a complete reboot of my system.

---

