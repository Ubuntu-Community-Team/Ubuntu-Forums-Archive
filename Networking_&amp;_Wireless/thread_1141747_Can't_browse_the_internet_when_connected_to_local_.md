---
title: "Can't browse the internet when connected to local network"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by perrti-y02 on 2009-04-28
Hello,
Whenever I connect to my own network (used for file server and general tinkering, IP is 192.168.2.x?!) I am unable to browse the internet which comes in on my Wifi card (IP 192.168.1.101). If I am not connected to the wired network then I can happily browse the interweb.

Any ideas what my problem is? I think it is trying to find the interweb on my local network, where it clearly isn't.

I am running 9.04 and everything is using static IP addresses.

---

### Post by Iowan on 2009-04-28
What are results of **route**? (In particular, what is gateway address?)

---

### Post by perrti-y02 on 2009-04-29
The results are as follows:

tim@shuttle:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
tim@shuttle:~$ 
 is that any help?

---

### Post by perrti-y02 on 2009-04-29
bump

---

