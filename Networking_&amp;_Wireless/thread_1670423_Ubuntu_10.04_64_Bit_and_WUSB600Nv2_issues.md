---
title: "Ubuntu 10.04 64 Bit and WUSB600Nv2 issues"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by vdubbugman53 on 2011-01-18
so i have been trying to do this for several days now and i can not get my WUSB600N V2 to work.  

i have downloaded that most recent drivers and i have ran 
```
cd Desktop/RT3572
make
sudo make install 
```i have set required values = y 

and i have black listed the rt2800usb driver

if i ```
lsusb
```i get 

B```
us 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 005: ID 1737:0079 Linksys **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```and i belive that is it there but i still have nothing.  any help

---

