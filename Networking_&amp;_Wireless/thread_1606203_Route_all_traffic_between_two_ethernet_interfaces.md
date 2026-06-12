---
title: "Route all traffic between two ethernet interfaces"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by kontozebyoszukacqnxa on 2010-10-26
Hi,

I have a Ubuntu box with 3 ethernet cards:
- eth0 - connected to internet (dhcp)
- eth1 - 192.168.0.1 connected to embedded device1
- eth2 - 192.168.0.1 also connected to embedded device2
(both eth1/eth2 have to be in identical, though separate, private networks).

Also, on eth0 I have two tunnel endpoints:
- vlan1 - 192.168.1.1 - virtual lan dev (OpenVPN or n2n)
- vlan2 - 192.168.2.1 - like previous

I would like to have access (from internet) to one of the embedded devices at a time through one of vlan devices (i.e. if I want to work with device1 I'll connect to vlan1 and at the same time someone else could work with device2 using vlan2 tunnel). Ah - both embedded devices have the same MAC addresses (I know it is wrong, but I cannot change their MACs).

OpenVPN in bridge mode is working only partially - it forwards ICMP traffic, even FTP, but not TCP/UDP packets (I've tried 'fragment' option, so it's not a problem of too big packets). What is more, the tunnel fails when embedded device restarts.

Hence my question - how to route/transfer all traffic from one ethernet device to another (eth1 <-> vlan1, eth2 <-> vlan2)? The lower operating layer (best would be MAC) the better.

---

### Post by psusi on 2010-10-26
You can not have two different interfaces with the same IP address.

Most embeded devices have a way to change their IP address, be it with a magic ping, or a configuration parameter over a serial port.  You will need to change their addresses so they are on different networks.

---

### Post by kontozebyoszukacqnxa on 2010-10-26
> **psusi said:**
> You can not have two different interfaces with the same IP address.
Why not? If the embedded devices had different MAC addresses, there wouldn't be a problem - ebtables can route packets based on MAC. But in this case even ebtables won't help.

> **psusi said:**
> Most embeded devices have a way to change their IP address, be it with a magic ping, or a configuration parameter over a serial port.
It was my first idea, but, believe me, I have tried everything and there is no way to change either IP nor MAC (in persistent way).

So, maybe I'll rephrase my question - is there any way to separate etherent cards and forward all traffic (preferably without any modification to packets) between a pair of interfaces?

---

### Post by lisati on 2010-10-26
> **kontozebyoszukacqnxa said:**
> Why not?
It can be a pain in the "you know where", just like a phone that's on a "[party line]("http://en.wikipedia.org/wiki/Party_line_%28telephony%29")".

---

### Post by psusi on 2010-10-26
> **kontozebyoszukacqnxa said:**
> Why not? If the embedded devices had different MAC addresses, there wouldn't be a problem - ebtables can route packets based on MAC. But in this case even ebtables won't help.

Because the IP address identifies the interface.  It's how the system knows where to send it to.  If both interfaces have the same address, which one do you forward the packet to?  There's no way to tell.

> **kontozebyoszukacqnxa said:**
> So, maybe I'll rephrase my question - is there any way to separate etherent cards and forward all traffic (preferably without any modification to packets) between a pair of interfaces?

Yes, you can bridge two networks together and that will forward the raw ethernet frames from one to the other, but that doesn't sound at all like what you want to do.

---

