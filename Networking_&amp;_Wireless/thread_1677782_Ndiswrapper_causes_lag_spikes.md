---
title: "Ndiswrapper causes lag spikes"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Burky on 2011-01-29
I have my Ubuntu configured with ndiswrapper in order for my card to work. Ndiswrapper works fine, until I play Armagetron Advanced. On this game, I'll constantly get lag spikes which makes the game extremely hard to play. I'm not sure if there is anything I could do about this, but it would be nice if there was a way to fix this...

Information:
```
lsusb
Bus 002 Device 003: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]

```

```
iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"NETGEAR-2.4-G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:AC:6E:67   
          Bit Rate=24 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
  uname -mr
2.6.32-28-generic-pae i686

```

```
lsb_release -d
Description:	Ubuntu 10.04.1 LTS

```

---

