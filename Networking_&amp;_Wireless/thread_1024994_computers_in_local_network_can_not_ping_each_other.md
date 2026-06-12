---
title: "computers in local network can not ping each other"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by jocsch on 2008-12-29
I have a notebook and a netbook, both are connected via wifi to a fritzbox router. Both are in the same subnet and both can connect to the internet (via the fritzbox). However I can not ping or connect via ssh from one machine to the other.
Route displays the following information

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.178.0   0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth1

```

192.167.178.1 is my router. The ip adress of my notebook is currently

```
eth1      Link encap:Ethernet  HWaddr 00:23:4d:5c:6b:59
          inet addr:192.168.178.27  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe5c:6b59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101924 errors:0 dropped:0 overruns:0 frame:12004
          TX packets:81760 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:110126371 (110.1 MB)  TX bytes:11808160 (11.8 MB)
          Interrupt:17 Base address:0xc000
```

The netbook has the 192.168.178.28
Any ideas what's going wrong?

Thanks,
 Markus

---

