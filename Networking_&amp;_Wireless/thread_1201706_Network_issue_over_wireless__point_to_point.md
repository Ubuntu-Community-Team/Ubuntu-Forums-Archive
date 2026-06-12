---
title: "Network issue over wireless  point to point"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by dacoman on 2009-07-01
I have this very strange issue.

Have setup a wireless point-to-point (PTP) for about 1/4 mile. It's working, it is tested with mac in windows computers. 

The problem is with two different computers running Ubuntu 8.04 and Ubuntu 8.10. This computer could not acquire an IP lease from DHCP. I have tried to setup fixed IP without success either. Both of these machines work if on site connected directly to the LAN. Both worked over the PTP when it was setup in the warehouse (just yards away from each end).

So my question? What's going on? Any ideas much appreciated. 

I am thinking that in the current setup it takes longer for a tcp packets to receive a replay so they are dropped. Is there a way to play with this timeout issues. Is this hardware dependent or kernel dependent?

Thank you,
-D

---

### Post by jonobr on 2009-07-01
I dont know if this is relevant , but I have seen issues in the past where MTU sizes have caused a problem for tunneling.

There were older bugs in hardy where people using tunneling would set the MTU size themselves in the NM Gui, and it would not be reflected in the actual MTU.

Im wondering if looking at your MTU size in use for the mac and comparing it to what you are using for the ubuntu client, and altering may help you out?

I also get the feeling you may need to do some wireshark tracing on either end to see if this is a TCP related issue

---

