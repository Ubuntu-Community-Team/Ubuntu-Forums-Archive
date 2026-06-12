---
title: "Reloading network driver on wake"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by AceMilo on 2009-07-05
When my computer is off or in sleep/hibernate mode the network card stays on but drops to 100mbit mode to save power for, I presume, wake on lan.  When I wake my computer from sleep, the nic stays in 100mbit mode, it does not go to full 1gbit mode.  When I first turn on my computer I notice the same behavior, but once the os starts to load and it loads the nic drivers it goes to full gigabit.  I tried doing a /etc/init.d/networking restart but this doesn't fix it.  Basically, I just need to know a command to restart the nic driver, and if possible, a way to have it run it on wake from suspend.

Thanks

---

### Post by AceMilo on 2009-07-07
Bump

Still need help on this one.

---

