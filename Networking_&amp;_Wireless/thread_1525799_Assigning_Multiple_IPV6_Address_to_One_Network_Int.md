---
title: "Assigning Multiple IPV6 Address to One Network Interface?"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by fogNL on 2010-07-07
I have an ipv6 tunnel setup through freenet6, and I want to add multiple ipv6 address to the one eth0 interface.  I have done this in the past by manually adding the ip addresses using ifconfig.  But, I was wondering if there was a more automated way for my networking scripts to add them on boot up?  I'm running Ubuntu Server 10.04.

---

### Post by Brandon Williams on 2010-07-07
/usr/share/doc/ifupdown/examples/network-interfaces.gz contain the following example for IPv4:
```
# auto eth0 eth0:1
# iface eth0 inet static
#     address 192.168.0.100
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
# iface eth0:1 inet static
#     address 192.168.0.200
#     network 192.168.0.0
#     netmask 255.255.255.0
```
The same method should work for adding multiple IPv6 addresses. In this case, both addresses are static, but that doesn't have to be true of either one. I've used this method to add multiple dhcp assigned addresses to a single machine, too. The only important part is appending the ":<number>" to the interface name.

---

