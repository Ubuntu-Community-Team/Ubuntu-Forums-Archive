---
title: "Won't route from LAN to internet"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by gene02 on 2011-06-07
I just upgraded from lucid to maverick, but my machine, which acts as the router and firewall between my home LAN and the internet, has stopped routing traffic between the two interfaces.

I've had this issue pop up before with OS upgrades, and removing Network-Manager had helped, so I did it again this time, and my network is still borked.

Here is ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:59:a0:88  
          inet addr:<internet ip>  Bcast:<broadcast>  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2407 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2638670 (2.6 MB)  TX bytes:409546 (409.5 KB)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:0a:c9:7e  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63485 (63.4 KB)  TX bytes:128668 (128.6 KB)
          Interrupt:20 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186891 (186.8 KB)  TX bytes:186891 (186.8 KB)

```

and here is route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<inet ip>       0.0.0.0         255.255.255.248 U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
239.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 eth1
0.0.0.0         <inet gw>    0.0.0.0         UG    100    0        0 eth0

```

(external ips censored out of paranoia...)
I don't know where that 239.0.0.0 address is coming from.  I removed it manually:
```
route del -net 239.0.0.0 netmask 255.0.0.0 dev eth1
```

but that didn't help.

I'm hitting my head against the wall now.  Help!

[SOLVED: Solution was to uncomment this line in /etc/sysctl.conf: "net.ipv4.ip_forward=1".  I'm guessing Network-Manager helpfully commented it out]

---

