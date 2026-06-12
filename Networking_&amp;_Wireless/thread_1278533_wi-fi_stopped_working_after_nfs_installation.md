---
title: "wi-fi stopped working after nfs installation"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by netimen on 2009-09-29
I have managed to connect my desktop (**kubuntu 9.04**, **2.6.28-11-generic** kernel with **D-Link DWA 110** usb Wi-Fi adapter) to a **Acer Timeline 4810G** laptop (**ubuntu 9.04**). All went OK till this morning I installed nfs on both systems. 

Now I can see from the laptop the network created on my desktop (via *iwlist*), but after I try to connect to it (*iwconfig wlan0 essid _my_essid_*) *ping* of my desktop returns
```
From 192.168.1.1 icmp_seq=6 Destination Host Unreachable
```

*dmesg | grep wlan* returns now
```
[ 3502.027059] wlan0: Trigger new scan to find an IBSS to join
[ 3504.968034] wlan0: Trigger new scan to find an IBSS to join
[ 3507.872033] wlan0: Trigger new scan to find an IBSS to join
[ 3510.668039] wlan0: Trigger new scan to find an IBSS to join
[ 3511.473337] wlan0: Creating new IBSS network, BSSID f2:96:e6:84:c6:2d
[ 3512.676031] wlan0: no IPv6 routers present
[ 3541.488046] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3572.312129] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3603.124035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3603.969610] wlan0: Selected IBSS BSSID 8a:9f:71:7a:97:51 based on configured SSID
```
on the desktop and something similar on the laptop.

There weren't such messages before nfs installation, though I'm not sure that installation caused the problem. What does ```
wlan0: no IPv6 routers present
``` mean?

How do I connect? I don't use network managers, I connect manually, using the following procedure on the desktop and a similar one on the laptop:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 1
sudo iwconfig wlan0 key off
sudo ifconfig wlan0 up
sudo ifconfig wlan0 192.168.1.1
sudo iwconfig wlan0 essid '2111'

```

---

### Post by x22 on 2009-10-01
for what it's worth, here's what I use--

ifconfig wlan0 up
iwconfig wlan0 essid ...
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key ...
iwconfig wlan0 key open
dhclient wlan0

---

