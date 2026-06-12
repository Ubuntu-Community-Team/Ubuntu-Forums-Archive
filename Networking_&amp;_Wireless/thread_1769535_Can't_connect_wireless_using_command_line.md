---
title: "Can't connect wireless using command line"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by mcknight0219 on 2011-05-28
Hi, forum

Recently I switched to FVWM, so I intend not to use gnome like
network-manager :( However, I can't connect to wireless using command line, the dhclient just won't obtain address. The problem is weird because I can get wireless connection with nm-applet perfectly....

Anybody ran into same problems before ?

---

### Post by chili555 on 2011-05-28
Manual methods are unlikely to work on any system if Network Manager is installed and running, which it almost always is, if it's installed. Is it?```
ps aux | grep -i network
```Can you please show us your commands? Disguise any passwords, please:```
sudo iwconfig wlan0 key xxx
```May we also see:```
cat /etc/network/interfaces
sudo iwlist wlan0 scan
```I assume wlan0 is your wireless interface; substitute eth1 or whatever it is.> The problem is weird because I can get wireless connection with nm-applet perfectly....
Meaning that NM *IS* running? Manual methods will probably never work.

---

