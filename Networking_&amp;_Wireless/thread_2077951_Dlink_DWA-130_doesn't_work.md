---
title: "Dlink DWA-130 doesn't work"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by moppag on 2012-10-29
Hi, I tried to install my dwa-130c usb wireless card on ubuntu server 12.10 64 bits But it doesn't work. 

When I run iwconfig I get:

wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


When I run sudo lshw -C network, I get:

*-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:9
       logical name: wlan0
       serial: 00:22:b0:ee:ca:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xU multicast=yes wireless=802.11b/g/n

---

