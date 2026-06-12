---
title: "Intermittant wireless"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by johnnytm on 2010-10-08
HI, I am having problems with connecting to the inter-net every time I first start my Ubuntu 10.04 laptop. It's a Dell machine with a Broadcom 4312. I have to enable wireless on every start, but even doing that it will not even try to connect unless I reboot my machine. ```
johnnytm@ubuntu:~$ lspci -nn | grep 'Broadcom'
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
johnnytm@ubuntu:~$ iwconfig eth1
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:208  Noise level:172
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

johnnytm@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:7b:33:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:f1:a1:e0:d6:57  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fee0:d657/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10525 errors:0 dropped:0 overruns:0 frame:4280
          TX packets:11149 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10863620 (10.8 MB)  TX bytes:1719431 (1.7 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33200 (33.2 KB)  TX bytes:33200 (33.2 KB)

johnnytm@ubuntu:~$ sudo lshw -C network
[sudo] password for johnnytm: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:f1:a1:e0:d6:57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: f0:4d:a2:7b:33:fc
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)

```
The wireless connection is set to connect automatically, and I don't know what else to check.

---

### Post by johnnytm on 2010-10-09
No one else every had this problem?:confused:

---

### Post by johnnytm on 2010-10-12
This was not really solved, but is no longer an issue with an update to maverick meerkat.

---

