---
title: "Routing issues (and failures)"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by StueyB on 2010-06-30
Hi Everyone,

Just want to ask a question about networking. I am playing around with networking and hitting some issues. Basically I am creating a 10.0.0.0/8 network in addition to the 192.168.1.0/24 I already have.

All I want to be able to do at this point is to create a separate network that can port forward (route) and talk to the internet.

I have a machine latest ubuntu with 3 nics. One nic (eth0) is plugged into a linksys WRT54G ethernet port with a DHCP provided address of 192.168.1.107
The gateway (internet bound) is 192.168.1.1 and the netmask 255.255.255.0

eth1 has a statically assigned ip of 10.0.0.1 and a subnet mask of 255.0.0.0

At the other end of the eth1 cable is a basic little machine running linux. It has a statically assigned ip of 10.0.0.2 with a netmask of 255.0.0.0. Default route is 10.0.0.1

This little machine can ping 10.0.0.1 fine. But it times out after that. I think it comes down to setting up the forwarding between the networks.

I have set ip forwarding in sysctl.conf and rebooted btw. 

What am I missing. I think it is just a forwarding rule. The main machine ( The one i suspect has the issue ) has its table below:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
10.0.0.0        *               255.0.0.0       U     1      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

