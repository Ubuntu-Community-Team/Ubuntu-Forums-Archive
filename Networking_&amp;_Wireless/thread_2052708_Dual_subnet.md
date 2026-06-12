---
title: "Dual subnet"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by maxicool on 2012-09-03
i have two ethernet cards connected on two separated network.

device eth0 
ip 192.168.0.14
network 192.168.0.0/255.255.255.0
gw 192.168.0.1

device eth2
ip 192.168.68.14
network 192.168.68.0/255.255.255.0
gw 192.168.68.254

here is my /etc/network/interface :

auto eth0 
iface eth0 inet static
address 192.168.0.14
netmask 255.255.255.0
gateway  192.168.0.1

auto eth2
iface eth2 inet static
address 192.168.68.14

after network restart, i can only access network through eth0.
what should i do so that i can also access 192.168.14.0 network ?

---

### Post by papibe on 2012-09-03
Hi maxicool. Welcome to the forums ):P

Try setting both netmask and gateway for the other interface too:
```
auto eth0 
iface eth0 inet static
    address 192.168.0.14
    netmask 255.255.255.0
    gateway 192.168.0.1

auto eth2
iface eth2 inet static
    address 192.168.68.14
    netmask 255.255.255.0
    gateway 192.168.68.254
```
Let us know how it goes.
Regards.

---

### Post by opensshd on 2012-09-03
How are you specifying what application accesses from which adapter?

---

### Post by Iowan on 2012-09-03
Post results of **ifconfig -a**. 
If I understand correctly, the gateway should be where the system sends traffic not otherwise specified. Traffic going to the subnets should be directed there... traffic to eg. 8.8.8.8 would be directed through the gateway interface.

You might also check **route -n** to see the routing table.

---

### Post by maxicool on 2012-09-09
Tanks a Lot, everyone! I found Out that i made a silly mistake.  The local network is on eth1 instead of eth2.  Sorry for troubling you guys.

---

