---
title: "Steps to bring IP networking manually up through USB"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by pierref on 2012-01-30
Hello

After Googling and searching this forum, I didn't find any "How to bring up an IP interface on an USB port" guide.

When the USB device is plugged in (an Android smartphone), a /dev/ttyACM0 entry shows up, but no usb0 interface.

With the lsusb command, I can see on which bus that device is connected.
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 004: ID 04e8:689e Samsung Electronics Co., Ltd** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` 

Only usb_storage module is loaded automatically, but not usbnet. I can load it manually issuing: ```
sudo modprobe usbnet
```

My question is: what do I still have to do for connecting the usb0 interface with that specific USB device on a particular USB bus/port/device?

I want to do it first manually; later I will see how to manage it automatically with udev.

---

### Post by akmp on 2012-02-15
Hi pierref,
 
I also have the same issue as you have described.
 
I am connecting a nokia phone to the USB port and want it to get detected as usb0 interface.
 
currently i get "usbpn0" interface up when i do "ifconfig -a" and also i get hte following under /dev
 
/dev/ttyACM0
/dev/ttyACM1
 
were you able to get it up, are there any other dependency other than "cdc_ncm" on the linux PC side?
 
with thanks and regards
akmp

---

### Post by pierref on 2012-02-15
> **akmp said:**
> I am connecting a nokia phone to the USB port and want it to get detected as usb0 interface.
 
currently i get "usbpn0" interface up when i do "ifconfig -a" and also i get the following under /dev
 
/dev/ttyACM0
/dev/ttyACM1
 
were you able to get it up, are there any other dependency other than "cdc_ncm" on the linux PC side?

Well, you are a step further than me. I couldn't get further. 

Can't you use the usbn0 interface instead of usb0? Anyway, I think that you can change the name of the interfaces appearing in the output of ifconfig by adding some rule into the udev configuration files. In that way, I once could reorder the eth0; eth1, eth2 NICs in some server.

I advise you to search any occurence of "usbpn" in /etc/udev and /lib/udev, issuing:
```
sudo grep -r usbpn /lib/udev/rules.d /etc/udev/rules.d
``` and tell me if you get wiser with that output.

---

### Post by akmp on 2012-02-18
Hi pierref,
 
Did not find any rules for usbpn0 interface.
 
Couple of pointers i am working on are
 
1. To ensure CDC_NCM driver to be used by the USB interface, currently i see only CDC_ACM driver in the dmesg logs when phone is connected.
2. Selecting the right setting in the phone, in the phone i have multiple options to select for USB type and i select Nokia PC suite which may not be the right selection.
 
Please do help if you find across any further info to make this work.
 
With thanks and regards
akmp

---

