---
title: "usb dongle recognized as wlan0 but no wireless extensions?"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by dcast on 2006-02-22
Hi i installed a driver for my zd1211 based usb wireless dongle. It is now recognized in hal device manager as wlan0 and a wireless adapter. also when I type sudo lshw I get :

*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:4f:13:bb
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
 

edit: this also comes up farther up the list:

-usb
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: ZyDAS
                   physical id: 2
                   bus info: usb@1:2
                   version: 48.02
                   capabilities: usb-2.00
                   configuration: driver=zd1211 maxpower=500mA speed=12.0MB/s


for it. It is not recognized in networking, also when i boot teh computer it sometimes hangs on "starting hotplug subsystem" Can I make this work?

---

### Post by EKa on 2006-03-03
Seemingly my problem is the same, when trying to install usb wlan. I'd like to learn, if you have solved it so far.

thanks

---

### Post by EKa on 2006-03-05
My current situation is that my usb wlan stick gets packets sended, but the number of receives stays 0. Trials to open web pages lead to suggestion to check the address name and new trial. Also, it seems like the weather app tries to update itself but does not do it.

Any ideas?

---

