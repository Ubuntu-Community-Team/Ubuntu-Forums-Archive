---
title: "Can see wifi connection but can't connect, need help. Beginner to Ubuntu."
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by polaskaroid on 2013-07-12
This is my first time using Ubuntu Linux so I have no idea what I'm doing.

I just installed Ubuntu Linux 12.04 on my Macbook White. Everything was fine till the installation screen where it said I need to connect to wifi. 

When I checked all of the usual wifi that I see everyday was there including mine but it's greyed out. I can't click on it or do anything but the other wifi (which I don't have access to) works normally and request a password.

Currently I'm using a wired connection and was able to finish my installation. Anyone got any suggestion ?

---

### Post by polaskaroid on 2013-07-12
NVM, I found a fix.

Aparantly my Ubuntu can't connect to WPA2 wifi, simply changing to WPA fixed it.

---

### Post by praseodym on 2013-07-12
Thats very unusual. Please show the hardware and driver specs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```

---

