---
title: "IPsec and bridging question"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by redocdlo on 2010-06-08
Hello,
I am totally new to Linux and am both impressed and confused.
 
I need an IPSec solution and am unclear if Linux can do what I want.
 
I have a linux box acting as a transparent bridge between a small private LAN (IPv6) and the IPv6 WAN and want it to also apply IPsec on behalf of one or more of the hosts on the bridged private LAN.
That is, I want the bridge to enforce IPSec policy between the very few protected hosts and the many remote peers by: 
 - establishing an outgoing SA with a destination peer on behalf of a local host
 - intercept incoming IKEv2 traffic destined for one of the protected local hosts, and 
   perform the negotiation masquerading as that host.
 - establish an incoming SA with a peer if an unencrypted packet is received, 
   again masquerading as the local host. 
 
Both transport and tunnel modes are necessary.
 
I do NOT want to encapsulate an entire ethernet frame.
 
There is some indication that it could be done via IPTABLES.
Has anyone already done this?

Any tips or pointers would be appreciated
 
thanks

---

