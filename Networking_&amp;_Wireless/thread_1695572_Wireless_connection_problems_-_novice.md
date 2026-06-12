---
title: "Wireless connection problems - novice"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by Tai Chi Pete on 2011-02-26
I am new to Linux and have installed Ubuntu 10.10 onto my Dell Insprion 6000 - Pentium M - 1.73GHz - 50Gb Hard Disk - 2Gb memory. Cable connection is perfect. Updated. Search for driver produces negative result, none installed. Shows Wireless internet turned off. After reading various blogs none of the 'simple' solutions have worked and in response to various suggestions I have produced the following information:
 
[SIZE=1]03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/SIZE]
[SIZE=1]03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)[/SIZE]
[SIZE=1]03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)[/SIZE]
[SIZE=1]03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)[/SIZE]
[SIZE=1]03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)[/SIZE]
[SIZE=1]pete@pete-Inspiron-6000:~$[/SIZE]
 
[SIZE=1]eth0 Link encap:Ethernet HWaddr 00:12:3f:dc:8e:c9 [/SIZE]
[SIZE=1]inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0[/SIZE]
[SIZE=1]inet6 addr: fe80::212:3fff:fedc:8ec9/64 Scope:Link[/SIZE]
[SIZE=1]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/SIZE]
[SIZE=1]RX packets:83 errors:0 dropped:0 overruns:0 frame:0[/SIZE]
[SIZE=1]TX packets:115 errors:0 dropped:0 overruns:0 carrier:0[/SIZE]
[SIZE=1]collisions:0 txqueuelen:1000[/SIZE]
[SIZE=1]RX bytes:25696 (25.6 KB) TX bytes:15915 (15.9 KB)[/SIZE]
[SIZE=1]Interrupt:18[/SIZE]
 
[SIZE=1]lo Link encap:Local Loopback [/SIZE]
[SIZE=1]inet addr:127.0.0.1 Mask:255.0.0.0[/SIZE]
[SIZE=1]inet6 addr: ::1/128 Scope:Host[/SIZE]
[SIZE=1]UP LOOPBACK RUNNING MTU:16436 Metric:1[/SIZE]
[SIZE=1]RX packets:8 errors:0 dropped:0 overruns:0 frame:0[/SIZE]
[SIZE=1]TX packets:8 errors:0 dropped:0 overruns:0 carrier:0[/SIZE]
[SIZE=1]collisions:0 txqueuelen:0[/SIZE]
[SIZE=1]RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)[/SIZE]
 
 
[SIZE=1]pete@pete-Inspiron-6000:~$ iwconfig[/SIZE]
[SIZE=1]lo no wireless extensions.[/SIZE]
 
[SIZE=1]eth0 no wireless extensions.[/SIZE]
 
[SIZE=1]eth1 IEEE 802.11bg ESSID:off/any [/SIZE]
[SIZE=1]Mode:Managed Channel:0 Access Point: Not-Associated [/SIZE]
[SIZE=1]Bit Rate:0 kb/s Tx-Power=off Sensitivity=8/0 [/SIZE]
[SIZE=1]Retry limit:7 RTS thr:off Fragment thr:off[/SIZE]
[SIZE=1]Power Management:off[/SIZE]
[SIZE=1]Link Quality:0 Signal level:0 Noise level:0[/SIZE]
[SIZE=1]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/SIZE]
[SIZE=1]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/SIZE]

[SIZE=1]I am a wireless novice, can anyone help please?[/SIZE]

[SIZE=1]Tai Chi Pete[/SIZE]

---

