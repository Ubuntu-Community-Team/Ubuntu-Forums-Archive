---
title: "Alacritech Quad Port 10/100 Server Accelerator"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by mbeierl on 2011-01-17
I've got one of these in my Ubuntu 10.10 system, lswh -c network shows:
```

   *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:dfae0000-dfae7fff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 2.1
       bus info: pci@0000:04:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:dfae8000-dfaeffff
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 2.2
       bus info: pci@0000:04:02.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:dfaf0000-dfaf7fff
  *-network:4 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 2.3
       bus info: pci@0000:04:02.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:dfaf8000-dfafffff

```

But nothing I can figure out allows me to use or allocate any eth devices to these unused ports.

How do I use them?

---

### Post by cyberndj on 2012-04-08
Hi, I also have one of these cards in my system as well. Running Ubuntu Server 11.10 and its up to date. I'm not worried about the  "acceleration" features, but I would like to know where to go to get the regular networking functions working.

Here are some output of commands that I've read elsewhere that have been asked for.

-Jake

sudo lshw -C network
```
cyberndj@ubuntu:~$ sudo lshw -C network
[sudo] password for cyberndj:
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 1
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fcf18000-fcf1ffff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 6.1
       bus info: pci@0000:01:06.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fcf10000-fcf17fff
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 6.2
       bus info: pci@0000:01:06.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fcf08000-fcf0ffff
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: Quad Port 10/100 Server Accelerator
       vendor: Alacritech Inc
       physical id: 6.3
       bus info: pci@0000:01:06.3
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fcf00000-fcf07fff
```


sudo lspci -nn | grep 01:06.0
```
cyberndj@ubuntu:~$ sudo lspci -nn | grep 01:06.0
01:06.0 Ethernet controller [0200]: Alacritech Inc Quad Port 10/100 Server Accelerator [139a:0001] (rev 01)
```

ifconfig -a```
cyberndj@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:5a:9b:b4:8c
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:24

eth1      Link encap:Ethernet  HWaddr 00:00:5a:9b:b4:8d
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:24

eth2      Link encap:Ethernet  HWaddr 00:00:5a:9a:8b:1c
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20

eth3      Link encap:Ethernet  HWaddr 00:00:5a:9a:8b:1d
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20

eth4      Link encap:Ethernet  HWaddr 00:06:5b:f3:dd:60
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28

eth5      Link encap:Ethernet  HWaddr 00:06:5b:f3:dd:61
          inet6 addr: fe80::206:5bff:fef3:dd61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1052 errors:0 dropped:39 overruns:0 frame:0
          TX packets:1875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:92035 (92.0 KB)  TX bytes:233496 (233.4 KB)
          Interrupt:29

eth5.2    Link encap:Ethernet  HWaddr 00:06:5b:f3:dd:61
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fef3:dd61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:67915 (67.9 KB)  TX bytes:217486 (217.4 KB)

eth5.4    Link encap:Ethernet  HWaddr 00:06:5b:f3:dd:61
          inet6 addr: fe80::206:5bff:fef3:dd61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:4 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:344 (344.0 B)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:45663349 (45.6 MB)  TX bytes:45663349 (45.6 MB)
```

---

