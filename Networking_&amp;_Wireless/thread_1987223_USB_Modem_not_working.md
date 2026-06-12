---
title: "USB Modem not working"
date: 2012-05-26
forum: Networking &amp; Wireless
---

### Post by bimaljr on 2012-05-26
Hello,

I have ZTE USB modem. In older version of Ubuntu (11.04, 11.10) I had installed SAKIS3G tool. So my dongle appear in the Network Selection dropdown list. I just configure it and it's working.

But in Ubuntu 12.04, I cannot see it. After some googling, I find that it will be detected on boot. So I have inserted it and rebooted my system and it's detected. Than it's connected and working perfectly but after two-three minutes it's disconnected and removed from the network dropdown. So I cannot see or select it.

Can you help me so I can connect to my 2G internet connection via my ZTE dongle?

---

### Post by bimaljr on 2012-05-26
lsusb command output:


```
bimal@bimal-homelinux:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:0016 ZTE WCDMA Technologies MSM 
```

---

### Post by ILUVU on 2012-05-28
USB Modem wil be working,

Try to use your  ZTE USB modem in two steps
1. Use a Product ID and Vendor ID changers in windows
2. Use a GUI (Graphicla user interface ) in ubuntu

than use your modem in ubuntu . Hope it will 100% work

To see full instruction go to[ http://luv2know.wordpress.com]("http://luv2know.wordpress.com")

---

