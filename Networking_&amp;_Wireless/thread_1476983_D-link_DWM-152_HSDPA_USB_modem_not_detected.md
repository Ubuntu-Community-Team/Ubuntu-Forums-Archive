---
title: "D-link DWM-152 HSDPA USB modem not detected"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by c_siswan on 2010-05-08
Hello everyone,

My D-link DWM-152 HSDPA USB modem is not in the USB_modeswitch supported hardware list and ubuntu was recognized it as USB storage. Any idea how can i switch it to modem mode? I'm using ubuntu lucid.

Any help would be much appreciated.

---

### Post by pdc on 2010-05-08
does it create an icon on your desktop?

type 

> lsusb in a terminal; 

If so, (*ie you get an icon*) right-click; select "eject"

again

type

> lsusb

do you get a different ID;

does 

> dmesg | grep tty

give you some tty values: ie ttyUSB0 or perhaps  ttyACM0 ?

If you can copy and paste  your various lsusb results

---

### Post by c_siswan on 2010-05-09
Yes, it created an icon in my desktop,call CONNMGR.
lsusb output:
iewhwee@siewhwee-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:a800 D-Link System 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
siewhwee@siewhwee-laptop:~$ lsusb

lsusb after "eject":
siewhwee@siewhwee-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:a800 D-Link System 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
siewhwee@siewhwee-laptop:~$ 

The ID still remain the same as before. What to do next?

---

### Post by pdc on 2010-05-09
in the terminal if you copy and paste this

> dmesg | grep tty

looking for ttyUSB0 or ttyACM0 ....

if either you should be able to configure as here

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

half way down page ....... create a mobile broadband connection

---

