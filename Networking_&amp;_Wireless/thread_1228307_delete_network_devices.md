---
title: "delete network devices"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by redshift88 on 2009-07-31
I installed Windows XP as a virtual machine in VirtualBox and I was trying to set it up to get networking working in windows so it can connect to the internet.

Anyways, after a few hours, I gave up, leaving a few new network devices and bridges behind that I would like to remove so I can try again with a clean slate.

I would like to remove:

_wmaster0_

ifconfig wmaster0
wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-7E-BC-34-E0-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

_virbr0_

ifconfig virbr0
virbr0    Link encap:Ethernet  HWaddr 9a:ea:96:e4:a2:d3  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::98ea:96ff:fee4:a2d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:4259 (4.2 KB)

_pan0_

ifconfig pan0
pan0      Link encap:Ethernet  HWaddr c2:63:37:4b:3b:05  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



I'm guessing I just have to edit a few files, but am not sure which one to open.  Any help would be appreciated.

---

