---
title: "Huawei E2010 football modem not detected"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by bigboss92 on 2010-07-06
I have recently changed my laptop's OS to ubuntu 10.04. I plugged in the Huawei E2010 usb modem, but it was detected as a mass storage device and not as a 3g modem. Can someone pls help??

---

### Post by pdc on 2010-07-06
can you tell us what 

> lsusb  gives you?

usb_modeswitch should help ..........

go here

click on the 1.1.3-1 version (the latest) in the sid unstable: unstable means latest and best ..........

install by selecting gdebi installer; (right-click on file when downloaded, if you system doesn't offer you an earlier option)

try and configure now with this installed

if no joy, 

copy and paste this command into a terminal and copy and paste the result back here

> dmesg | grep tty

---

### Post by bigboss92 on 2010-07-06
> **pdc said:**
> 
usb_modeswitch should help ..........

go here

click on the 1.1.3-1 version (the latest) in the sid unstable: unstable means latest and best ..........

install by selecting gdebi installer; (right-click on file when downloaded, if you system doesn't offer you an earlier option)

try and configure now with this installed

if no joy, 

copy and paste this command into a terminal and copy and paste the result back here

I am sorry, i am still new to ubuntu, my second day actually.
lsusb gives:
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by pdc on 2010-07-07
> ID 12d1:1446 Huawei Technologies Co., Ltd. 

OK; so this is your modem; as you say, it is being seen as a storage device

so do you know if you have 32bit or 64bit Ubuntu

if you don't know, type

> uname -r into a terminal: if it says, i686 somewhere there, you are 32bit 

....... so you need usb_modeswitch

go here

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

scroll down: to usb_modeswitch on this page and download the right package for your system: ie 32bit or 64bit 

when you click, your system is likely to say: do you want to install with gdebi installer: say yes, and it will ask for your sudo password: give that;

once usb_modeswitch is installed;

reboot; 

your modem should be recognised ..........

usb_modeswitch will do its magic all by itself for you

---

