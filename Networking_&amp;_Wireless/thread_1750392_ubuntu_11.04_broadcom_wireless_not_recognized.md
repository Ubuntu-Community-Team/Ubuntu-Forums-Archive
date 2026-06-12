---
title: "ubuntu 11.04 broadcom wireless not recognized"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by nadavten on 2011-05-05
ive installed ubuntu 11.04 and my broadcom wireless is not recognized. solution ?

---

### Post by william.smith3 on 2011-05-05
Have you tried to disable then enable wireless as well as a reboot? Are you still having the issue with the wireless network not being recognized?

---

### Post by josephmills on 2011-05-05
lets see what kind of broadcom wireless model you have please open your terminal and type in 
```
lspci -vnn | grep 14e4

```
then paste here thanks

---

### Post by nadavten on 2011-05-06
Ethernet controller: ....
Network controller: Broadcom BCM4311 802.11b/g WLAN rev01

---

### Post by nadavten on 2011-05-06
Ethernet controller: ....
Network controller: Broadcom BCM4311 802.11b/g WLAN rev01

---

### Post by bkratz on 2011-05-06
> **nadavten said:**
> Ethernet controller: ....
Network controller: Broadcom BCM4311 802.11b/g WLAN rev01


This link should give you what you need.

[http://ubuntuforums.org/showthread.php?t=1741865](http://ubuntuforums.org/showthread.php?t=1741865)

---

### Post by nadavten on 2011-05-06
thank u all. managed to solve the problem ):P

---

### Post by bkratz on 2011-05-06
Glad you got it going!

---

### Post by fatpunk2 on 2011-05-27
thanks bkratz : same problem, same solution (aka your link to the other post), eveything works on my antique Pavilion dv5000 :P

---

