---
title: "Ubuntu Newbie can't get NetGear wireless card to work"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by DALS5 on 2011-03-14
System: HP Vectra VL
Ubuntu Version: 8.10,

lsusb
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub,

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.,

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:da:08:9f:78  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe08:9f78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6737730 (6.7 MB)  TX bytes:702052 (702.0 KB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16980 (16.9 KB)  TX bytes:16980 (16.9 KB)

pan0      Link encap:Ethernet  HWaddr 86:78:84:ca:a4:ea  
          inet6 addr: fe80::8478:84ff:feca:a4ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B),


Note: wlan0: is not present,

Note: Any help you can provide would be greatly appreciated. Thanks in advance!

---

### Post by walt.smith1960 on 2011-03-15
According to the ID, it's a Netgear WNA3100 using a Broadcom BCM43231KBFG chip.  You might take a look at the sticky at the beginning of the forum re Broadcom 43xx card problem.  It might be more complicated using 8.10;  newer releases (kernels) have better support for recent wifi devices.

---

### Post by DALS5 on 2011-03-15
Tried following the directions noted in the sticky at the beginning of the forum re Broadcom 43xx card problem; however, I must've done something wrong. ifconfig output has changed to:
fermin@alison-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:da:08:9f:78  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8763 (8.7 KB)  TX bytes:3793 (3.7 KB)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4092 (4.0 KB)  TX bytes:4092 (4.0 KB)

---

### Post by walt.smith1960 on 2011-03-16
Are you able to connect to a wired internet connection?  I used a Linksys PCMCIA adapter with a Broadcom chip some time ago.  When I got an internet connection and clicked on additional drivers, I was presented a chance to enable the Broadcom adapter.  I did so and was up & running.  Apparently there are a number of Broadcom driver packages available.  The correct package depends on which Broadcom chip you have.

---

