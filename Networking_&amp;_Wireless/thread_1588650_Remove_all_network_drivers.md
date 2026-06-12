---
title: "Remove all network drivers"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by Butcher0 on 2010-10-05
I want to build a system totally without network support. Does anybody know where the network-drivers are located? I think i need to know which packages/modules to uninstall also?

I am going to build a live-system out of it afterwards, and boot it from a USB. Don`t know if that has anything to say, but my experience has been that especially the /etc/network/interfaces keeps getting overwritten at boot-time as soon as I make it a live-system.

That`s why i was thinking of removing every network-driver upfront, such that Ubuntu has an empty database for network-cards.

Any opinions or answers are greatly appreciated, thx! :)

---

### Post by kreggz on 2010-10-06
I wonder if you could reconfigure the networking init script to not start at boot rather than taking out the drivers.

---

### Post by chili555 on 2010-10-06
Please see /lib/modules/2.6.32-25-generic/kernel/drivers/net. Substitute your kernel version if it's not 2.6.32-25-generic.

---

