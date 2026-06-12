---
title: "Laptop can see wireless networks, but can't join any network"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by anil_robo on 2011-03-14
I have a very old laptop I was thinking of installing Ubuntu 10.10 on. The install went smoothly. Everything seems to be working well except the wireless connection. When I click on the wireless icon on the top right, it shows me a list of networks available. I have tried joining open networks, WEP, WPA and WPA2 networks - all of which fail. I know the password is working because I tested it on my macbook sitting alongside the old laptop.

The wireless adapter in question is supposed to work "out of the box" with Ubuntu, still I'm having problems.

Here are the details of the old laptop:

**1.1) Brand:**
Neo (a phillippine-based company)

**1.2) Model number: **[FONT=Arial][COLOR=navy][COLOR=navy][FONT=Arial]
[COLOR=Black] SZS223 (discontinued)[/COLOR]

[/FONT][/COLOR][/COLOR][/FONT]**2 ) Wireless Brand, Model and Wireless Chipset:**
Intel corporation PRO/Wireless 2200BG [Calexico2] (rev 05)

[B]3 ) check interface:
[/B]```
$iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:66  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[B]
4 ) Check for modules:
[/B](pasting selected entries)
```
$lsmod
libipw                 39808  1 ipw2200
cfg80211              144470  2 ipw2200,libipw
lib80211                5058  3 lib80211_crypt_wep,ipw2200,libipw
```[B]5 ) Kernel boot messages

[/B]```
$ dmesg | grep "ipw"
[    7.543983] libipw: 802.11 data/management/control stack, git-1.1.13
[    7.543987] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    8.588907] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    8.588910] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    8.589044] ipw2200 0000:01:07.0: PCI INT A -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[    8.589124] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    9.878635] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
``` [B]6 ) Network configuration

[/B]```
$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:0e:56:e7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:5 memory:ffbff000-ffbfffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:24:2c:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:5 ioport:c800(size=256) memory:ffbfd400-ffbfd4ff
``````
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:6B:2A:32:4E
                    ESSID:"india"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-36 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 11124ms ago
```[B]8 ) Ubuntu Version: 
10.10

[/B][B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
$ uname -mr
2.6.35-22-generic i686
```[B]10 ) Restarting the network:
[/B]$ sudo /etc/init.d/networking restartGives no error messages whatsoever.

---

