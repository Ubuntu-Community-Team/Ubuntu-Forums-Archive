---
title: "Adding new network card"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by Skerit on 2010-04-17
So I've switched to a new motherboard, an Asus P6T SE one, and now I don't have any cable connections in Networkmanager anymore.

I see the new card when I run "ifconfig", it's called "eth2", but I have no idea where to go from here without messing up networkmanager.

---

### Post by Iowan on 2010-04-17
Does **eth0** still appear? You might edit */etc/udev/rules.d/70-persistent-net.rules* to swap eth0 and eth2.
(I like to make a backup somewhere - in case I mess something up)

---

