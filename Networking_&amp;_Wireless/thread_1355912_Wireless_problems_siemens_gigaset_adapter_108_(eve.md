---
title: "Wireless problems siemens gigaset adapter 108 (everything included)"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by wvdoorn on 2009-12-15
Hi guys,

I've joined this forum because I feel like this is my last chance before buying new hardware to have an internet connection on Ubuntu.

I downloaded Ubuntu 3 days ago, and installed it directly. Then the struggling began, with installing my wireless USB-adapter. After some searching on google I saw that my adapter was one of the *worst* supported adapters for Linux. I will try to include almost EVERYTHING what I did, and all information. Note: I've been trying to make it work for ~15 hours.

**Router:** KPN Experia BOX
**Adapter:** Siemens gigaset usb adapter 108 (not built-in, IN the USB-port)
**Chipset(?) id:**: 129b:160c

This is basic information, note that everything worked fine before on Windows.

Basically I tried two things:

A) Downloading the official driver from the gigaset website.

This worked fine before, it said "Device {ID} installed", but no interface called 'wlan0' or something.

ndiswrapper -l: [http://codepad.org/waGbQDZY](http://codepad.org/waGbQDZY)
iwconfig: [http://codepad.org/5FsQaWxj](http://codepad.org/5FsQaWxj) 
ifconfig: [http://codepad.org/zvxSsc6V](http://codepad.org/zvxSsc6V) 
dmesg: [http://codepad.org/GUMuI5b0](http://codepad.org/GUMuI5b0) 

B) Downloading drivers from netgear.de (Which everyone recommends)

I also tried downloading the drivers 
from [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Siemens_Gigaset_USB_108](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Siemens_Gigaset_USB_108) but then it doesn't show that 
any device/hardware is installed @ ndiswrapper + 
it gives error at dmesg, and wlan0 is still not there. If I edit the .conf files from 1280:4250.F.Conf to {id}.F.CONF in /etc/ndiswrapper/*drivers*/ it says the device is installed BUT still no wlan0 there.

Several people tried to help me, but they all couldn't get it to work. If you need some more information, just post, since, like I already said, I tried everything.

Thank you very much for reading.

---

### Post by wvdoorn on 2009-12-16
bump

---

### Post by wvdoorn on 2009-12-17
bump

---

### Post by wvdoorn on 2009-12-17
bump :-(

---

### Post by wvdoorn on 2009-12-18
bump

---

### Post by wvdoorn on 2009-12-18
bump

---

### Post by wvdoorn on 2009-12-18
bump

---

### Post by wvdoorn on 2009-12-19
bump

---

### Post by wvdoorn on 2009-12-19
bump

---

