---
title: "sharing the internet connection (the how-to's don't work)"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by rcopper on 2009-05-16
I know there are some quides here about how to share the internet connection but nothing seems to work. 

I need to share the internet connectio so that the ubuntu computer (nr1) serves as a router to an XP comp (nr2) and sometimes another ubuntu computer (nr3) instead of the xp..

the nr1 computer has two net cards - how should I configure these cards as well as the other computers?

---

### Post by albinootje on 2009-05-16
> **rcopper said:**
> 
I need to share the internet connectio so that the ubuntu computer (nr1) serves as a router to an XP comp (nr2) and sometimes another ubuntu computer (nr3) instead of the xp..


You need to use two different network ranges.

Suppose that the NIC connected to your router has 10.0.0.2 and your router has 10.0.0.1 (where I assume that this was done by DHCP running on your router), then you should give the other NIC and the client machine (nr.2 or nr.3) a different network range, e.g. the other NIC gets 192.168.1.1 and the client gets 192.168.1.2
The gateway address for the clients would then be 192.168.1.1

On the Ubuntu router you need to set up Masquerading with iptables, and that should be it (unless I forgot something).

Which howtos did you follow by the way ?

For masquerading see here e.g. :
[http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux](http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux)

---

