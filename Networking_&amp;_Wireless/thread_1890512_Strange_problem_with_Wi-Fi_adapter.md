---
title: "Strange problem with Wi-Fi adapter"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by papi92 on 2011-12-03
Hello! I have a strange problem with Wi-Fi adapter. When I leave my computer on for a long time (more than 6 hours) Wi-Fi adapter is disconnected from my home network and no longer wants to connect. The only option is to restart the computer. I tried to write in console "wlan0 down" and then "wlan0 up" but nothing happens.

I use the Fujitsu Amilo Pi 3560 with Intel 5100 Wirelles adapter, Ubumtu 10.04.

---

### Post by deonis on 2011-12-03
It is possible a problem with your hardware. you said that you tried restarting it, did you use ifconfig for that ? So try typing ifconfig in terminal find an interface which correspond to you wifi adapter and then try this in terminal:

ifconfig wlan0 down
ifconfig wlan0 up 

hope that helps

---

