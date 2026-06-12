---
title: "Not recognizing my new router"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by enezx on 2013-05-27
I bought a new router and my ubuntu 12.04 running on dell inspiron 5420 does not recognise it. It recognised my previous router perfectly. It still recognises my mobile's personal hotspot and some other wifi's but not my new one.
Help me!

To add if it helps wired connections do not work on my ubuntu - perhaps driver problem.

Here's some outputs if it helps :-

1) lspci
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
02:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)



```

2) ifconfig
```
eth0      Link encap:Ethernet  HWaddr c0:18:85:c6:49:a1            inet6 addr: fe80::c218:85ff:fec6:49a1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1584 (1.5 KB)  TX bytes:1584 (1.5 KB)



```


Yes I already downloaded the compat wireless 2012-07-03 driver many times. It does not seem to work!

---

