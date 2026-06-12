---
title: "ad-hoc network and RSSI value"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by sgrest on 2010-08-03
Hi,

I'm trying to connect two laptops using wireless (without AP using ad-hoc mode) and upon connection get the RSSI value from each the network card. The two laptops have different wireless cards (Intel PRO/Wireless 4965 AGN and Intel PRO/Wireless 2200BG). Ubuntu 10.04 is running on both laptops. I'm using ioctl() call to get the RSSI value.
  
Problem:

When the laptops are connected and I want to get the RSSI value, the ioctl() call, on the laptop with Intel PRO/Wireless 4965 AGN card, gives "SIOCGIWSTAT on wlan0 : operation not supported" error. However the program works fine on the other laptop! I wonder if anybody knows what is the problem with this configuration. I searched a lot on Google but I couldn't fix it :(.

Thanks

---

### Post by sgrest on 2010-08-04
Hi,

Is the way that I explain the problem confusing? If it is, I can explain it with more details. I'm  stuck in this problem, can anybody help? 

Thanks

---

### Post by Bladerunner_1989 on 2011-09-11
Hi, 
I have similar problem (I see RSSI values in AP mode, but not in Ad-hoc, however using sniffer I made sure that beacons are transmitted in both directions). But for me it just doesn't work at all. My chipset is Atheros 5k. It shows the same message. I guess some cards just don't support RSSI value reporting in ad-hoc mode. If noone points anything I will proceed with libpcap - it is much more flexible solution. Or does anyone know anything better?
Cheers,
Dima.

---

### Post by Bladerunner_1989 on 2011-09-15
btw, i succeeded with libpcap - it is really flexible solution.
Cheers,
Dima.

---

