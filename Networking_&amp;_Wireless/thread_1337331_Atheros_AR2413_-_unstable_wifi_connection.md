---
title: "Atheros AR2413 - unstable wifi connection"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by jw1949 on 2009-11-25
Installed 9.10 on a Tosh A100 Satellite laptop with a dual boot to WinXP and, so far I am very pleased to have almost everything that I was running on XP working nicely on Ubuntu - notably OpenOffice (for Word + Excel), Picasa, GnuCash (for Quicken), Amarok and VLC.  I have also installed Chrome - I prefer it to Firefox 'cos it seems much faster, however,  at the moment I am having some problems keeping the wifi connection stable - I do not think it is Chrome as I have similar issues with Firefox.

When I click on a link the timer rolls and rolls with no result.  The wireless icon in the panel says the wireless connection is active, varying between 40 and 65%.   connection immediately.  

When I try to access pages on Chrome, I am getting Error 101, error 324 intermittently.  It seems to be OK for 2 or 3 page accesses then just blocks up on me and reports these errors.

Firefox is no better, eg a google search on fool discussion boards delivered results but when I try to go to one of the links I get nothing - on the panel Network monitor shows a spike and then the accesses disappear.

I am complete newbie - any ideas ?

I have installed the linux-backports modules and restarted - seems no better !


The output from is
__________________________________
*-network:0
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wmaster0
       version: 01
       serial: 00:11:f5:e9:eb:22
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.4 latency=168 maxlatency=28 mingnt=10 multicast=yes 

wireless=IEEE 802.11bg
       resources: irq:20 memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:2f:f7:b6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no 

maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:a000(size=256) memory:c0215000-c02150ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
__________________________________________________________________________________

The output from ifconfig is 
________________________________________
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:2f:f7:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:f5:e9:eb:22  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fee9:eb22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8576402 (8.5 MB)  TX bytes:2034691 (2.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-F5-E9-EB-22-65-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
_____________________________________________________________

---

### Post by Sleig on 2009-12-01
Hi. Any fix? I seem at have the same problem

---

### Post by Open4D on 2010-07-18
> **Sleig said:**
> Hi. Any fix? I seem at have the same problem
Yes.  Bug 568090's description includes a workaround - adding one line to file [FONT=Courier New]/etc/modprobe.d/custom-wireless.conf[/FONT]   (and creating the file if it doesn't already exist).

 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090)

---

### Post by yelvington on 2011-02-15
++ this thread.

It has (knock on wood) saved me from ordering a usb wifi adaptor for my elderly mother's Toshiba. It's been running Ubuntu for years but recently stopped networking, so I upgraded it to Maverick only to run into this weird intermittent whitescreen problem with Web pages. No errors appeared in the system logs. I narrowed it down to the laptop (my devices all work fine on the network) and managed to find this thread through Google -- but it took dozens of attempts to get this site to render.

I installed both the cited fixes, and all seems well at this point (knock on wood again).

---

