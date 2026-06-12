---
title: "Network Bridge Issue"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by justjustin on 2012-09-22
Hi, I have created a network bridge in ubuntu and it seems to be working correctly apart from one issue which is holding me back.

I have created the bridge as root like so:

```
tunctl -t tap0 -u zombie
ifconfig tap0 0.0.0.0 promisc up
ifconfig eth0 0.0.0.0 promisc up
brctl addbr br0
brctl addif br0 tap0
brctl addif br0 eth0
ifconfig br0 192.168.1.4/24 up
route add default gw 192.168.1.1
route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.1.254
```


My eth0 interface is connected to my physical internet router and the tap0 interface is connected to a GNS3 router. **The GNS3 router has a default route to 192.168.1.1 and has internet connectivity.** No problem there, the bridge appears to be functioning correctly.

I am encountering difficulty when I add another network in GNS3, in this case, the network 192.168.100.0. 

This is my current topology to make things a little clearer:

Physical (Internet) Router -- 192.168.1.1
(eth0)Ubuntu Host(tap0)------ 192.168.1.4
Router1[f0/0](GNS3) --------- 192.168.1.254
Router1[f1/0](GNS3) --------- 192.168.100.254
Ubuntu-Server(Vbox) --------- 192.168.100.1

And this is the routing table from my Ubuntu-Host:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         voyager.home    0.0.0.0         UG    0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.100.0   192.168.1.254   255.255.255.0   UG    0      0        0 br0
```

**The Ubuntu Host (192.168.1.4) is able to ping the Ubuntu-Server VM @192.168.100.1 and vice versa.** 

**Why am I unable to achieve internet connectivity on the Ubuntu-Server VM?** 

I got this working a couple of days ago and I was sure I had entered the commands above to achieve this but I must have missed something or done something slightly different. **Is it a firewall issue?** I have tried these commands:

```
iptables -I INPUT -j ACCEPT -i br0
iptables -I OUTPUT -j ACCEPT -o br0
```

...which I believe allow ALL traffic through the bridge but I am unsure as I am not familiar with iptables(yet!). I also have no idea of the security issues these could raise for my Host system.

Please, please, help me! **Any** help or comments at all would be so appreciated even if it is only with one aspect of my problem. Thank you in advance.

---

