---
title: "Multiple external IP's, want to NAT through specific IP."
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by twocom on 2009-02-04
Hi,

I have a /27 assigned to my internet connection. 2 of these publc IP's are assigned to my Ubuntu server. I have some internal machines that NAT out through the Ubuntu server. I want the internal machines to route out through the 2nd IP on the Ubuntu server (that sits on its own interface) but I'm having difficulty trying to get my head around what needs to be done to allow this to work.

My network interfaces are setup as follows:

eth0: public ip
eth1: public ip
eth2: internal lan

Requests for the internet that come over eth2, I want routed out through eth1. I added the following to /etc/ufw/before.rules 

-A POSTROUTING -s 192.168.0.0/24 -o eth1 -j MASQUERADE

but it doesn't allow the internal lan internet access. Changing -o to eth0, allows it to work but it obviously routes out through the eth0 IP which isn't what I want.

I'm not sure if I need to be adding some other iptables rules or this is a routing issue. Whilst I'm on the topic of routing, this is what my routing table looks like:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.224   *               255.255.255.224 U     0      0        0 eth0
xxx.xxx.xxx.224   *               255.255.255.224 U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
default         r.XXXX.com       0.0.0.0         UG    100    0        0 eth0

Should I be adding a route for eth1?

Any help greatfully received.

Thanks,
Paul.

---

### Post by josephalevin on 2010-11-29
Paul,
Did you have any luck finding a solution?  I'm struggling with the same situation. 

Joseph

---

