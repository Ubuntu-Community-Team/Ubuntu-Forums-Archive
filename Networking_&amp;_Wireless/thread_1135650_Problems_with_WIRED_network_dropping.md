---
title: "Problems with **WIRED** network dropping"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by pwillis on 2009-04-24
Hello,

I am running U. 8.04 H.H. on an IBM eServer xSeries 306 server.

The server contains 2 on-board gigabit network adapters based in Intel chips:

82541GI
82547GI

Networking generally works, although the network appears to drop periodically
which disconnects sessions. This happens approximately every 10 minutes.

When the network does go down it will come up again by itself after
a period of time.

At first I thought there was something in power management that was
causing the network to go to standby mode.

I turned off all the power management services in ubuntu. This didn't 
fix the problem. 

I then edited '/boot/grub/menu.lst' and disabled acpi and apm. This also
had no effect on the problem.


What could be going on every 10 minutes when I have all power management
turned off?

Thanks for any help,

Peter

---

### Post by The Cog on 2009-04-24
I have seen reports that the network-manager does something like that if you don't kill it. Worth a try.

---

