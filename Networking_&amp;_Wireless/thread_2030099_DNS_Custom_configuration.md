---
title: "DNS Custom configuration"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by enterdavertex on 2012-07-20
Hello everybody , I am have a monitoring system that monitor all the computer of every machine into my network , the problem is I actually monitor some other network over the internet. All i wanted to do is actually use a external DNS server when the dns is *.com, that way that would reduce the DNS traffic over my main DNS server.  

Thank you everyone for your precious time.

---

### Post by efflandt on 2012-07-22
If you are using bind9 (named), just make sure that **forward first;** is either not in, or commented out (# prefix). in your named.conf options so that is not active.

Then if you have forward and reverse zones properly defined for your LAN, your nameserver should only query the internet for names or IP's it does not have zones for.

---

