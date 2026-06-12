---
title: "Splitting traffic on network device"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by mdewet on 2010-02-08
Hi All,

I'm faced with a networking problem and would appreciate some advice. I am manually capturing and injecting Ethernet traffic (using lib_net/lib_pcap libraries) for an application. At the moment , both capturing and injecting are done on the same physical interface (e.g. eth0). The problem is that all the traffic that I inject, are captured again by my application causing an unwanted feedback of injected traffic. This caused that I had to implement traffic filtering when capturing traffic, which is consuming resources and eventually will become too complicated to support.

I have tried using virtual interfaces to separate the capturing and injecting streams, but that also presented the same problem as all the traffic from eth0 is forwarded to both eth0:1 and eth0:2. 

Can someone please give some advice on possible solutions on separating the streams so that no feedback occurs? If possible I would like both streams to go through 1 physical device, using more PDs will be the last resort.

I am also looking at using TUN/TAP devices to try and separate the two streams, maybe writing a user-space program that lies between the physical device and the TUN/TAP devices to do the routing of traffic, but hopefully the Kernel has some way of solving the problem.

Any help appreciated

mdw
Ubuntu Server 9.04

---

