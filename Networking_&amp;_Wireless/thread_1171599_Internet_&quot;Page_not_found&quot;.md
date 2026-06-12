---
title: "Internet &quot;Page not found&quot;??"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by rob2nd9th on 2009-05-27
Ok so my got a wifi box from Orange his lap top See's it he has signal strength but when he tries to go on line he gets the unable to find page screen??

Its a Thompson? box he on 9.04

Iv try to talk him through his resolve .conf but thats not fixed the problem.

Any pointer would be appreciated.

---

### Post by Iowan on 2009-05-27
Check **route -n** ```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[COLOR="Red"]0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0[/COLOR]
``` This is from my wired box, but wireless should be similar.  Verify that the "gateway" address points to router/modem/internet access point.

---

### Post by superprash2003 on 2009-05-28
post output of ifconfig from the terminal also try opening [http://74.125.45.100](http://74.125.45.100)

---

### Post by rob2nd9th on 2009-05-29
> **Iowan said:**
> Check **route -n** ```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[COLOR="Red"]0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0[/COLOR]
``` This is from my wired box, but wireless should be similar.  Verify that the "gateway" address points to router/modem/internet access point.

Ok my dad is about 600 miles away with no Internet :( so posting results is proving tricky. The above fro what he tells me is the same Except
192.168.1.0 is 192.168.2.0 and 
192.168.1.1 is 192.168.2.1

What bugs me is he got the laptop when he visited me and i installed 9.04 on to it and is worked fine hear??

---

