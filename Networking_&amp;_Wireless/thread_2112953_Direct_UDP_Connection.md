---
title: "Direct UDP Connection"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by zufram on 2013-02-06
Hi all!

I want to establish a direct connection between two PC through UDP protocol. The UDP will be implemented using simple client-server method in Python script via terminal. To send a message, the receiver IP address and port is required. As far as i know, IP address is assigned via DHCP or manually. To this time, i tested the program using loopback address (127.0.01 or my IP).

How can i determine the IP address and/or port (UDP, specifically) of the other PC in direct ethernet connection? Is it automatically assigned when i connect the two PC (like local 192.168.0.x or so)?

Many Thanks!

---

### Post by SlugSlug on 2013-02-06
It wont be automatically assigned unless it's connected to a DHCP server. You would need to manually assign it an IP

---

### Post by zufram on 2013-02-07
So i need a routing device to do a direct UDP connection? Is it possible to "preconfigure" the IP address?

Many thanks!

---

