---
title: "[SOLVED] IPv6"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2008-12-04
What's the difference between IPv4 and IPv6 and how do I know what I have?

---

### Post by Kobalt on 2008-12-04
Definition : [http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)

Check if your Internet provider has IPv6 support.

---

### Post by puppywhacker on 2008-12-04
chances that you have IPv6 are close to zero, too little operators are offering it, because too few sites are IPv6 reachable

an address looks like this fe80::210:a7ff:fe10:8c43
instead of for instance IPv4 127.0.0.1

you can check with ifconfig if there are entries with "inet6" and you can try to reach the following famous IPv6 sites

[http://ipv6.google.com](http://ipv6.google.com)
[http://kame.net](http://kame.net)
[http://www.whatismyipv6.net](http://www.whatismyipv6.net)
[http://www.sixxs.net](http://www.sixxs.net)

---

### Post by Iowan on 2008-12-05
It's likely you'll see IPv6 info in your **ifconfig** results, but questionable if your router (or your ISP) can/will use it.

---

### Post by theozzlives on 2008-12-05
So what is it, just a way to expand IP addresses?

---

### Post by jflaker on 2008-12-05
> **theozzlives said:**
> So what is it, just a way to expand IP addresses?

Yep
under IPV4, there are only 4,294,967,295 addresses
under IPV6, there are 2 to the power of 128 ) or 340-undecillion or 3.4E38 billion (actually 340,282,366,920,938,000,000,000,000,000,000,000,000) addresses

It expands it just a LITTLE BIT as well as addresses SEVERAL security issues never resolved under IPV4

---

### Post by jonobr on 2008-12-06
From what I saw migration push from IPV4 to IPV6 was growing through the 90s
and came to a huge head up to 2000 when the dotcom thing was out of control.
More business , more people looking for IP addresses.

When the whole thing went kersplat the major push seemed to go out of it.
Now we are back to it again, and once again the march is on to IPV6.
Im wondering what this economic downturn will do,
will it passify things for another while?

A lot of IP V6 is being implemented, however, the important thing to remember is that IPV6 is backwardly compatible.

---

