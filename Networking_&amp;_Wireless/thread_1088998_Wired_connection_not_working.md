---
title: "Wired connection not working"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by njk123 on 2009-03-06
My ethernet card is not working at all since 4 days. Tried everything but no help. Here is what happens.

1) When I turn on windows(on desktop) should network connected (linux)
2) When I give both machines the same address, windows shows an error for ipconflict.
3) Ping is also not possible from both the machines.
4) This  is the ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:c9:01:63:df  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe01:63df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:19731 (19.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:721026 (721.0 KB)  TX bytes:721026 (721.0 KB)

---

### Post by Iowan on 2009-03-06
These are two different machines?
If they are separate machines, they must NOT have the same IP address... although the addresses must be in the same subnet.
What is IP address of Windows machine? 
Is (Are) address(es) via DHCP server (router or modem) or are they manually set (static)?

---

