---
title: "sero7 pro"
date: 2013-06-10
forum: Mobile Technology Discussions (CLOSED)
---

### Post by boregard on 2013-06-10
hi, just purchased the sero7 pro, anyone else got one yet? i am having trouble connecting it to 12.04 desktop with usb cable, other than that i like it so far. regards

---

### Post by hansdown on 2013-06-10
Hi  boregard.

The price is right. Have you upgraded to jellybean 4.2?

---

### Post by boregard on 2013-06-11
> **hansdown said:**
> Hi  boregard.

The price is right. Have you upgraded to jellybean 4.2?
no, i am trying to get it to connect to my desktop via usb cable and having no luck. everything else seems to be working good though. best regards

---

### Post by hansdown on 2013-06-11
When you have it plugged in, what does

> lsusb

return?

---

### Post by boregard on 2013-06-12
> **hansdown said:**
> When you have it plugged in, what does



return?this is the return i get.thanks

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6363 Alcor Micro Corp. 
Bus 001 Device 006: ID 109b:9106  
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 004: ID 04f2:1112 Chicony Electronics Co., Ltd

---

### Post by boregard on 2013-06-12
okay, after checking tethering option in settings, it recognizes NVidia Corp.


```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6363 Alcor Micro Corp. 
Bus 001 Device 007: ID 0955:7103 NVidia Corp. 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 004: ID 04f2:1112 Chicony Electronics Co., Ltd 
```

---

### Post by hansdown on 2013-06-12
I found a couple things that may help.

Install

> easy tether

on the sero pro.

Go to

applications >development

and check usb debugging

This link is for android phones, but should be the same.

[http://www.upubuntu.com/2011/12/how-to-tether-your-android-phone-to.html](http://www.upubuntu.com/2011/12/how-to-tether-your-android-phone-to.html)

---

### Post by boregard on 2013-06-12
thanks hansdown, appreciate all your help. i have tried go-mtpfs,gmtp and searched the internet for a few days now with no luck. i think for now i'll just use sd card to transfer files. it would be alot easier to just connect to my desktop though. best regards

---

### Post by hansdown on 2013-06-13
Best wishes  boregard.

Wish I had one to test.

---

### Post by 3rdalbum on 2013-06-14
Ubuntu 12.04's implementation of MTP is broken. I was never able to get the later MTP versions to work on 12.04, so I used an FTP server on the phone/tablet and connected to it from the desktop over wifi.

---

### Post by boregard on 2013-06-14
> **3rdalbum said:**
> Ubuntu 12.04's implementation of MTP is broken. I was never able to get the later MTP versions to work on 12.04, so I used an FTP server on the phone/tablet and connected to it from the desktop over wifi.thanks, for suggestion may try that myself,tried everything else. right now i think i need a rest from this problem. completley frustated. quick question about something, is usb debugging the only thing that is supposed to be checked in developer options?
regards

---

### Post by boregard on 2013-06-21
> **3rdalbum said:**
> Ubuntu 12.04's implementation of MTP is broken. I was never able to get the later MTP versions to work on 12.04, so I used an FTP server on the phone/tablet and connected to it from the desktop over wifi.afte all the things i have tried i totally agree with you. so i  downloaded Software data cable app from play store and now i can connect via ftp. best regards

---

