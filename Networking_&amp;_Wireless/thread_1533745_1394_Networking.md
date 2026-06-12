---
title: "1394 Networking"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by baker126 on 2010-07-18
Please help me...I have been Googling for hours!

I have two computers...Ubuntu server and Windows XP client.  Both are connected to the internet using Ethernet.  I have them connected directly using 1394 to increase speed of large transfers.  The internet network and 1394 have different IP address scemes.
Internet 192.168...
1394 10.0.0...

I am having problems getting the two computers to communicate with each other.  I can ping the server's ip address and and it loops back.  Same with the XP's IP address.  I can't ping each other.

ifconfig shows my eth0 and eth1 connections are up.  The eth1 Link Encap says UNSPEC.  (Don't know if that means anything.)  

The connect used to work and I have no idea what happened to break the two.  

Thanks.

---

### Post by DarthScape on 2010-07-18
Possibly setup static routes?

---

### Post by baker126 on 2010-07-18
Got 'em.  10.0.0.2 for the server and 10.0.0.3 for the XP machine.

---

