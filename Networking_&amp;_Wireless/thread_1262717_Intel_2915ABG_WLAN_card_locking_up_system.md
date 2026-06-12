---
title: "Intel 2915ABG WLAN card locking up system"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by BinaryMn on 2009-09-10
Hi, I have an Averatec 3200 series laptop running Ubuntu 9.04. The wireless card that came with it was a buggy Ralink card, so I took it out and put in an Intel PRO/Wireless 2915ABG [Calexico2] card that I had laying around.

I've come to the conclusion that it's the WLAN card that keeps locking up my laptop. The laptop will run for hours as long as I keep the WLAN card turned off. If I turn it on, it'll completely lock up sometime between five and fifteen minutes afterwards.

I've rebuilt the ieee80211 subsystem and recompiled the driver using the instructions at [http://ubuntuforums.org/showpost.php?p=6688433](http://ubuntuforums.org/showpost.php?p=6688433) in an attempt to try fixing this problem. Unfortunately, it hasn't made any difference.

I've gone through /var/log, trying to find an error message of some sort that might shed some light on this, but I haven't found anything.

Obviously, I'm not making this post on the laptop in question. As soon as I make this post, I'm going to try getting on the laptop I'm having problems with and try posting lspci and lshw outputs before it locks up on me.

P.S. I can't do anything when it locks up. I can't Ctrl + Alt + F# into a console session. I can't REISUB. I can't Ctrl + Alt + Backspace. I cannot do ANYTHING when it locks up on me.

---

### Post by BinaryMn on 2009-09-10
```
chris@linuxbox:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
```


```
chris@linuxbox:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:76:f9:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2 firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.2.10 latency=32 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:19:c0:b4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:9d:14:03:74:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

