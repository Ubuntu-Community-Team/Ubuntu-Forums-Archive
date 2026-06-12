---
title: "any software for Ubuntu to relay packets?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by feelagain on 2009-07-22
Hi, guys,
I am looking for sort of packet relay software packages. 
Here is what I want to do:
I have three ubuntu box as A, B, C. They are connected as A<-->B<-->C. Now I want C to send a file to B using whatever a file shifting application while B directly forwards any packets received from C to A. So what B does is to replace the IP destination header of each coming packet from C with A's IP and send it to the network. Does anyone know if there are any software package exising which can be configured to do so on B??
 
Many thanks.:popcorn:
 
 
Cheers,
Lei

---

### Post by spd106 on 2009-07-24
I don't quite understand your problem. You've described either a router if you're trying to forward network packets or a proxy if you're more concerned with higher level traffic such as web files.

Useful links:
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
[http://en.wikipedia.org/wiki/Squid_(software](http://en.wikipedia.org/wiki/Squid_(software))

---

### Post by aesis05401 on 2009-07-24
> **spd106 said:**
> I don't quite understand your problem. You've described either a router if you're trying to forward network packets or a proxy if you're more concerned with higher level traffic such as web files.

Useful links:
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
[http://en.wikipedia.org/wiki/Squid_(software](http://en.wikipedia.org/wiki/Squid_(software))

I would suggest this link as a starting point: [http://www.linuxfoundation.org/en/Net:Bridge]("http://www.linuxfoundation.org/en/Net:Bridge")

You can prototype all sorts of network setups on a linux box right out of the box by using the bridge functionality in conjunction with IPTables.  It will never run as quickly as a hardware router for the same task, but it does allow us mortals to play with filtering and layout functionality that only comes on really expensive hardware.

---

