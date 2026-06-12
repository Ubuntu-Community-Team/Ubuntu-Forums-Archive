---
title: "Multiple ranges in a VLAN"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by KLStringer on 2010-05-27
We have the IP's  192.168.1.231 - 192.168.1.235 excluded from our current MS DHCP server scope. When I define the range for VLAN 1 on the Ubuntu DHCP server that we're going to how do I exclude this set from being given out?

Currently my conf file looks like:

```
### VLAN 1 ####
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.56 192.168.1.230;
range 192.168.1.236 192.168.1.250;
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option domain-name "harp.local"
}
```Is having the two separate range decelerations correct?

---

### Post by KLStringer on 2010-05-28
Really would like to get some feedback on this, we plan on going live with the new system this weekend when traffic will be low.

---

### Post by wirelessmonkey on 2010-05-28
Yes, your range statements are correct. Are you sure you want to use VLAN 1 though? It's typically the Management VLAN for most switches...

---

### Post by KLStringer on 2010-05-28
Unfortunately I don't have a choice, until we move off our aging Aspect ACD system to the Asterisk ACD system we're building the Aspect systems have to stay on the 192.18.1.0/24 network. I guess I could call it VLAN 100 though.

---

