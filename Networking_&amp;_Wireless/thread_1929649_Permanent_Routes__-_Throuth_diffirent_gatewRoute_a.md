---
title: "Permanent Routes  - Throuth diffirent gatewRoute add -p [IP] netmask [mask] [gateway]"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by chimeradeimos on 2012-02-22
Hi Guys

I want to know how to add routes to ubuntu 11.10. network manager isnt really working and as sson as I restart all the routes go missing.

Details of my network:

I run a network with a 192.168.xxx.xxx range with a subnet of 255.255.252.0 and then we got external branches connecting via vpn with 192.168.xxx.xxx with the subnet of 255.255.255.0

My default gateway that i use to connect to the internet differs from those that the other users connect to. In windows i use the following command in cmd to add the route and everything works:

Route add -p [IP] netmask [mask] [gateway]

almost the same as on ubuntu..

sudo route add -net 192.168.164.0 netmask 255.255.255.0 dev eth1

and this is the output I get from netstat:


$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.150.250 0.0.0.0         UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
192.168.148.0   0.0.0.0         255.255.252.0   U         0 0          0 eth0
192.168.148.0   0.0.0.0         255.255.252.0   U         0 0          0 eth1
192.168.164.0   0.0.0.0         255.255.255.0   U         0 0          0 eth1


Somehow this just doesnt look right to me as the gateway is my internet gateway and not our vpn gateway...

how can I change this and make tre routes permanent?

---

