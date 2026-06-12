---
title: "Ubuntu 13.04 consuming the whole network speed from router"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by krishna147 on 2013-06-22
Hi,

I just recently upgraded to 13.04

We have a four computers at home and we have 15Mbps Network connection which we share using a Netgear Router.
I use ubuntu and the rest of the guys computers are using Windows 7 OS.

When my computer (with ubuntu) is connected all the other windows PCs Network speed is going down drastically low.
We checked the speed of internet using www(dot)speedtest(dot)net
When Ubuntu computer is connected to the Router : Only Ubuntu PC is showing 15Mbps speed and rest all windows PC's are showing speed of around  0.09 Mbps
                                                                      (very low speed) (Tried opening other pages also they are very slow)
When the Ubuntu is not connected to Router : All the 3 Windows PCs are showing 15Mbps on the website and all the pages are o
pening fine in their system

Due to this issue I have to Use Windows 7 instead of Ubuntu Since the network is shared and all the guys are not able to use the internet because of low speed
of internet
I am facing this issue once I upgraded from 12.10 to 13.04 

Please help me in resolving this as i dont want to use windows in place of ubuntu

Thanks in advance for any help

---

### Post by praseodym on 2013-06-22
Hi,

what hardware is in use?
```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by krishna147 on 2013-07-03
I disabled the proprietary driver of broadcomm and now the issue is resolved
Thanks

---

