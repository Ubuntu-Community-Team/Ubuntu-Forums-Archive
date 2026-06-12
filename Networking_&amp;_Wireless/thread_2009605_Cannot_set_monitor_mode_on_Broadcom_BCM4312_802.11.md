---
title: "Cannot set monitor mode on Broadcom BCM4312 802.11b/g LP-PHY"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by tylerthemiler on 2012-06-24
Hello all,

I am trying to set my wireless card into monitor mode. I am working with:

```
description: Wireless interface
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
logical name: eth2
```When I try to set it to monitor mode I get:

```
sudo iwconfig eth2 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.
```
I also tried using:

```
$ sudo airmon-ng start eth2


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
1094    NetworkManager
1096    avahi-daemon
1097    avahi-daemon
1167    wpa_supplicant
1720    dhclient
Process with PID 1720 (dhclient) is running on interface eth2


Interface    Chipset        Driver

eth2        Unknown         wl (monitor mode enabled)

$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11bg  ESSID:"Redacted"  
          Mode:Managed  Frequency:2.437 GHz  
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=4/5  Signal level=-59 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:0   Missed beacon:0
```I've gone through various driver tutorials, but nothing is helping. Anyone know how to get this working for this specific wireless card?

---

