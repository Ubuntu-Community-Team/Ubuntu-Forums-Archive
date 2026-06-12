---
title: "Intel Wireless 4965AGN - 11.04"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by xur17 on 2011-10-24
I have the Intel Wireless 4965AGN card running on a Thinkpad T61 with ubuntu 11.04, and have been having issues getting my laptop to connect and stay connected to the university wireless.  It connects perfectly fine to my home wifi, but when I attempt to connect to the university wireless it takes several minutes to connect, and constantly connects / disconnects (and will stay disconnected for several minutes).

I notice the issue the most when there are a lot of other laptops connected to the wifi (and then I can't connect at all), but the issue still persists no matter what.

My friends' laptops (same chip in windows), and my phone connect and stay connected fine.

Any recommendations, or is there a good way to upgrade to a newer release of the intel driver to try it out?  I have been using ubuntu for several years, and this new issue is really starting to drive me away from it.

---

### Post by varunendra on 2011-10-27
Please post outputs of:
```
sudo lshw -C network
```Following ones when you are connected to your university network:
```
ifconfig
iwconfig
```and following one when you get disconnected
```
dmesg | grep -iE "wlan|net"
```(please note it is 'piping symbol between dmesg and grep, and between "wlan" and "net", not a small 'L'. Best to just copy-paste if not sure.)

---

