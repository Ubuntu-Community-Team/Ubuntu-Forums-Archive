---
title: "wireless misconfiguration again....FFFFFUUUUUUU"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by cespinal on 2010-06-19
after having some trouble last week with my wireless...no I am facing some more complicated ones to my extent.

for some reason, the kernel is loading my wireless card as eth1 and knetworkmanager seeks for such name, but lshw -c network shows two connections: eth0 and eth2... after trying some stuff I got the wireless led to turn blue, meaning that the kernel loaded it although knetworkmanager could not detect it. Now the led is back at orange and I cant for the hell of me solve this thing. 

here are the outputs for the common commands used in this case 
```
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:2c:50:e6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:20 memory:f2588000-f2588fff ioport:30f8(size=8) memory:f2589c00-f2589cff memory:f2589800-f258980f
  *-network DISABLED
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 03
       serial: 00:1a:73:fc:5f:74
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f2200000-f2203fff memory:f2000000-f20fffff(prefetchable)
yeto@yeto-laptop:~$          yeto@yeto-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0  
          inet6 addr: ::1/128 Scope:Host       
          UP LOOPBACK RUNNING  MTU:16436  Metric:1                                            
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7744 (7.7 KB)  TX bytes:7744 (7.7 KB)

```

and

```
:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0  
          inet6 addr: ::1/128 Scope:Host       
          UP LOOPBACK RUNNING  MTU:16436  Metric:1                                            
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7744 (7.7 KB)  TX bytes:7744 (7.7 KB)

yeto@yeto-laptop:~$ [   28.163231] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
bash: [: missing `]'

knetworkmanager(1509) KNetworkManagerTrayIcon::KNetworkManagerTrayIcon: connecting "eth0" 's signals
knetworkmanager(1509) KNetworkManagerTrayIcon::KNetworkManagerTrayIcon: connecting "eth2" 's signals
knetworkmanager(1509) KNetworkManagerTrayIcon::updateInterfaceToDisplay:
knetworkmanager(1509) KNetworkManagerTrayIcon::updateInterfaceToDisplay: interfaces considered:
knetworkmanager(1509) KNetworkManagerTrayIcon::updateInterfaceToDisplay: Solid::Control::WiredNetworkInterface(0x99f94d8) 1 1
knetworkmanager(1509) KNetworkManagerTrayIcon::updateInterfaceToDisplay: Solid::Control::WirelessNetworkInterface(0x99faf20) 2 1
knetworkmanager(1509) KNetworkManagerTrayIcon::updateInterfaceToDisplay: interface to display: Solid::Control::WiredNetworkInterface(0x
99f94d8)

```

would any kind, enlightened guru help me untangle all this spaghetti?
thanks

---

### Post by cespinal on 2010-06-19
okay this is wierd as f.......
suspended the system to ram to go bed... woke up for a moment, turned of the computer... everything works now.... what is this?

---

