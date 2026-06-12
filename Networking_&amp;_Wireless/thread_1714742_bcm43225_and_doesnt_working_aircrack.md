---
title: "bcm43225 and doesnt working aircrack"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by thskat on 2011-03-25
hi 

i have Broadcom Corporation BCM43225 and aircrack doesnt working, i think problem is in drivers
but i dont know what can i do ... i was looking for but i diddnt find any working ;/

---

### Post by josephmills on 2011-03-25
> **thskat said:**
> hi 

i have Broadcom Corporation BCM43225 and aircrack doesnt working, i think problem is in drivers
but i dont know what can i do ... i was looking for but i diddnt find any working ;/

hi there I am new to linux but are you having troubles with monitor mode or injecting? Here is a link I hope it helps  [http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

---

### Post by thskat on 2011-03-26
yea that exactly prolbem which i have
can you help me with install these drivers ?

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)
i should install b43, but i am new on linux and i even dont know how to install those
there is a patch file but i dont know what i have to do with this

---

### Post by bkratz on 2011-03-26
> **thskat said:**
> yea that exactly prolbem which i have
can you help me with install these drivers ?

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)
i should install b43, but i am new on linux and i even dont know how to install those
there is a patch file but i dont know what i have to do with this




According to this page your card requires the STA driver, not b43.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The STA driver is the official Broadcom version which does not support aircrack.

---

### Post by thskat on 2011-03-26
so, how can i use aircrack on ubuntu ?

---

### Post by alan2796 on 2011-03-27
Please correct me if im wrong, but broadcom released an open source driver that supports the b43225 a search on this forums and you will find a link o how to download compile and install it search new broadcom driver, I dont think aircrack page has been updated?  I have that card in my acer and the card appears to get into monitor mode

---

### Post by thskat on 2011-03-30
[http://ubuntuforums.org/showthread.php?t=1617380&highlight=new+broadmcom+driver](http://ubuntuforums.org/showthread.php?t=1617380&highlight=new+broadmcom+driver)

does it help with  troubles ?
monitor mode or injecting

---

### Post by thskat on 2011-03-31
ref

---

### Post by thskat on 2011-04-09
the main problem is this 
> 
Interface    Chipset        Driver

eth1        Unknown         wl


there is a Unknown chipset...
i really dont know what can i do to reapir this ... ;/

---

