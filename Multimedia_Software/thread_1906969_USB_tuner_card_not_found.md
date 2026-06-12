---
title: "USB tuner card not found"
date: 2012-01-10
forum: Multimedia Software
---

### Post by FuzzyFeat on 2012-01-10
First: This card was playing quite nicely in VLC and Kaffeine.

Then after a shutdown and reboot I get this message in VLC:

VLC is unable to open the MRL 'dvb://frequency=0'

Kaffeine can not find the card either. 

This is the output for ~$ lsusb:

master@Slave:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f9:0228 Brother Industries, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 005: ID 2040:7200 Hauppauge** 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:63fb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As you can see the Hauppauge card is recognized with the lsusb request. The card also lights up.

Possibly connected: the card does not start-up/recognized when plugged in after boot, only while it is inserted before boot up.
Same with the mouse.

I have tried this in all usb sockets with the same results.

Any assistance will be appreciated.

---

### Post by FuzzyFeat on 2012-01-11
Two days later it fixed itself. WTF? Still would like to know how to fix it if it happens again.

---

### Post by BicyclerBoy on 2012-01-11
Dual booting with windows ? i.e. firmware ?
The haupig USB stick requires USB2.0 because (I think) it does not support PID filters..(LinuxTV.org)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

---

