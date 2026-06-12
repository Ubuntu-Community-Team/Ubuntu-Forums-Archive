---
title: "Why is my network connections window taking so long?"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by baxna on 2010-06-30
Hi there,

I'm new to Ubuntu, just installed 10.04 Lucid on my Lenovo ThinkPad X61 7674-BS9 today. My question is related to the network connections window and wireless networking. When I start the computer and log in, everything starts up very fast except for this one thing. When the icon finally appears I can open the network connections window but it's like it's frozen there for 5 minutes or so. If I try to close the window (thinking it's hung) it still sits there. Any ideas what could make it behave so slowly?

Here's some output from other commands I saw people running for diagnostics. If there's any other info you'd need to see please let me know.

Thanks in advance for your help!

```
# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1d:72:88:e1:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f8200000-f8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149351 (149.3 KB)  TX bytes:149351 (149.3 KB)

pan0      Link encap:Ethernet  HWaddr 06:6c:58:ce:77:29  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:e1:48:73  
          inet addr:192.168.1.86  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fee1:4873/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1485775 (1.4 MB)  TX bytes:314907 (314.9 KB)
```

And also this:

```
# sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1d:72:88:e1:0a
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:f8200000-f821ffff memory:f8225000-f8225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:e1:48:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.86 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:f7f00000-f7f01fff
```

---

