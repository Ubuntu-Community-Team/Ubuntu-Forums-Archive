---
title: "Can't see may device in network manger, why ?"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by clausrei on 2012-03-30
I can't see my device in Network Manger, why ? 
The dongle is connected. The blue light is flashing, which means it found a network. The devise is recognized. see lsusb device 002:

```

markus@Ocelot:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 19d2:1007 ONDA Communication S.p.A. 

```And ifconfig is showing this:   
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:7e:f3:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:50:35:3e  
          inet addr:192.168.101.212  Bcast:192.168.101.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe50:353e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13224137 (13.2 MB)  TX bytes:981321 (981.3 KB)
          Interrupt:17 Base address:0x2000 Memory:b0107000-b0107fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Why is it not showing up ?

Thanks for your help

---

