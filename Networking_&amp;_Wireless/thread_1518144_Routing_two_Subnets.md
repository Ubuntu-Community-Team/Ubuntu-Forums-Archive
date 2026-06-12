---
title: "Routing two Subnets"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by Lord_Devi on 2010-06-26
I have two subnets which I am interested in connecting. I've read from beginning to the Linux Networking HOWTO, a few guides here on nixCraft, many forums posts, but have so far succeeded only in confusing myself.

Some basic network details:

Subnet A:
 Network Range: **192.168.1.0/24**
 *Gateway 1A*: **192.168.1.1/255.255.255.0**
  Gateway Interfaces:
  *br0*: **192.168.1.1/255.255.255.0**
  *vlan1*: **70.76.84.224/255.255.252.0**
 LAN Domain: tec.lan
 Example *Host 1A*: **perpetrator.tec.lan - 192.168.1.10/255.255.255.0**
 Example *Host 2A*: **rapine.tec.lan - 192.168.1.11/255.255.255/0**

Subnet B:
 Network Range: **192.168.2.0/24**
 *Gateway 1B*: **192.168.2.1/255.255.255.0**
  Gateway Interfaces:
  *eth0*: **192.168.1.145/255.255.255.0**
  *eth1*: **192.168.2.1/255.255.255.0**
 LAN Domain: tec.lan
 Example *Host 1B*: **ubuntu-01.tec.lan - 192.168.2.10/255.255.255.0**
 Example *Host 2B*: [B]ubuntu-02.tec.lan - 192.168.2.11/255.255.255.0
[/B]

I am trying to think of any further relevant details, but that seems to be it to me. If I forgot anything, please tell me.

Ok the question. WHAT do I type? (Explicitly!) And WHERE do I type it? In order to reach **ubuntu-01.tec.lan**, or **ubuntu-02.tec.lan** from **perpetrator.tec.lan** or **rapine.tec.lan**?

Note: I'm interested in using actuall ROUTES. I can already achieve results similair to this with either a NAT firewall, or with VPN.. but that's not what I am interested in.

Thank you very much for your reads and help in advance! This seems like it should be a simple thing, but I am having incredible difficulty with this..

From what I have found out so far, I should need something like the following:

On *Gateway 1B*:
```
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.2.1 dev eth1
```

And on *Gateway 1A*:
```
route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.1 dev br0
```

Any help would be appreciated!

---

### Post by Brandon Williams on 2010-06-28
Based on the details you provided, gateway 1B is on both subnets, correct? eth0 is on subnet 192.168.1.0/24 and eth1 is on subnet 192.168.2.0/24. If this is true, then there should be no need to add any routes on gateway 1B. Gateway 1A, on the other hand, is only on 192.168.1.0/24, so you will need a routing table entry there:
```
route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.145
```
Note that you don't have to specify the device because gateway 1A only has one interface on the 192.168.1.0/24 subnet.

---

### Post by Lord_Devi on 2010-06-30
hehe.. Yeah ok. I suppose I could have clarified things further by stateing what it is I am actually trying to accomplish. The 192.168.1.0/24 network is my physical network, while 192.168.2.0/24 network is a Virtual network consisting of a series of virtual machines which are set to use Host Only networking. I wanted the two to be able to communicate with each other without the use of network address translation or other such hackish mechanisms. 

I don't have the time at the moment to test that line out.. but I shall later on today or tomorrow.

I see exactly what you are saying and it seems to actually make sense to me!! hehe, which is refreshing. Gateway 1B is indeed on both subnets. Where as Gateway 1A is actually a DD-WRT routing device that I use to connect my physical network to the Internet. Gateway 1B is the actual Host machine on which the Virtual Network is running. I think your advice has probably hit the solution bang on, but I'll have to test it to be sure in a bit here..

Thanks a lot for the help and advice Brandon. I'll post later on with success or failure to let the forum know how things went. 

This subnetting stuff seems so simple in concept but is easy to get lost in all the numbers, devices, and terminology...

---

### Post by Lord_Devi on 2010-07-10
Just an update.. I have it all working perfectly now. The correct answer was:

1. Tell the machines on Subnet B to use 192.168.2.1 as their gateway, and:

2. On Gateway 1A, configure a static route telling packets trying to reach 192.168.2.0/24 to use 192.168.1.145 as their gateway.

```
route add -net 192.168.2.0/24 gw 192.168.1.145
```

Thank you for your time.

---

