---
title: "I can't get a wireless connection"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by fxmisticat on 2009-03-04
I am brand new to ubuntu. I installed Ununtu 8.1 - the Intrepid lbex 

when i run iwconfig i get:
```

lo     no wireless extensions.

eth0   no wireless extensions.

wlan0  IEEE 802.11bg  ESSID:""
       Mode:Managed  Frequency:2.412 GHz Access Point: NotAssociated
       Tx-Poer=0 dBm
       Retry min limit:7    RTS thr:off    Fragment thr=2352 B
       Link Quality:0  Signal level:0  Noise level:0
       Rx invalid nwid:0  Rx Invalid misc:0   Missed beacon:0

pan0   no wirelss extensions.

```

does this mean it found my card as wlan0?

system->preferences->Network Connections does not show that device listed in the Wireless tab.

can someone please assist me? Thanks ahead of time!!

---

### Post by Crafty Kisses on 2009-03-04
We need more information on the situation. Please post the results of the following commands:
```
sudo lshw -C network
lspci
```

---

