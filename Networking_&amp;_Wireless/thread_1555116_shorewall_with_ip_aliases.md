---
title: "shorewall with ip aliases"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by fdelval on 2010-08-17
let me show you my config and tell me if its ok

Its pretty simple:
eth2 ->  192.168.1.0 
eth2:0 ->192.168.50.0
eth1 and eth0 are the net interfaces, 1 router each to provide wan failover (not implemented here)


Hosts:
> 
loc1 eth2:192.168.1.0/24
loc50 eth2:192.168.50.0/24


Interfaces
> net6    eth0        detect
net7    eth1        detect
-    eth2    192.168.1.255,192.168.50.255

Masq
> eth0    eth2
eth1    eth2
eth2    eth2

Policy
> all    all    ACCEPT    info

Rules
SECTION NEW
> REJECT    loc50    loc1    all


Zones
> fw    firewall
net6     ipv4
net7     ipv4
loc1      ipv4
loc50      ipv4


Problems / Doubs:

**1) Is the hosts file required?**

2) I guess i need doing masq from local to each external, and also from local to local even if they share the same interface, hence the     [SIZE=3]**eth2 eth2**[/SIZE] in the masq file...

3) So is shorewall well implemented in these scritps to handle aliases?

---

### Post by fdelval on 2010-08-18
bumpy

---

### Post by fdelval on 2010-08-19
last

---

