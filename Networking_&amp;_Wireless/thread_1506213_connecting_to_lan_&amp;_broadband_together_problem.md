---
title: "connecting to lan &amp; broadband together problem"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by AQ80 on 2010-06-10
Hi all,

I need help ,I'm connecting to LAN through wired Ethernet and to mobile broad at the same time but I want to get my Internet from the mobile broadband connection while being able to see the local network and share printers.

the problem is when I go to any website it comes to me through the LAN (I know that because my LAN restricts most sites while my mobile broadband dose not)

thanks in advance   ):P


P.S. : a solution using GUI is not necessary but highly preferred.

---

### Post by Peter09 on 2010-06-10
if you type the command 
```
route
```
into the terminal you will see the routing preferences for your system. The key is the IP address of the default gateway, thats where your system will go to get something from the internet.

---

### Post by AQ80 on 2010-06-10
thanks peter09   ):P


I got this in the terminal 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
172.26.203.0    *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
default         172.26.203.230  0.0.0.0         UG    0      0        0 eth0


now how do I change the default gateway

---

### Post by Peter09 on 2010-06-10
The synax for route is
 
```
route add default gw <the ip address> 

```
 
and
 
```
route delete default gw <ip address>
```
 
worth a try.

---

### Post by AQ80 on 2010-06-10
Thank you Peter09

your the best 



this problem is solved :p:p:p:p

---

