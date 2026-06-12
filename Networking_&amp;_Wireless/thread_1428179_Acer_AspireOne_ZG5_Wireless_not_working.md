---
title: "Acer AspireOne ZG5 Wireless not working"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by pabut on 2010-03-12
Hi all .... I've tried to solve this on my own but I'm at the banging my head on the table stage .... so I appeal to those wiser than I ... any guidance would be appreciated! 

[new information 2010/03/13: I set up a spare wireless AP and turned off WEP seems to work ... using it as I type this. I consider this a workaround and not a solution. I'm not comfortable having an open AP on my network.]

Netbook is an AcerAspire One ZG5 (AOA150-1555) .... can't get wireless to work .... it seems to be trying but can't associate with my access point .... it works fine when I boot the other operating system which shall not be named ....  

Sticker on the bottom says it's an Atheros AR5BXB63

Loaded Ubunto\u 9.10 NBR with the most recent updates (as of the date of this post)
Added based on some posts I read:
linux-backports-modules-karmic-generic (2.6.31.20.33) ...
linux-backports-modules-karmic (2.6.31.20.33) ...


Vital data

lspci -nn:
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

ifconfig 
wlan0     Link encap:Ethernet  HWaddr 00:24:2c:05:da:60
          inet6 addr: fe80::224:2cff:fe05:da60/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:880 (880.0 B)  TX bytes:4737 (4.7 KB)

root@netbook:~# iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"XXXXXXXX"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX
          Power Management:off

(ESSID and key altered to protect the innocent)

 Relevant loaded modules:
root@netbook:~# lsmod | grep ath5k
ath5k                 122244  0
mac80211              210508  1 ath5k
ath                     8444  1 ath5k
cfg80211              130632  3 ath5k,mac80211,ath
led_class               4096  2 ath5k,sdhci

lshw:
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:05:da:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:55200000-5520ffff

head of modinfo:
root@netbook:~# modinfo ath5k
filename:       /lib/modules/2.6.31-20-generic/updates/cw/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby



iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:22:6B:72:32:1F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm
                    Encryption key:on
                    ESSID:"ec0ntact"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f218fe6f56
                    Extra: Last beacon: 596ms ago
                    IE: Unknown: 00086563306E74616374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

root@netbook:~# lsb_release -d
Description:    Ubuntu 9.10

uname -mr
2.6.31-20-generic i686

Interesting lines from dmesg:

[   19.202777] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.202823] ath5k 0000:03:00.0: setting latency timer to 64
[   19.202911] ath5k 0000:03:00.0: registered as 'phy0'
[   19.746051] ath: EEPROM regdomain: 0x65
[   19.746061] ath: EEPROM indicates we should expect a direct regpair map
[   19.746072] ath: Country alpha2 being used: 00
[   19.746078] ath: Regpair used: 0x65
[   19.950292] Registered led device: ath5k-phy0::rx
[   19.950363] Registered led device: ath5k-phy0::tx
[   19.950374] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
.
.
.
[   35.664344] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.611570] wlan0: deauthenticating from 00:22:6b:72:32:1f by local choice (reason=3)
[   43.611840] wlan0: direct probe to AP 00:22:6b:72:32:1f (try 1)
[   43.614448] wlan0: direct probe responded
[   43.614461] wlan0: authenticate with AP 00:22:6b:72:32:1f (try 1)
[   54.952702] wlan0: direct probe to AP 00:22:6b:72:32:1f (try 1)
[   54.954704] wlan0: direct probe responded
[   54.954718] wlan0: authenticate with AP 00:22:6b:72:32:1f (try 1)
[   66.286600] wlan0: direct probe to AP 00:22:6b:72:32:1f (try 1)
[   66.288607] wlan0: direct probe responded
(repeats several times .....)

---

