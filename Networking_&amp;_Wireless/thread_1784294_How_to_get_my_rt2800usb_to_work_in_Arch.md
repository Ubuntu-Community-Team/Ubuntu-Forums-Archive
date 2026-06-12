---
title: "How to get my rt2800usb to work in Arch"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Pougnet on 2011-06-16
I own a usb wifi card and it works great in Ubuntu. But, when i installed Arch linux on a separate hard drive, I could not get the wireless working. So, I am wondering if it is possible to take the firmware from the kernel on my Ubuntu machine and transfer it over to the arch machine? Here is the info on the device:
-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:26:5a:0d:15:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bgn

---

### Post by chili555 on 2011-06-16
You certainly could. Are you confident that missing firmware is the issue? May I see, obviously on the Arch machine:```
lsmod | grep rt2
dmesg | grep rt2
ls /lib/firmware | grep rt2
```Thanks.

---

