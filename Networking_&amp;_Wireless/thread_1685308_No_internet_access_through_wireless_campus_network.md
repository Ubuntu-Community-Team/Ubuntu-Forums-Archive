---
title: "No internet access through wireless campus network?"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by LanguidLegend on 2011-02-10
I am trying to connect to the college campus wifi network, but  having difficulties in Linux.
I am dual-booting Windows 7 and Ubuntu 10.10, and I use Google Chrome web browser on both. When I boot into Windows, my laptop connects to the network (as I can see from the taskbar icon) and I can (and currently am) connect in Chrome.
However, in Ubuntu, it connects (or so the icon indicates) but Chrome doesn't load any pages.

The campus network is unsecured, but once you open the browser, you are prompted with a log-in page (student ID and password) to actually connect.

Here is my output for iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:"sjsu_campus"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:6C:BC:D3:E0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by lukeiamyourfather on 2011-02-10
If you're actually connected and have an IP address then the issue might be the browser. Try Firefox to see if you get the login prompt page.

---

