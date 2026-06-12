---
title: "pctv 460e and hauppage win tv nova s2 usb"
date: 2013-03-14
forum: Multimedia Software
---

### Post by sparklyballs on 2013-03-14
hi all, i have been playing around with ubuntu for just about a week now on a bootcamped mac mini late 2012, after some initial frustrations i have got hd-audio passthrough and ethernet working in the same kernel (3.7.4 on ubuntu 12.10). 

my next two projects are setting up a tv server backend, it's going to either be tvheadend or myth (not decided yet) but before that i have an issue with two of my three tuners, and the other part of the project is getting the remote working (not for this thread though). 

so concentrating on the tuner cards, here is a copy pasta from terminal. 

sparklyballs@LINUX-HTPC:~$ uname -r
3.7.4-030704-generic
sparklyballs@LINUX-HTPC:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 003 Device 005: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 004 Device 002: ID 0bc2:3320 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 006: ID 1d57:32da Xenta 2.4GHz Receiver (Keyboard and Mouse)
Bus 003 Device 007: ID 0e8d:1956 MediaTek Inc. 
Bus 003 Device 008: ID 2013:024f PCTV Systems nanoStick T2 290e
Bus 003 Device 009: ID 2013:024c PCTV Systems 
Bus 003 Device 010: ID 2040:d900 Hauppauge 
Bus 003 Device 011: ID 1934:5168 Feature Integration Technology Inc. (Fintek) F71610A or F71612A Consumer Infrared Receiver/Transceiver
Bus 002 Device 008: ID 05ac:828a Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
sparklyballs@LINUX-HTPC:~$

as you can see the vendor names for the tuner cards are coming up, but not the specific cards, i briefly tried mplayer from a tutorial i found online and it worked fine with the pctv290e on a terrestrial feed  but the other two cards were a no go, not finding a satellite signal. the two cards in question are in the title of this thread. does anyone know whether these cards are supported in linux and if they, will it work with 3.7.4 

thanks for any help or advice.

---

