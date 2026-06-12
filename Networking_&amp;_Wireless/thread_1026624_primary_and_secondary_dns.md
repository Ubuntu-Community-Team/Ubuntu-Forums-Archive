---
title: "primary and secondary dns"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by cancertropica on 2008-12-31
Hello friends,

I am facing one problem that i am unable to figure out where i set primary and secondary dns setting.meaning their address.when i see etho(0) it shows same 192.168.1.1 in all .mean primary dns ,secondary dns and default route.


I want to know how i set my other server at primary and secondary dns.

This all i want to do because i have slow Internet. I am using ubuntu 8.10 desktop.

please help me . I am new to Linux world.

---

### Post by Blackwood on 2008-12-31
DNS servers are set using the Network Configuration Tool.  System->Administration->Network select Unlock then the DNS tab.  The order in the list determines Primary, Secondary, etc.  DNS settings are not entered for each interface.  It is a global setting that all interfaces use.

---

