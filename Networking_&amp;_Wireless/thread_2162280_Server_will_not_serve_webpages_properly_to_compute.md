---
title: "Server will not serve webpages properly to computers on same network or itself"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by capthawkeye24 on 2013-07-13
Hello everyone!

The 12.04 linux server I have been working on will not serve webpages properly to computers on the same network as the server or to itself. Would anyone here happen to have a solution to this issue? 

The server does however serve webpages to computers outside of it's network perfectly fine. 

Thank you!

Brett

---

### Post by steeldriver on 2013-07-13
Hello and welcome to the forum

How are you addressing the server from inside the LAN? if you are trying to access it via your public (external) IP, I think that will only work if your router supports (and is configured for) NAT loopback --> [https://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback](https://en.wikipedia.org/wiki/Network_address_translation#NAT_loopback)

---

### Post by capthawkeye24 on 2013-07-13
We are trying to access the server via the internal IP. 10.1.10.10.. We also tried to serve the pages directly on the server by typing localhost in the address bar to no avail.

---

### Post by capthawkeye24 on 2013-07-16
Bump! Trying to figure this out, any help would be nice!

---

### Post by steeldriver on 2013-07-16
I am only just getting my feet wet with apache2 but maybe you have deny rules for the localhost and LAN IP in your /etc/apache2/sites-available/yoursite file? or you have bound apache2 to the public hostname/IP only instead of *:80?

---

