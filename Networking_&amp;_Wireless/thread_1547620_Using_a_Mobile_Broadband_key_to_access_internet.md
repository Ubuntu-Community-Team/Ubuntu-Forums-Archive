---
title: "Using a Mobile Broadband key to access internet"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by Nano3.14 on 2010-08-07
So i recently-ish bought a netbook, and a mobile-broadband toggle to go with it, and set it aside to use later. i promptly installed the Netbook  remix on the laptop.

Well, I goofed, and didn't notice until well after I bought the WAN toggle that it was made for windows. so, I downloaded Wine in an attempt to run the start.exe and get my internet. unfortunately, the executable (and the entire drive, i found) are marked by ubuntu as read only. Is there anyway to change this to allow me to run the file? if i did, would it even work?

thanks!

---

### Post by pdc on 2010-08-07
plug it in

UNR (network remix)may just recognise it; and offer you a chance to configure

perhaps if you open a terminal: (from the accessories category I think)

and type in 

> lsusb

and copy and paste back what you get: UNR is doing well with mobile broadband these days ........

(so I am suggesting you don't need wine, and just use the UNR setup ...........)

---

### Post by Nano3.14 on 2010-08-07
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1410:5030 Novatel Wireless 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
tahdah. I realize i may have messed up with the linux install, seeing as there appears to be five installs... but it works.   
anyway, the 'novatel wireless' thing is the device, and i did not get any configuration options when in plugged it in.

---

### Post by pdc on 2010-08-07
your device is being seen as a virtual CD-ROM; (which it is ..)

go here 

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

scroll down the page and select the appropriate version of usb_modeswitch ..ie you will likely need the i386 version if using 32bit Ubuntu ..

download;

install; 

it should allow your system to recognise your device, and flips its ID so it is seen as a modem:

it may offer to configure for you; if not, right-click on network manager and configure mobile broadband from the tab

if you want to read more about how usb_modeswitch works, go here [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by Nano3.14 on 2010-08-07
awesome, thanks. that got it working.

---

