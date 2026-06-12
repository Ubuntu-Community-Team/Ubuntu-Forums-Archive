---
title: "Wireless No Longer Connects"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by romleinster on 2013-01-28
I'm running Ubuntu 12.04 on an ASUS eee PC netbook. Wireless has worked fine since install (almost two years ago). Yesterday I can't connect to my home network. I didn't change any settings or upgrade/install anything out of the ordinary (I believe I did do a system upgrade recently though, just the typical apt-get update/apt-get upgrade). Other machines in my house are connecting fine, other OS's on the same box can connect fine, and in Ubuntu I can make connections to other networks.

I've confirmed the saved password for the wireless is correct. I've tried disabling/re-enabling wireless on the computer, and I've tried resetting the wireless router.

Any ideas on how to get Ubuntu to connect to my network?

here's my wireless driver info:

Network Controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

my wireless's ifconfig:
eth1
Link encap:Ethernet HWaddr 48:5d:60:55:41:62
inet addr:192.168.33.101 Bcast:192.168.33.255 Mask:255.255.255.0
inet6 addr: fe90::4a5d:60ff:fe55:4162/64 Scope:Kink
UP BROADCASE RUNNING MULTICAST MTU:1500 Metric: 1
RX packets: 158 errors: 0 dropped:0 overruns:0 carrier:0
TX packets:395 errors:65 dropped:0 oveerrun:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:59491 (59.4 KB) TX bytes:60787 (60.7 KB)
Interrupt:17 Base address:0xc000

and iwconfig:
eth1
IEEE 802.11abg ESSID:off/any
Mode:Managed Access Point: Not-Associated
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management: on

and my router's wireless settings:
Access Point:        00:1b:5b:4c:64:a1
Channel:               1 (2412 MHz)
Authentication:     WPA-PSK and WPA2-PSK 
Encryption:           TKIP

---

