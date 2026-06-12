---
title: "can't connect through Comcast cable modem"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by Lary Grant on 2009-03-13
I have a Dell mini 9 running pre-installed ubuntu 8.04.  I can connect fine at home, but when I bring my laptop to my mother's house, I can't connect using Ethernet to her Comcast cable modem.  Her Windows laptop's networking is set totally vanilla... obtain IP address and DNS automatically and connects fine.
 
When I connect my mini 9 to the cable modem, the panel networking icon says it connects to the local network, but I can't see any websites and I can't even ping 76.96.54.12 which is comcast.net.  When I do that, I get:
 
```
From 169.254.9.84 destination icmp_seq=1 Destination host unreachable
```
 
I have no idea what that 169 address is... it doesn't return anything in reverse dns searces.  However, I **can** ping it from my mini 9.
 
Any ideas?

---

### Post by pytheas22 on 2009-03-13
The 169 address is an IP that Linux assigns itself when it's unable to fetch an external address for some reason.  I'm not sure why Ubuntu is unable to get an address from the modem, however, if it's set up to serve dynamic IPs.

Do you know the exact model of the modem?  If you google it, you might find other people having issues with it on Ubuntu, and how to resolve them.  Also, if you can connect to it via USB, do that and run the command 'lsusb', and post the output here.  This will provide some identifying information.

---

### Post by e24ohm on 2009-03-13
> **Lary Grant said:**
> I have a Dell mini 9 running pre-installed ubuntu 8.04.  I can connect fine at home, but when I bring my laptop to my mother's house, I can't connect using Ethernet to her Comcast cable modem.  Her Windows laptop's networking is set totally vanilla... obtain IP address and DNS automatically and connects fine.
 
When I connect my mini 9 to the cable modem, the panel networking icon says it connects to the local network, but I can't see any websites and I can't even ping 76.96.54.12 which is comcast.net.  When I do that, I get:
 
```
From 169.254.9.84 destination icmp_seq=1 Destination host unreachable
```
 
I have no idea what that 169 address is... it doesn't return anything in reverse dns searces.  However, I **can** ping it from my mini 9.
 
Any ideas?what do you get when you ping the local loopback address?

---

### Post by Lary Grant on 2009-03-13
It seems it has to do with Comcast security.  I finally worked it out using a router and these directions:

[http://www.elifulkerson.com/articles/router-vs-comcast.php](http://www.elifulkerson.com/articles/router-vs-comcast.php)

---

