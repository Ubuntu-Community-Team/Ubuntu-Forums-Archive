---
title: "Problems with Static IPs and Routes"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by amarcionek on 2012-02-01
Hi all,

I'm having issues with static IP routing with more than one interface configured. What I would like to do is have 2 ethernet interfaces configured for link redundancy and load balancing.  But with 2 interfaces up, I can't get to the internet.  (I.e. ping google.com)  

The following is my /etc/network/interfaces for Server 10.04

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.20.248
netmask 255.255.255.0
gateway 192.168.20.1

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.20.249
netmask 255.255.255.0
gateway 192.168.20.1

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.20.1    0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.20.1    0.0.0.0         UG    100    0        0 eth0

On this server, If I bring either eth0 or eth1 down, I can ping google.com just fine. 

Interestingly enough, if I do a manual *route add default gw 192.168.20.1*, I can then ping google.com with both interfaces up.  Here is the routing table after the route add, notice the 3rd line:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.20.1    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.20.1    0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.20.1    0.0.0.0         UG    100    0        0 eth1

I would like to get this server to a place where a service or server restart doesn't clear out the settings to the route add is not desirably.

I don't think its DNS because the ping resolves to an IP address rather quickly. It just can't get there:

amarcionek@UbuntuOpenStack:~$ ping google.com
PING google.com (74.125.113.103) 56(84) bytes of data.

Here is the /etc/resolv.conf:

nameserver 192.168.20.1
nameserver 192.168.20.22
nameserver 192.168.20.20


Thanks for any help!
Adam

---

