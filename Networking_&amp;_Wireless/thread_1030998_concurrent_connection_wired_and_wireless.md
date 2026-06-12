---
title: "concurrent connection wired and wireless"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by blkmagikca on 2009-01-04
Using ubuntu 8.10. Wireless works as does wired networking. However, I cannot get them to run at the same time. I know that this is done in Windoze, but I cannot get it to work with ubuntu.

The reason: I am using wireless to connect to the internet (I am in an RV in an RV park that provides wi-fi). However, to print I have a networked laser printer, and this is connected to a 10/100Mbit switch through the wired NIC.

Is there any particular modification I have to make to the network manager to do this?

Howard

---

### Post by superprash2003 on 2009-01-05
post output of ifconfig from the terminal..also post output of route -n

---

### Post by Iowan on 2009-01-05
Dunno about the "new" NM, but older versions would not activate two interfaces at once - though you could manually configure /etc/network/interfaces to activate more than one interface.

---

