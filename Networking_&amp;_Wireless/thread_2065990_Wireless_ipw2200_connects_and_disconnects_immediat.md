---
title: "Wireless ipw2200 connects and disconnects immediately"
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by bumeshrai on 2012-10-03
I have an old laptop on 12.04. The wireless connection was working fine till two days back, but now it connects and disconnects immediately and then ask for authentication,  and the cycle goes on. I think it happened after an update, though I don't remember what update it was. When I boot with windows partition, the wireless works fine. I had stopped using windows, 2 years back, but now I am forced to use it because of the wireless problem. Please help me.

My system outputs are:

$ uname -a
Linux umesh-TravelMate-4020 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux

$ lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:d6:e8:22
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:b010b000-b010bfff
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 02
       serial: 00:c0:9f:c0:11:4c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.7 latency=32 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:b0106000-b0107fff memory:84000000-8401ffff

$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"\x08p\xD4\xB2\x8A)TH\x9A\x0A\xBC\xD5\x0E\x18\xA8D\xAC[\xF3\x8EL\xD7-\x9B\x09B\xE5\x06\xC43\xAF\xCD"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:80  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:DA:2C:A1:08
                    ESSID:"ceeicf"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-40 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 180ms ago
          Cell 02 - Address: B0:B2:DC:1D:E0:A1
                    ESSID:"ICF"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=23/100  Signal level=-85 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12592ms ago

eth0      Interface doesn't support scanning.

---

### Post by bumeshrai on 2012-10-04
Any help please.

At least a direction to another forum, where I could get a response.

---

### Post by bubbajunk on 2012-10-05
There was a kernel regression bug introduced in the kernel update 3.2.0-29. It affects Intel 2200BG wireless card and the signal strength reported by the network manager applet. I have the same issue as you on my Thinkpad with that card. The applet reports zero signal strength and sometimes no wireless APs at all. The work around for me is to toggle the wireless off/on using "Enable Wireless" in the applet. After doing that I can see the wireless networks. Here's a link to the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1035590](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1035590)

---

### Post by bumeshrai on 2012-10-05
bubbajunk: Thanks for the response. I went through the link. My case seems to be slightly different.

I had no problem till 3.2.0-32. 3.2.0-29 was OK for me. Even now the signal strength is ok. My problem is immediate disconnection after the connection is established. The same is the case even if I go for earlier versions. It seems to be some non-kernel update I may have have permitted, because even 3.2.0-32 was working properly and suddenly one day, when I rebooted the problem happened!!

Now either I have to use wired connection or use ms windows for wireless. Both highly inconvenient options.

---

### Post by steeldriver on 2012-10-05
do you see anything in dmesg that might give you a clue what's happening?

```
dmesg | grep ipw2200
```

---

### Post by bumeshrai on 2012-10-05
$ dmseg | grep ipw2200 output is

[   25.504439] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   25.504444] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   25.554399] ipw2200 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.554432] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.103783] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

---

### Post by steeldriver on 2012-10-05
Hmm... nothing obvious there... but I noticed your iwlist scan shows the signal quality/level is low

```
Quality=23/100  Signal level=-85 dBm
```that doesn't sound good - have you tried other channels?

---

### Post by bumeshrai on 2012-10-05
Changed to wicd. Problem solved. Thanks to all.

---

