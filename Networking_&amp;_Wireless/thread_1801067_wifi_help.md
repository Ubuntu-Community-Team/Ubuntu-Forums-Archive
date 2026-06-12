---
title: "wifi help"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Kdroidx on 2011-07-09
I need help with my wireless network. It doesnt recognize that any network is around. The broadcom STA driver will not install and it says "Please have a look at the log file for details: /var/log/jockey.log" the jog file says 

2011-07-09 21:21:33,921 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-09 21:21:33,987 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-09 21:21:42,640 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-09 21:21:42,678 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-09 21:21:42,695 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-09 21:22:40,418 DEBUG: Shutting down

I'm on 11.04, im very new to ubuntu and im on a macbook 6,2 i7. The wifi worked when i booted from cd but now it doesnt work once i installed.

---

### Post by nm_geo on 2011-07-09
Do these in terminal copy and paste 

```
lspci -nn
``````
rfkill list all
``````

sudo lshw -C network
```We can start with those first

---

### Post by Marky FAQ on 2011-07-10
Does the driver supports Windows?
Get windows drivers and find .inf file and run windows wireless driver
and click install.

that simple

---

