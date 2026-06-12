---
title: "reliance USB modem cannot connect"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by josejp on 2011-10-28
Dear ones, I have a reliance netocnnect USB modem from huawei. I have installed the driver as per the instructions in the CD. I have configured the device with pppconfig command. After that when I have applied the command pon it is showing that the /etc/modem is not a valid one. 
 
I have choose the modem port as ttyUSB_utps_mod as in the user manual. What else should I do to get my modem connected
 
expecting the answers soon

---

### Post by dineshs on 2011-10-28
Is it an HSDPA device ? I have a  Huawei E173 device and I use [this]("http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html") to connect.
Can you post the output of ```
lsusb
```and```
dmesg| grep tty
```

---

