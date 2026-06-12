---
title: "ubuntu routing issue"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by mahoney362 on 2013-05-28
Hi guys,

A question regarding the routing within Ubuntu Server 10.04.

I have one Ubuntu server machine with two interfaces virtualized on Hyper V. Both interfaces have been confirmed and are working.

Here are the results from an ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:15:5d:01:5b:1c
          inet addr:192.168.0.232  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:5dff:fe01:5b1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12951 errors:0 dropped:2843 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:967626 (967.6 KB)  TX bytes:1252 (1.2 KB)


eth1      Link encap:Ethernet  HWaddr 00:15:5d:01:5b:1d
          inet addr:10.0.1.232  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:5dff:fe01:5b1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32250 errors:0 dropped:285 overruns:0 frame:0
          TX packets:4183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3718844 (3.7 MB)  TX bytes:301101 (301.1 KB)

The eth0 interface is connected to a infrastructure network while eth1 is an interface to the colo network

The problem i'm having is there are some colo addresses with the ip address 192.168.0.X e.g. 192.168.0.49, 192.168.0.130. When trying to contact these addresses, they aren't responding. After performing a traceroute, it appears as though the traffic is trying to go out eth0 interface i suspect because of the 192.168.0.232 address on eth0.

Is there a way I can tell ubuntu that if it can't contact an address, try a different interface?

I would simply add a static route however it isnt feasible because there a 50+ addresses in the colo network with the range of 192.168.0.X

---

