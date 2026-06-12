---
title: "WiFi Scanning with iwlist interrupts network connection"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by BillRebey on 2009-09-18
I'm using iwlist in Ubuntu 9.04 to scan for active WAPs, but when iwlist runs, it disrupts networking so that all other networking tasks are disrupted, fail, or have to wait until the scan is complete.   

Network functionality is returned immediately when the scan is complete.

I'm using a WiFi card based on the Realtek RTL8187L chip, and the driver that comes with the 9.04 Kernel.

How do I prevent iwlist from disrupting networking capability while it's scanning?

---

