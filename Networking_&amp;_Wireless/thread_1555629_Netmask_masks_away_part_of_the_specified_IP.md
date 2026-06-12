---
title: "Netmask masks away part of the specified IP"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by titanicmusic14 on 2010-08-18
[B]Netmask masks away part of the specified IP in '192.168.10.100-192.168.10.200/24'

What does this mean?
[/B]

---

### Post by Brandon Williams on 2010-08-18
Each part of the 4 parts of the IP address is referred to as an octet, which means that it has 8 bits. This type of netmask specification declares the number of bits used to represent the network. In this case, you've said that 24 bits (3 octets) represent the network. The warning message in question is indicating that the address you specified (192.168.10.200) has a non-zero value in the fourth octet and that this value will be ignored due to the specified netmask. You probably want "192.168.10.0/24".

---

### Post by Iowan on 2010-08-18
There are several online subnet calculators ([here]("http://www.subnet-calculator.com/cidr.php") for example). They are handy for working out which subnet starts where for what mask, etc...

---

