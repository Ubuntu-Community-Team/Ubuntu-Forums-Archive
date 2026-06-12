---
title: "Wifi not working"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by zeusdo on 2012-08-21
I just installed Ubuntu but can not get the wifi to work. I went to System settings/ hardware/ additional drivers and it found one a trying to download and install but then came back with an error. It told me to go to the log file and this is what it said:

2012-08-21 13:30:55,443 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-08-21 13:30:55,444 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-08-21 13:30:55,553 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled

---

### Post by Finnicella on 2012-08-21
Hi, please give to me the output of these commands:
```
sudo lshw -C network
```
```
sudo rfkill list all
```
```
lspci -nn | grep -i net
```
```
lsmod
```
Bye and I'm sorry for my english. :D

---

### Post by zeusdo on 2012-08-21
Thanks for your reply, but I got it working. I did a full system update, about 416 updates found. Then it was able to install the correct driver and all is working fine now.

---

### Post by Finnicella on 2012-08-23
I'm very happy you solved.:D
Bye

---

