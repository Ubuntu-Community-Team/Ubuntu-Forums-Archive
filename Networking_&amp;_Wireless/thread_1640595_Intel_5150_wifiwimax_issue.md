---
title: "Intel 5150 wifi/wimax issue"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by gopyan on 2010-12-08
Hello friends.

I understand, that forum have many topics dedicated this problem, but i think , that my problem unique.

I want to connect my Netbook( with Ubuntu 9.10) and PC (with WinXP) via wireless media. I try to ad-hoc connection.

I have:

Netbook-Intel 5150 wifi/wimax card.
PC- Orinoco Wireless Pc card.

I want to notice (My Netbook have Winxp also) that connection WinXp -> WinXp is good. 

I invoke folowing commands


/etc/init.d/network-manager stop
ifconfig wlan0 down
iwconfig wlan0 mode ad-hoc
iwconfig wlan0 channel 6
iwconfig wlan0 essid 'test'
ifconfig wlan0 up
ifconfig wlan0 10.0.0.20 netmask 255.0.0.0

On my Pc (with WinXp) ip - 10.0.0.11 netmask 255.0.0.0

My Pc see that ad-hoc connection with essid 'test' is exist.
Connection to 'test' from my Pc is OK.

But I can't ping my Pc from Ubuntu Netbook.

What I do wrong????

iwlist wlan0 scan work fine.

Please help my guys.

---

### Post by gopyan on 2010-12-09
Ayyyyyyyyyyyyy

---

