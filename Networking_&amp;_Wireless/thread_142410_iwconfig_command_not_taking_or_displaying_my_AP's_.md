---
title: "iwconfig command not taking or displaying my AP's MAC"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by scubacuda on 2006-03-10
This is odd.

I install 5.10 on my Sony with the Netgear MA401 PCMCIA 802.11b card, and it *almost* works correctly.

During the install (apci=off), I selected the wireless card as my default network connection. After the install, I booted into gnome, and opened up a terminal to config my 802.11 card.

Whenever I run **iwconfig**, I see my card. **lshw** correctly shows it as a Negear also. However, when I push parameters into iwconfig (e.g. iwconfig eth0 essid mySSID) and then run a iwconfig to check them out, it has a MAC address of a neighbor.

So, after bootup, I type something like this.```
sudo ifconfig eth1 up
iwconfig

(outputs my neighbor's network -- his MAC address and his SSID)

sudo iwconfig eth1 essid mySSID
iwconfig 

(outputs my SSID with neighbor's MAC address)

sudo iwconfig eth1 ap 00:09:5b:ed:73:6b # just like man iwconfig says

(and I get the following error)
Error for wireless request "Set AP Address" (8B14):
     SET failed on device eth1; Operation not supported
```

Any ideas why this is the case?

---

