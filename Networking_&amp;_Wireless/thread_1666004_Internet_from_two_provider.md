---
title: "Internet from two provider"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by Farrukhjon on 2011-01-13
[SIZE=4]**How to organize in one server the Internet from two providers (ADSL) ? It is thankful in advance.**[/SIZE]

---

### Post by ripat on 2011-01-13
Hi,

It is possible with 2 NIC on the WAN side and 1 on the LAN side. Use the *ip* command (a utility from iproute2) for load sharing and balancing.

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

Also, posting in ALL CAPS is generally viewed as SHOUTING.

---

### Post by Farrukhjon on 2011-01-13
[SIZE=3][B]It is very grateful for the link.

Whether there is a way to organize through SQUID?

[/B][/SIZE]

---

### Post by sj1410 on 2011-01-13
> **Farrukhjon said:**
> It is very grateful for the link.

Whether there is a way to organize through SQUID?



no this is not possible thru squid. you need iproute2 to achieve this.

or 

[http://www.pisces.net.in/p/effortless-linux-based-firewall.html](http://www.pisces.net.in/p/effortless-linux-based-firewall.html)

---

