---
title: "DWL-650+ problem"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by buttari on 2006-01-20
Hi,
I'm new to (K)Ubuntu. I heired an old Thinkpad from my brother and I'm trying to make it connected to my wireless access point through a DWL-650+ wireless card. When I plug-in the card, it is recognized and related modules are loaded. Then I
```

ifconfig wlan0 up
iwconfig wlan0 essid any

```

but 
```

iwlist s

```
says "no scan results". Then I take a look inside /proc/driver/acx_wlan0 and there is written
```

staus: STOPPED

```
If I start the KDE control center and go to Network it says that interface wlan0 is disabled but when I try to enable it, it says that there was an error and that I should do it manually. 
Can anybody help me with this problem?
Thanks a lot

PS
the wireless card works perfectly on another machine with Gentoo installed.

---

