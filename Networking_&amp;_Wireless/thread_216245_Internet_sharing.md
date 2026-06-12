---
title: "Internet sharing"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by renaissance on 2006-07-15
Hi guys !

 I have static ip space 193.40.121.50 - 193.40.121.80 and i want to share internet to another pc's. How i can do it ? Thank you

---

### Post by mips on 2006-07-15
**dhcp3-server** could do the trick.

Those are public IP addresses and I would advice you to make sure your network/pc's are secure.

---

### Post by verbatim210 on 2006-07-15
clueless when it comes to programming linux as a router, how/where do you learn that sort of thing?

firewalls
dns
dhcp
gateway/sharing

---

### Post by MrHorus on 2006-07-15
> **mips said:**
> **dhcp3-server** could do the trick.

Not by itself it won't.

What you have to do is configure your system to be a router so that it can route packets between your address space and the network of your upstream provider.

[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

This link might be a bit indepth but it will cover everything you need to know about this although the section about NAT is of course irrelevent since you have real, routable IPs.

---

### Post by mips on 2006-07-16
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

Different scenario though seeing you already have public addresses.

---

