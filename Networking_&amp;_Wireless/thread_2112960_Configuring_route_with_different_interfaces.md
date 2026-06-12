---
title: "Configuring route with different interfaces"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by ranjithr on 2013-02-06
Hi,
I have a PC with Ubuntu 10.04 running on it. The PC have 6 Ethernet interfaces. I want to configure all with static IP. The first one, eth0 si to be connected in a public domain and all the others to a private domain with same gateway and same netmask. The */etc/network/interfaces* is like below : 
```
auto eth0 eth1 eth2 eth3 eth4 eth5

iface eth0 inet static
address xx.4.8.180
gateway xx.4.8.254
netmask 255.255.255.0

iface eth1 inet static
address 192.168.1.201
gateway 192.168.1.254
netmask 255.255.255.0

iface eth2 inet static
address 192.168.1.202
gateway 192.168.1.254
netmask 255.255.255.0

iface eth3 inet static
address 192.168.1.203
gateway 192.168.1.254
netmask 255.255.255.0

iface eth4 inet static
address 192.168.1.204
gateway 192.168.1.254
netmask 255.255.255.0

iface eth5 inet static
address 192.168.1.205
gateway 192.168.1.254
netmask 255.255.255.0

```

The end idea is to make the five Ethernet interfaces like an network switch. That is if I ping 192.168.1.101, I should get the reply if I connect the cable to each one of the interfaces. I could not do that currently. It works sometimes from eth1, sometimes from eth5. 

The route table is as below:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth5
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth3
192.168.1.0     *               255.255.255.0   U     0      0        0 eth4
xx.4.8.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth5
default         *               0.0.0.0         U     0      0        0 eth0
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth4
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth3
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth2
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth1
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth5

```
Please help.

---

### Post by PowerBarry43 on 2013-02-06
Hi

Ok so what your trying to do here is slightly complicated because each of your interfaces needs to have an ip address, making it more like a router than a switch which works entirely on mac addresses. 

here is some info on how you can do it:

[http://pontus.ullgren.com/view/multiple_interfaces_on_the_same_subnet](http://pontus.ullgren.com/view/multiple_interfaces_on_the_same_subnet)

Hope this helps!

Barry

---

### Post by ranjithr on 2013-02-06
Thank you Barry for your quick reply. I will check by the method proposed and will revert. 

Thanks,
Ranjith

---

### Post by ranjithr on 2013-02-06
Hello Barry,
I am a relatively inexperienced in Linux. In the link posted by you, it says that there are some prerequisites - below values be enabled in the kernel:
```
CONFIG_IP_ADVANCED_ROUTER=y
CONFIG_IP_MULTIPLE_TABLES=y
CONFIG_IP_ROUTE_FWMARK=y
CONFIG_IP_ROUTE_MULTIPATH=y
CONFIG_IP_ROUTE_VERBOSE=y
CONFIG_NETLINK_DEV=y
```

When I surfed the net and some other forums, there was option given to make CONFIG_IP_ADVANCED_ROUTER=y by executing the line
         echo "1" > /proc/sys/net/ipv4/ip_forward
I could not find any options to enable the other parameters.
Please Help.
Ranjith.

---

