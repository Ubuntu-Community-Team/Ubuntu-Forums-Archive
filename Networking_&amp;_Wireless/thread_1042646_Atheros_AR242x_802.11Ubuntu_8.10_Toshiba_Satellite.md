---
title: "Atheros AR242x 802.11/Ubuntu 8.10/ Toshiba Satellite AMD Turion 64"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by Mrandoman on 2009-01-17
Toshiba L305D-S5893 (AMD Turion 64, Satellite) 

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Ubuntu 8.10

2.6.27-9-generic x86_64


I can't get wireless from my Atheros card. All I've tried so far are a few tips from friends, since I can't seem to find anything else.

---

### Post by ugm6hr on 2009-01-17
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

You need to enable this driver:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Some people have had to blacklist the atheros standard drivers and add ath5k to default modprobe list - there are plenty of similar posts here about it.

If you have tried "some tips" - you will have to tell us what, since previous attempts may interfere with the new driver.

---

### Post by PhaeZee5 on 2009-01-28
Hey man, bump! I'd like to see this fixed.

---

### Post by VirtualEdgar on 2009-01-30
Works like a charm. Thank you!

---

### Post by 5BallJuggler on 2009-01-30
One solution here:-

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by Linuxera on 2009-04-01
> **ugm6hr said:**
> [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

You need to enable this driver:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Some people have had to blacklist the atheros standard drivers and add ath5k to default modprobe list - there are plenty of similar posts here about it.

If you have tried "some tips" - you will have to tell us what, since previous attempts may interfere with the new driver.



Hi, 

My only problem with this solution is that although it works perfectly to activate my wireless, it CRASHES my ATI/AMD fglrx graphics driver, deactivating it and making impossible it's reactivation. 
My laptop is Toshiba Satellite A210 11I, Linux Mint Felicia x64.
I am trying other options..

Thanks in advance for any reply! :p

---

