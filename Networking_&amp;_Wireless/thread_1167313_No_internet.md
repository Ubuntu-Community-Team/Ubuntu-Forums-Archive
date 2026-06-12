---
title: "No internet"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by grandkodiak on 2009-05-22
So I finally got kubuntu up and running and i cant get any internet to download updates/drivers to finish getting all my hardware running 100%.
 
im new to linux so maybe im missing something.
 
i set up my manual ip, gateway, subnet and dns servers, yet i cant even ping my router let alone connect to a website. whats wrong?
 
i noticed that it wants a netmask prefix, i have no idea what that is so i left it blank, and a mac address... why doesnt it get that info automatically? does it need that to even connect?
 
please help, this is entirely frustrating.

---

### Post by Iowan on 2009-05-22
Prefix or suffix? CIDR uses a number instead of netmask - so 255.255.255.0 becomes /24.

---

### Post by superprash2003 on 2009-05-23
post the contents of your /etc/network/interfaces file

---

