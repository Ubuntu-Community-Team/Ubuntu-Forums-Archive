---
title: "Internal Router"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by Lambchopper on 2009-07-14
To anyone that can help: 

I'm using Ubuntu Server 9.04 to try and build a captive portal.  Before I can even work on the Captive Portal, I have to get the server to work as a router, routing between two private networks. 

**Here's what I have: ** 

ETH0: 10.254.1.128/27
ETH1: 192.168.102.0/24

**Contents of /etc/network/interfaces:**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 10.254.1.130
netmask 255.255.255.224
gateway 10.254.1.129

# The Inside network interface
auto eth1
iface eth1 inet static
address 192.168.102.1
netmask 255.255.255.0

**Output of the sudo cat /proc/sys/net/ipv4/ip_forward**
1


**Output of the route -n command**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.254.1.128    0.0.0.0         255.255.255.224 U     0      0        0 eth0
192.168.102.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.254.1.129    0.0.0.0         UG    100    0        0 eth0

**I'm not using Iptables or any firewalling, just ip forwarding.  Here's the output of iptables -nvL so show that**

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 



I can ping both the 10.254.1.130 and 192.168.102.1 interfaces of the server from either side of the server.  But I can't ping anything beyond that.  (E.G. A host on 192.168.102.10 can ping 10.254.1.130, but not 10.254.1.129).  I can't seem to figure out why as the routing table appears to be correct but packets won't pass to the other network.  Any ideas?

---

### Post by Lambchopper on 2009-07-14
Never mind...   Turned out to be a downstream static route on one of my Cisco routers....  Sweet!

---

