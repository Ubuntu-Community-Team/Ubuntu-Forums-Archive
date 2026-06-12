---
title: "Broadcom Airforce on Jolicloud"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by evangaj on 2012-04-21
I have installed Jolicloud operating system onto my HP Pavillion zv6000.

Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

I have tried to look at the other Ubuntu forums but none of them have helped

---

### Post by wildmanne39 on 2012-04-21
Hi, if it is based on ubuntu this should work.
```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```
Thanks

---

### Post by evangaj on 2012-04-22
It says that it could not find package b43legacy-installer. I tried to use the 

sudo apt-get install b43-fwcutter firmware-b43-installer

and also the same problem occured

---

### Post by bkratz on 2012-04-22
> **evangaj said:**
> It says that it could not find package b43legacy-installer. I tried to use the 

sudo apt-get install b43-fwcutter firmware-b43-installer

and also the same problem occured



The legacy you tried first was actually the wrong package for your card.  The second try was correct. did you have a wired connection when you tried this?
According to

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

This is the recommended command
sudo apt-get install firmware-b43-installer

---

### Post by wildmanne39 on 2012-04-22
Hi, I wanted to apologise because I gave the wrong command I do not know how I managed to do that.

---

