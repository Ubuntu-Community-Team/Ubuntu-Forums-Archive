---
title: "multiple nics, connection from 'other' subnet does not respond"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by jforman on 2012-11-04
I just slapped a second NIC into my Ubuntu server. I want to be able to run VM's on this machine that can connect to one or both subnet. But before I hook up any of the VMs, I want to confirm that the underlying Ubuntu server can talk to machines on both subnets. When I try to ping (or otherwise connect) to the interface of one NIC from a machine on the 'other' subnet, I get no response.

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
      address 10.10.0.21
      network 10.10.0.0
      netmask 255.255.255.0
      broadcast 10.10.0.255
      gateway 10.10.0.1
      bridge_ports eth0
      bridge_stp off

auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
      address 10.10.1.21
      network 10.10.1.0
      netmask 255.255.255.0
      broadcast 10.10.1.255
      bridge_ports eth1
      bridge_stp off

```Ifconfig output:
```

br0       Link encap:Ethernet  HWaddr 00:e0:81:78:de:ca  
          inet addr:10.10.0.21  Bcast:10.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe78:deca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:908860 (908.8 KB)  TX bytes:16832741 (16.8 MB)

br1       Link encap:Ethernet  HWaddr 00:e0:81:78:de:cb  
          inet addr:10.10.1.21  Bcast:10.10.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe78:decb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45643 (45.6 KB)  TX bytes:1092 (1.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:e0:81:78:de:ca  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5026123 errors:6 dropped:0 overruns:6 frame:0
          TX packets:3796358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3142984067 (3.1 GB)  TX bytes:1732983139 (1.7 GB)
          Interrupt:43 

eth1      Link encap:Ethernet  HWaddr 00:e0:81:78:de:cb  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1322198 errors:4 dropped:0 overruns:0 frame:2
          TX packets:1297611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:535400558 (535.4 MB)  TX bytes:140613057 (140.6 MB)
          Interrupt:44 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20215914 (20.2 MB)  TX bytes:20215914 (20.2 MB)

```route -n output
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.0.1       0.0.0.0         UG    100    0        0 br0
10.10.0.0       0.0.0.0         255.255.255.0   U     0      0        0 br0
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 br1
```I am able to ping/initiate connections 10.10.1.201 -> 10.10.1.21 and 10.10.0.217 -> 10.10.0.21
BUT what does NOT work is
10.10.1.201 -> 10.10.0.21 or 10.10.0.217 -> 10.10.1.21. (same-subnet connections work, ones requiring routing do not).

When I run a tcpdump on the router (OpenBSD) between this all, I see the requests but not the responses:
Nov 04 15:51:52.161056 rule 1/(match) pass in on em1: 10.10.0.217 > 10.10.1.21: icmp: echo request
(where em1 is the interface connected to 10.10.0.0/24)

On the Ubuntu server itself, the bridged interface sees the Syn packets, but no further response is sent:
root@pinotnoir:~# tcpdump -n -i br1 host 10.10.0.217
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br1, link-type EN10MB (Ethernet), capture size 65535 bytes
15:58:31.549411 IP 10.10.0.217.57965 > 10.10.1.21.22: Flags [S], seq 928841382, win 14600, options [mss 1460,sackOK,TS val 104435609 ecr 0,nop,wscale 7], length 0
15:58:32.548444 IP 10.10.0.217.57965 > 10.10.1.21.22: Flags [S], seq 928841382, win 14600, options [mss 1460,sackOK,TS val 104435859 ecr 0,nop,wscale 7], length 

What am I doing wrong here? I just want to be able to connect/ping across the routed subnet to the 'opposite' interface on the Ubuntu machine.

---

### Post by fwre01 on 2012-11-05
Hi. 

If not already done so, you will need to enable IP forwarding (routing) on your server. This link will show you how:

[http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/]("http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/")

Let us know how you go.

---

