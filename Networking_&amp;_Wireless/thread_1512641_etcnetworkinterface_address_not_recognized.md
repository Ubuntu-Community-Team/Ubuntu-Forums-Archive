---
title: "/etc/network/interface address not recognized"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by jmcalpi on 2010-06-18
Showing my ignorance, but why would this work
 
address 172.16.1.8
netmask 255.255.254.0
network 172.16.1.0
broadcast 172.16.2.255
gateway 172.16.2.254
 
But this would not work
 
address 172.16.2.8
netmask 255.255.254.0
network 172.16.1.0
broadcast 172.16.2.255
gateway 172.16.2.254
 
Notice the 2 in address.  Seems to me it doesn't like the network and wants it to be 172.16.0.0, but I am adding to a network already configured this way.  Thanks

---

### Post by Iowan on 2010-06-18
I need to use a [subnet calculator]("http://www.subnet-calculator.com/cidr.php") to decipher such things. Looks like 172.16.1.8 is in the subnet 172.16.0.0 - 172.16.1.255, whereas 172.16.2.8 is in the subnet: 172.16.2.0 - 172.16.3.255...

---

