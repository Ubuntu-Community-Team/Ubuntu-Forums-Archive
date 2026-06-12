---
title: "Enabling Dell Broadcom Wireless Internet"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by strujillo.jr on 2009-01-15
Hey everyone! SO i go the little WiFi light to light up so i know ubuntu detects the wifi thing...but how do i enable the wireless to connect to a network. I run 8.10 and when i right click on the Network manager and click edit connection i add my wireless LinkSys router and nothing appears in the network manager thingy... And it shows that wireless is disabled...how do i enable it...its getting confusing but im happy i got the wifi light on that makes me happy! lol

```
iwconfig
```
It produces this
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

