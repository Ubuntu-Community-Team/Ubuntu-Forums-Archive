---
title: "install huawei e220 on ubuntu 9.10"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by tembakau77 on 2010-04-26
Hi All,

I'm newbie with ubuntu, just install my HP notebook with Ubuntu 9.10. My problem is my ubuntu can't detect my Maxis Huawei E1762 (its not E220 - sorry) usb modem. Please help. thanks.

---

### Post by dineshs on 2010-04-26
In a terminal (applications-accessories=terminal)type
```
lsusb
```and enter.post the result
You can follow these guides
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)for setting up dialup connection

[https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)

---

### Post by GeorgeVita on 2010-04-26
Hi **tembakau77** and **dineshs**,
use any other connection to update your ubuntu 9.10 as initial (liveCD) version has a bug that affects most 3g modems.

Consider also a firmware update on your Huawei E220 (check your provider's internet site).

Regards,
George

---

### Post by tembakau77 on 2010-04-26
Hi [GeorgeVita]("http://ubuntuforums.org/member.php?u=638001") and Dineshs,

For your information I already update my ubuntu 9.10, and I'm using Huawei E1762 broadband modem. I can't find any firmware update download from any site. Please advice.

The way i use to connect my broadband modem is to activate it in windows, restart and boot to ubuntu, then ubuntu can detect my broadband modem. Please advice. thanks.

---

### Post by GeorgeVita on 2010-04-26
> **tembakau77 said:**
> ... I can't find any firmware update download from any site.
Hi **tembakau77**,
firmware update is needed for Huawei E220 (as stated on thread's title).

To determine system activity for your modem (E1762):
- boot without modem
- **wait** for the system to load
- open a terminal window (Applications > Accessories > Terminal)
```
sudo dmesg -c
```
- now attach your modem and **wait** 30 seconds
- from terminal:
```
lsusb
``` ```
dmesg
```
- if any CD-ROM icon appear on desktop right click and eject it
- after ejecting **wait 20 sec.**, retry dmesg and lsusb

Post above data EXCEPT those from 1st 'sudo dmesg -c' as it is very long without data for your modem.

Regards,
George

---

