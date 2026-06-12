---
title: "NetworkManager, Auto eth0 &quot;Never&quot; but it's connected?"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by VipX1 on 2009-08-24
I've had this before on new installs. Today I'm trying to call a router that is on a different subnet to the rest of my network. I've put my Ubuntu laptop on the same subnet, I think. My Auto eth0 connection in the Desktop setup GUI says Never for connected yet when I restart NetworkManager eth0 disconnects and reconnects. I have set eth0 to Manual (DHCP off) and added ip, mask and gate but is it working because eth0 says Never for conected?
Here is the output from route -A inet:```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0          *               255.255.255.0   U     1           0        0 eth0
link-local                *               255.255.0.0       U     1000     0        0 eth0
default            192.168.0.1     0.0.0.0               UG   0           0        0 eth0

```
```
eth0      Link encap:Ethernet  HWaddr **.**.**.**.**.**  
inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
inet6 addr: fe80::21d:9ff:fe47:ddc9/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:1998 errors:0 dropped:0 overruns:0 frame:0
TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0         
collisions:0 txqueuelen:1000          
RX bytes:892454 (892.4 KB)  TX bytes:177694 (177.6 KB)       
Interrupt:17

```/network/interface file has auto lo, iface lo inet loopback as only entery.

---

### Post by Iowan on 2009-08-24
Is this a new install? "Never" refers to the last time the connection (Auto Eth0) was used.

---

