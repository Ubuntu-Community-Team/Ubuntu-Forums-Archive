---
title: "2 netmask/gateway routing"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by lianne_john07 on 2011-06-17
Help! Please!

eth0
address 192.168.2.1
netmask 255.255.255.240
gateway 192.168.2.30

eth1
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.30

How can i use them both at the same time.

---

### Post by elliotbeken on 2011-06-17
> eth0
address 192.168.2.1
netmask 255.255.255.240
gateway 192.168.2.30

The netmask and the gateway are in two different networks. In other worlds they don't match the mask

The range for 255.255.255.240 would be 192.168.2.1 - 192.168.2.14 (usable)

---

### Post by elliotbeken on 2011-06-17
If you anted to have the netmask for eth0 as 192.168.2.30 you will need the mask as 255.255.255.224.

---

### Post by capscrew on 2011-06-17
> **elliotbeken said:**
> If you anted to have the netmask for eth0 as 192.168.2.30 you will need the mask as 255.255.255.224.

Although the OP probably did not intend to have the gateway outside of the local network, there is no reason that the the gateway (default route) has to be in the same subnet as all of the other hosts.  

Admittedly, this is not common, but it is perfectly legitimate.  You must state it differently than the OP has though.  First you have to declare the route and then make it the gateway.

Taken as a whole there are other problems.  Is this multihomed host serving as a router? Why 2 gateway addresses?

---

### Post by lianne_john07 on 2011-06-17
my bad for the gateway error, assuming that the gateway is 14.
Can you teach me how to make this work?

@capscrew-- no, there is two gateway at my office. and i can't make both of this to work at the same time.

---

### Post by capscrew on 2011-06-17
> **lianne_john07 said:**
> my bad for the gateway error, assuming that the gateway is 14.
Can you teach me how to make this work?

@capscrew-- no, there is two gateway at my office. and i can't make both of this to work at the same time.

You can't.  This is by design.  Unless the host is a gateway (router) between 2 networks or the interfaces are bonded and in one network, you should only have 1interface active on your computer at any one time.

---

