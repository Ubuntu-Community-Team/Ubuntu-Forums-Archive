---
title: "Ping warning - Duplicates"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by number4 on 2010-09-28
When I ping our Microsoft Windows terminal server "cluster" farm, I get ICMP warnings that there are duplicate packets.  I am able to rdesktop to the cluster with no problems. We are trying to setup nagios to run on this Ubuntu configuration and nagios is reporting the following error: "PING WARNING - DUPLICATES! Packet Loss=0%, RTA=.98ms.  FPing reports duplictes as well.  Is there a setting in the Arp table that needs to be set differently because the "Cluster" MAC address isn't an actual hardware MAC but a virtual MAC address?

---

### Post by relay_man on 2010-09-28
Not being at all familiar with your system, I'll take a guess.
To get multiple responses from a ping request, you would have to have either:
 
(1) multiple interfaces with the same ip address assigned

(2) multiple routes  that the echo request and reply can traverse.

Do you have wireshark or some other network analyzer tool available?
Being able to see exactly what is coming back from your  ping target
would be a great help.

---

### Post by number4 on 2010-09-29
I'll see what I can do to get wireshark setup to monitor specifically the ubuntu station.

---

