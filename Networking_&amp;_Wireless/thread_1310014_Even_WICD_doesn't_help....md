---
title: "Even WICD doesn't help..."
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by pricedout on 2009-11-01
9.04 version... Tried to install WICD to sort out my wireless connection but get 

Error: Conflicts with the installed package 'network manager'

I have downloaded an up to date driver for my wirelss card but am seriously out of my depth in sorting this out...

why won't it connect to the SSID it can see? The password is correct but still no connection

---

### Post by kevdog on 2009-11-01
You need to give us more info on your wireless card and system.

lspci -nnm
lshw -C network
ifconfig


This information is a good starting point.

---

