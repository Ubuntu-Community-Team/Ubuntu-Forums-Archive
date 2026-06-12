---
title: "How to test NIC card"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by ubontik on 2011-02-08
All of a sudden lost the Internet connection on Ubuntu10.04
----------------------------
$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.088 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.067 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.066 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.079 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.067 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.075 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.071 ms
64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.076 ms
$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:0b.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 05)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
$ sudo ufw status
$ ping 192.168.2.0
connect: Network is unreachable
Status: active

Any suggest for newbie.

Thanks

The output of 
$ sudo net -nr 
Kernel IP routing table 
Destination   Gateway  Genmask   Flags MSS Window irtt Iface

The output of 
$ sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056794 (1.0 MB)  TX bytes:1056794 (1.0 MB)
----------------
This is not what I expected. Network device should be (I think) eth0

---

### Post by ubontik on 2011-02-11
Anybody help me ple--a--se.
So, I ran the following commands:
$ dmesg | grep eth
$ /sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:dc:60:a0:8c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:662295 (662.2 KB)  TX bytes:662295 (662.2 KB)

I hope this time I'll get some answers.

Thanks

---

