---
title: "2 Network Interface and 2 Routers / Gateways"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by cripperz on 2009-06-20
Hi All,

I am running ubuntu 8.04 LTS. I have 2 routers both different internet IP / Gateways. 

Router 1: 192.168.1.254 - 2wire
Router 2: 192.168.2.1  - Belkin

And the server has 2 ethernet interfaces. Eth0 and Eth1

Eth0: 192.168.2.10
Eth1: 192.168.1.100

I have tried serveral methods and even trying to change the metric but so far only i can only connect to Router 2 via internet and the ip it is showing is only from Router 2. Internally both routing is fine as i can connect the shared drive accordingly. 

Here is my route -n print out

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 eth1

```

And here is my /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.2.10
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        dns-nameservers 192.168.2.1
        dns-search ath.cx
        metric 0
        gateway 192.168.2.1
        up ip route add 192.168.2.0/24 via 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed


iface eth1 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        dns-nameservers 192.168.1.254
        dns-search gateway.2wire.net
        metric 1
        up ip route add 192.168.1.0/24 via 192.168.1.254

```

Hope i can get some guide and help from the guys who are experienced in such setup here.

Cheers

---

### Post by dmizer on 2009-06-21
First of all, please don't spam our forums with your link.

It depends on how you intend to use this dual network setup, but I believe you will need to do what's called "bonding" to make this work: [https://help.ubuntu.com/community/UbuntuLTSP/Trunking](https://help.ubuntu.com/community/UbuntuLTSP/Trunking)

---

### Post by cripperz on 2009-06-21
I am pretty much aware of the network bonding tool. But my concerns is as there are two routers, there are different computers connecting to the server for their shared drives. Therefore doing a network bonding my cause all these shared drive to lose their connection. Can someone with the knowledge of routing assist me on this ? I believe i just need to get the routing right to be able to have both adapters connect to the internet with their own internet IPs independently.

---

### Post by Iowan on 2009-06-22
I can't claim to understand your setup (so I'm primarily providing a bump), but I'm curious that you used a "route add" instead of defining a gateway on eth1 (which would be the Router1 that is having problems).

---

### Post by jhannah on 2009-06-24
You have two default gateways which is almost certainly not what you want. This will end with your machine having a split-brain routing topology for your network and likely many headaches. You need to decide which box the machine should route traffic to for networks that it doesn't have a directly connected route for (ie, everything other than 192.168.1.0/24 and 192.168.2.0/24). By nature, only one route would be selected. The metric merely determines which route that would be.

It sounds like you really need a box between this one and your internet connections which will act as a packet scheduler and spread the load between two uplinks. This isn't really a trivial task and isn't something IP will just figure out on it's own. I haven't ever set anything up like this but using pfSense/m0n0wall/smoothwall should do the trick. This box would act as a Layer 3 demarcation between your machines and your internet connections.

Does that speak to your question?

---

