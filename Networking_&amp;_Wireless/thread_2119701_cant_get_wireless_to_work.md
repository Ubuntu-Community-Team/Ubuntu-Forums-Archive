---
title: "cant get wireless to work"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by jordanetodd on 2013-02-24
I installed 12.10 on my macbook pro 8,1. I have tried everything in the wiki to get the WiFi up and running, but so far, no dice. Any suggestions?

---

### Post by QIII on 2013-02-24
*Moved to** Networking & Wireless***

---

### Post by Hadaka on 2013-02-24
Hi, please post the output of..

```
rfkill list all
lspci -nn | egrep '0200|280' 
```
thanks

---

### Post by jordanetodd on 2013-02-24
Rfkill list all
0: hci0: Bluetooth
       Soft blocked: no
       Hard blocked: no
Lspci -nn | egrep '0200|280'
02:00.0 Ethernet controller [0200]: broad com corporation NetXtreme BCM57765 gigabit Ethernet PCIe [14e4:16b4] (rev 10)
03:00.0 Network Controller [0280]: Broad com Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 2)

---

### Post by Hadaka on 2013-02-24
Hi, please try this..

```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43 
```
thanks

---

### Post by jordanetodd on 2013-02-24
> **Hadaka said:**
> Hi, please try this..

```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43 
```
thanks

all fixed, thank you so much!

---

### Post by Hadaka on 2013-02-24
Great ! glad that worked for you.
please use thread tools and mark this SOLVED

---

