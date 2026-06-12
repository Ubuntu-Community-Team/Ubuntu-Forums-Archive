---
title: "WLan Traffic Limited to 64 kbit/s"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by Skeeve245 on 2010-02-27
Hi,
after the last update to KUbuntu 9.10 my WLan Interface is absolutely slow. Using Windows with my Notebook I still have download rates of 640 kbit/s and above as I had on my linux machine before.

lsusb shows: 
Bus 001 Device 006: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi

and lsmod shows:
root@Aahz:/# lsmod | grep rt
rt2500usb              21152  0
rt2x00usb              11548  1 rt2500usb
rt2x00lib              29756  2 rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211

Anybody any idea?

Thanks


Stefan

---

