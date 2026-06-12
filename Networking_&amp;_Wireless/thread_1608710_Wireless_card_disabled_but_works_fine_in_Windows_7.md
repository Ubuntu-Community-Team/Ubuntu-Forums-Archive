---
title: "Wireless card disabled but works fine in Windows 7"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by marylandman on 2010-10-29
Hi,

I just got Ubuntu and am new at this stuff. I have a dual boot windows 7 64 bit one and ubuntu 10.4. I booted ubuntu at startup and then tried to go online, but it says my wireless device is disabled. I tried pressing the keys on my keyboard to see if that may work, but it doesnt. I am lost and new at this. Any help would be appreciated. Thanks

---

### Post by chili555 on 2010-10-29
Let's try to figure out why it's disabled. The first step is to figure out what wireless card you have and then we'll figure out what driver it needs and make sure it's installed correctly. 

Please open Applications > Accessories > Terminal and, if your wireless in built-in, type:```
lspci -nn
```Post here the part that describes your wireless card. If it's a USB card, post:```
lsusb
```Also, please post:```
rfkill list all
```What kind of computer is it? Laptop or desktop? What brand is it?

---

