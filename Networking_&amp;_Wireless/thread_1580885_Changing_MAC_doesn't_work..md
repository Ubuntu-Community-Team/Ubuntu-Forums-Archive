---
title: "Changing MAC doesn't work."
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by Freaky#Funga on 2010-09-24
Hi folks. My internet provider uses dhcp withc fixed IP addresses assigned to certain MAC. Since I use several machines I have to change local MAC sometimes.
I use sequence:```
ifconfig eth0 down
ifconfig eth0 hw ether 00:16:36:e2:a6:11
ifconfig eth0 up
dhclient eth0
```

Problem is, that this doesn't work. MAC address is changed (even i Wireshark i can see dhcp requests from this new MAC), but dhclient does not receive dhcpack.

Funny thing is, that changing MAC on WXP in device driver works fine.
Any suggestions?

---

### Post by shaneg-nz on 2010-09-24
Have you tried using macchanger?


darkhorse@darkhorse:~$ **sudo apt-get install macchanger**

darkhorse@darkhorse:~$ **sudo macchanger --mac 00:11:22:33:44:55 wlan0**

or whatever you want to change it to?

macchanger -s     show's your mac

---

