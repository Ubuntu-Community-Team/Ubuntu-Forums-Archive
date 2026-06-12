---
title: "Wireless Ad-hoc Error"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by 888880566 on 2009-04-02
Hey,

I have a new Lenovo T400 with Ubuntu 8.04 installed and i got an error when i tried to set my wireless to ad-hoc mode.
----------------------------------------------------------
Interface Info:
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.3
netmask 255.255.255.0
wireless-key 1234567890
wireless-essid boozdtn
wireless-mode ad-hoc
wireless-channel 4

auto wlan0
----------------------------------------------------------
Driver Info:
iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
iwlagn: Copyright(c) 2003-2008 Intel Corporation
iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
-----------------------------------------------------------
Error message:
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                           Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
-----------------------------------------------------------

---

### Post by 888880566 on 2009-04-03
any one?>??

---

### Post by Tobi-fp on 2009-04-03
If you have a button for enabling / disabling your card, push it, and then restart.. Afterwards you should try to connect to a router instead of an ad-hoc to begin with (some driver modules does not support ad-hoc to the fullest.) If nothing works, i would recommend compiling the driver yourself

---

