---
title: "networking with 2 nics"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by AnalBeard on 2013-04-05
I've got 2 nics in my server, both of which are on different subnets but behind the same router. 

Below is my interfaces file, eth0 is in a separate vlan and is intended as the route to the internet. eth1 is a gigabit nic and intended to transfer traffic inside my lan.

```

# The loopback network interface
auto lo
iface lo inet loopback

#VLAN 2 external traffic
auto eth0
iface eth0 inet static
address 10.0.0.40
netmask 255.255.255.0
gateway 10.0.0.1
broadcast 10.0.0.255
post-up route add default gw 10.0.0.1 metric 1
pre-down route del default gw 10.0.0.1

#VLAN0 internal network
auto eth1
iface eth1 inet static
address 192.168.1.40
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
post-up route add default gw 192.168.1.1 metric 2
pre-down route del default gw 192.168.1.1

dns-nameservers 208.67.222.222 208.67.220.220 8.8.8.8

```

This produces this as a the routing table:

```

simon@sepulveda:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0           10.0.0.1        0.0.0.0             UG    1        0        0   eth0
0.0.0.0           10.0.0.1        0.0.0.0             UG    100     0        0   eth0
10.0.0.0          0.0.0.0         255.255.255.0    U      0        0        0   eth0
192.168.1.0     0.0.0.0         255.255.255.0    U      0        0        0   eth1

```

However, I'm getting 'destination unreachable' when i try and ping 8.8.8.8

Where am I going wrong?

---

### Post by Azrayal on 2013-04-05
Hi, 

So your goal is to have a subnet for transferring files and one for net access. 

If eth1 is only transferring files on the local subnet it doesn't need a gateway, removing that and restarting networking should resolve your issues.

---

### Post by AnalBeard on 2013-04-05
> **Azrayal said:**
> Hi, 

So your goal is to have a subnet for transferring files and one for net access. 

If eth1 is only transferring files on the local subnet it doesn't need a gateway, removing that and restarting networking should resolve your issues.

yes, this is correct, I intend all internet-bound traffic to use eth0, it didn't occur to me to remove the routes. I'll give that a try and see what happens!

---

