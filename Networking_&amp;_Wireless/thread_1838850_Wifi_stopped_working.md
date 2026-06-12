---
title: "Wifi stopped working"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by mrpenguin on 2011-09-04
For no reason at all my WiFi just stopped working on my Asus laptop running Ubuntu 11.04
The little WiFi icon on the top bar is gray with an exclamation over it and when i click on it everything is grayed out and not assessable except for VPN Connections and Enable networking (which is enabled) and edit connections.

I can not see My wireless network at all.

I have no idea what to do

---

### Post by wildmanne39 on 2011-09-04
Hi, please run these commands in the terminal:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mrpenguin on 2011-09-04
Thank you very much for the reply but I am an idiot !!!!
I swapped hard drives and put in my windows hard drive and wifi was not working on there either, so I knew then its not Ubuntu but might be my card not working, I googled the problem and realized there is an on and off switch on the side of the computer for the wife and it was off .......... had this laptop for 6 months and never knew about the switch ...lol

Thanks

---

### Post by wildmanne39 on 2011-09-04
Hi, your welcome! glad you got it working.

---

