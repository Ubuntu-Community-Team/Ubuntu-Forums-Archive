---
title: "dhcp reservations"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by mansour on 2010-10-14
I wondwer whether ip reseravtions should always be made inside of range in dhcp servers or even is possible to make outside reservations. This is just a curious question I am asking.
 
 
Thank you

---

### Post by capscrew on 2010-10-15
> **mansour said:**
> I wondwer whether ip reseravtions should always be made inside of range in dhcp servers or even is possible to make outside reservations. This is just a curious question I am asking.
 
 
Thank you
A reservation is for a *specific *IP address from the DHCP pool based on client's MAC address (hardware address).  The addresses that a DHCP server controls are only from that pool.  

There is no way for the DHCP server to hand out anything that is not part of that pool.  You can configure the range of IP addresses the DHCP server controls (the pool) for a given subnet.  

The IP addresses in that subnet that are not part of the pool must be statically configured.

---

