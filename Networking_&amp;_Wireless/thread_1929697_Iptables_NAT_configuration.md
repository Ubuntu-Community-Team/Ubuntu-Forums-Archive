---
title: "Iptables NAT configuration"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by ang3lo on 2012-02-22
Hi guys,

I need to translate the following Cisco configuration to Iptables

```
ip nat pool net-20 171.69.233.208 171.69.233.223 netmask <netmask> 255.255.255.240
ip nat inside source list 1 pool net-20
!
interface Ethernet0
ip address 171.69.232.182 255.255.255.240
ip nat outside
!
interface Ethernet1
ip address 192.168.1.94 255.255.255.0
ip nat inside
!
access-list 1 permit 192.168.1.0 0.0.0.255
access-list 1 permit 192.168.2.0 0.0.0.255

```

After read information about Iptables I would like to ask if the following configuration is correct and if is equivalent to the Cisco.

```
Iptables -t nat -A POSTROUTING -o eth0 -s 192.168.1.0/24 -j SNAT --to 171.69.233.208-.171.69.233.233
```

```
Iptables -t nat -A POSTROUTING -o eth0 -s 192.168.2.0/24 -j SNAT --to 171.69.233.208-.171.69.233.233
```

Thank you guys

---

