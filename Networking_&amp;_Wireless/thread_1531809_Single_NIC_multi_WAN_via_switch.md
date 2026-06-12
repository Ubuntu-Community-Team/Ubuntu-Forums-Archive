---
title: "Single NIC multi WAN via switch"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by prashantjois on 2010-07-15
Hi,

I'm not sure if this is the appropriate forum on which to post this question.  Feel free to direct me to a more appropriate venue if this is the case.  I should mention too that I'm a bit of a novice when it comes to networking.

I have two internet connections through two different ISPs, let's call them IA and IB.  I have one server with two NICs (LAN and WAN) that I want to use as a firewall machine and for load balancing/failover.  This is the scenario I want to set up:

```
                ________              ________
IA <---------> |        |            |        |
               | switch |<------WAN->| server |<-LAN------> 
IB <---------> |________|            |________|
```


The switch is not VLAN or managed, just a simple switch.  IA and IB are accessible on the 192.168.30.0/24 and 192.168.40.0/24 networks, with gateways 192.168.30.1 and 192.168.40.1 respectively.

Is is possible to set the server up such that I can access both IA and IB through my one single WAN NIC?

I thought of perhaps setting the WAN NIC's main address to be in the 192.168.30.0/24 network, then setting up a virtual interface on the same card to be in the 192.168.40.0/24.

My /etc/network/interfaces would look something like this:

> auto lo
iface lo inet loopback

# LAN
auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0

# Primary WAN
auto eth1
iface eth1 inet static
address 192.168.30.101
netmask 255.255.255.0

# Secondary WAN
auto eth1:1
iface eth1:1 inet static
address 192.168.40.101
netmask 255.255.255.0

However, this scenario does not work as expected.  I'm unable to see the 192.168.40.0/24 network at all.

Is there any way to achieve what I want using a single WAN NIC like I described?

Thanks for any help

---

