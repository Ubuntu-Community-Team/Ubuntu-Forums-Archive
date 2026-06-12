---
title: "[Debian] Getting WiFi card working with a .ko module? (Device not ready)"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by abtekk on 2012-04-23
I'm porting Debian to my Android slate (Zenithink ZT-280 C91) and due to the fact Ubuntu is based on Debian, I thought it would be OK posting this here.

I need to get the wifi working, I placed the wlan.ko module taken from the Android file system and placed it in /lib/modules/2.6.34

I then ran (as root) "insmod /lib/modules/2.6.34/wlan.ko" and Debian picked up the wifi card, but the network manager says "Device not ready".

---

