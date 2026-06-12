---
title: "How do I disable DHCP?"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by RuleMaker on 2009-10-16
I have googled and tried few solutions but none of them worked.
The problem is that I have configured my /etc/network/interfaces to have a static IP address but still, when I restart my PC it assigns a different IP address than I have defined in interfaces file.
When I run sudo /etc/init.d/networking restart it assigns the correct IP to eth0 interface.

I assume that, instead of looking in the interfaces file, the system uses the DHCP to assign an IP address to my PC on system boot.

How could I disable the DHCP on startup or could it eventually be something else that is causing this (ARP or something else)?

---

### Post by RuleMaker on 2009-10-16
I have noticed a strange thing, ifconfig says that my local IP is 192.168.1.2 while the network-admin GUI says it's 192.168.1.3 (which it should be).

I trust to ifconfig since when I turn on the other PC on the network I lose my internet connection, probably because of conflicting IP addresses.

Here is how my interfaces file looks like:
```
auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

---

### Post by jonobr on 2009-10-16
what happens when you ping 
192.168.1.2 and then 192.168.1.3?
from a terminal window
One of them is lying to you, which ever doesnt respond is telling porkies....

---

