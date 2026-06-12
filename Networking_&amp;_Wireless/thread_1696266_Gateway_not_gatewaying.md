---
title: "Gateway not gatewaying"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by sproot on 2011-02-27
This might well be user error, but I can't get my dual homed server to gateway.

There are two NICs:
```
# The internal network interface
auto eth0
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255 
# Outside interface                                                          
auto eth1
iface eth1 inet static
        address 192.168.2.4
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
```The routing table looks OK to me:
```
# ip route
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.4 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.4
default via 192.168.2.1 dev eth1  metric 100
```Forwarding is enabled:
```
# cat /proc/sys/net/ipv4/ip_forward 
1
```I was using shorewall, but I cleared it when the problem struck:
```
# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination 
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```But I can't ping even from one NIC to the other:
```
# ping -I eth0 192.168.2.4
PING 192.168.2.4 (192.168.2.4) from 192.168.1.4 eth0: 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
```It was working, until I was messing around with the patch cables and managed to get them swapped over. I've corrected them now but it no longer seems to pass packets between interfaces. I noticed because squid (transparently proxying) stopped working, other stuff on the box (postfix, dovecot, getmail, dnsmasq) is working fine, the internal NIC is visible from the internal network, the external NIC can access the 'net.

I've rebooted (more than once) but the problem persists, any network gurus spot anything obviously wrong?

TIA
sproot

---

### Post by Iowan on 2011-02-27
I'll admit to being unfamiliar with the intimates of **ping -I**, but if "Set source address"  means "send the ping out the specified interface", it *might* explain why an address in a different subnet cannot be found. 

Have you checked settings in **squid.conf**? I don't see why they might have changed, but sounds like most of the rest of the server is working...

---

### Post by sproot on 2011-03-04
Yeah, user error  :oops:   I was expecting that doing, for example, a traceroute from 192.168.1.x to 192.168.2.x would show 192.168.1.4 and 192.168.2.4 as hops, because the gateway is routing between the two networks. It doesn't, it just shows the source interface as a hop.  The issue was that the return route from the default gateway on the 192.168.2.0 network was wrong, packets were going out but didn't have a route back. When I fixed that it started working.  Doh!  Thanks sproot

---

