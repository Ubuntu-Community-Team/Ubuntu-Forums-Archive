---
title: "Wireless security mode-wep, wpa, wpa2, etc"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2012-03-03
Router Linksys E1200.

My routers wireless>security mode seems to only offer a choice of WPA2 Personal & WPA2 Enterprise. However the "help" section refers to WEP also. Why can't I find it as an option? The reason I want to use something differant than WPA2 is that although my router offers WPA2, my adapter offers WPA/WPA2 Mixed. Is this compatable or are these 2 different  modes?

Also, my router offers N, B and G mode. But my adapter, even though it is a N adapter, when I tried to set it up under Ubuntu 11.04 live dvd I was only given the options for B and G.

Any thoughts on this?

---

### Post by praseodym on 2012-03-03
Please show

```
lsusb
lsmod
iwconfig
sudo iwlist scan #which NW is yours?
dmesg | grep country
iwlist chan
```
Obviously the adapter should support WPA2. Pure N-mode works (with 300M) only in the 5 GHz range, 150 M (as optimum) in the 2.4 GHz range. Maybe a driver/firmware problem?! We'll see ;-)

---

