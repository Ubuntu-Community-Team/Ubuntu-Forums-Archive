---
title: "unable to define gateway"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Rajwinder on 2009-08-03
Hi I am new to Linux. I am unable to define gateway by network manager. It automatically resets to 0.0.0.0 
Secondly my wired connection sometimes did not work. It shows disconnected.It works fine after 1 or 2 reboots. Thanks for any help

---

### Post by Crafty Kisses on 2009-08-03
What are the results of the following?
```
route
```

---

### Post by Rajwinder on 2009-08-03
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ip address    *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

---

### Post by Rajwinder on 2009-08-04
Problem has been solved.I Have uninstalled the network manager and configured LAN Card by Command Line.Now Its working fine

---

### Post by Iowan on 2009-08-04
I had problems getting NM to accept some information - can't remember if it was a "press Enter instead of Tab" fix, or something different... moot point if you already found a fix.

---

### Post by Rajwinder on 2009-08-07
Thanks lowan.Now i have configured Lan card through NM also with your advice.Thanks again.

---

