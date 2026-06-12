---
title: "Ubuntu 12.04 Wifi Driver problems"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by metabolicjosh on 2013-04-28
I have a new computer. My motherboard is here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157331](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157331)

My computer does not even recognize the lan card that I have. Why am i not able to fix this? And do you guys know what to do?

---

### Post by DarkAii on 2013-04-28
Hi there, I am new as well, and I would like you to give out more information about your machine regarding your wireless device, besides the Motherboard alone that dosen't seem to have an intergreted ...wireless device.

For that, would it be possible for you to open the **TERMINAL** application, then copy-past these instructions in order to help the moderators ?

```
 cat /etc/lsb-release; uname -a
```
```
 lspci -nnk | grep -iA2 net
```
```
lsusb
```
```
iwconfig
```
```
arch
```
```
 rfkill list all
```
```
 lsmod
```
```
sudo iwlist wlan0 scan
```

---

