---
title: "easy way of keeping dhcp server and nameserver in sync?"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by andreas.kotowicz on 2009-07-12
I have a small dhcp server running that takes care of giving fixed IP address to specific MAC addresses. Is there an easy way to use this config file in order to configure my nameserver? I don't want to type in all the information by hand :)

---

### Post by superprash2003 on 2009-07-12
here is my dhcpd.conf file

[B]default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.254;
option domain-name-servers 208.67.222.222, 208.67.220.220;
option domain-name &#8220;HOME&#8221;;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.15;
}[/B]

this is the line you need to add

**option domain-name-servers 208.67.222.222, 208.67.220.220;**

---

