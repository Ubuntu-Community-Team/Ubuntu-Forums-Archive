---
title: "pinging problem"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by CEYLON on 2011-01-19
I am not able to ping in to my ubuntu box from a defferent network
 
but i can ping the default gateway of that ubuntu box (it is a cisco router)
 
is it a icmp problem??

---

### Post by koszta on 2011-01-19
Yeah, it could be.. If I were you I would try to see if the default route is set properly by using: 
```
route -n
```

Oh and make sure that your iptables arent blocking anything  (but by default it should be off without any firewall)
If all is well then I would probably try to look for the problem in cisco router 
```
show runconfig
```
-> that will give you more info than you need... you gotta go through it and see for yourself

---

### Post by CEYLON on 2011-01-19
Thank you

---

### Post by Iowan on 2011-01-19
I'm a bit curious if the Ubuntu box has a "private" IP address. (192.168.X.X, 10.X.X.X, 172...). The router might not (hopefully) let an external address ping into your network.
(eg. you can ping my router's external address, but even if you know this machine has 192.168.1.13, you can't ping it from outside my network)

---

