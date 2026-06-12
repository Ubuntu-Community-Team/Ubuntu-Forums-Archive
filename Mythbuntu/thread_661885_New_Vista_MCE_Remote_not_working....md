---
title: "New Vista MCE Remote not working..."
date: 2008-01-08
forum: Mythbuntu
---

### Post by Article22 on 2008-01-08
I recently purchased this remote ([http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=583848](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=583848)) and it doesn't work in MythBuntu.

It has the following details :   

--- lsusb ---   
ID 0471:060d Philips   

--- dmesg ---   
lirc_dev: IR Remote Control driver registered, at major 61  lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 RemoteControl driver for LIRC $Revision: 1.33 $

Looking in the latest lirc_mceusb2.c file it seems that the ID 0471 is fine and assigned to Philips but there is only the suffix of 0x0815 assigned to it which is for the older MCE 2005 receiver.

Can one of the developers get this passed downstream to be added please as this remote is the replacement to the older RC6 MCE 2005 remote.

I tested the remote using the older MCE 2005 receiver and it works fine so it is only the new receiver which needs to be defined.

Thanks,

Nigel.

---

### Post by anand on 2008-07-13
I had a similar problem with my particular Vista MCE remote (made by Topspeed).

I downloaded the latest version of LIRC from their webpage and compiled it and installed it myself.  It puts its kernel modules into /lib/modules/2.6...../misc.  The stock kernel modules for LIRC are in /lib/modules/2.6..../ubuntu/media/lirc.  I moved the stock modules out of that directory to avoid any duplicated module problems, then ran depmod/modprobe and my remote worked fine.

It's kind of frustrating that Ubuntu is still using an old version of LIRC.  My particular remote is included in LIRC 0.8.3 and was in SVN for months prior to that release (and prior to 8.04 coming out) but I guess Ubuntu hasn't updated the source files used for their "0.8.3pre" version in a while.

---

### Post by superm1 on 2008-07-14
> **anand said:**
> I had a similar problem with my particular Vista MCE remote (made by Topspeed).

I downloaded the latest version of LIRC from their webpage and compiled it and installed it myself.  It puts its kernel modules into /lib/modules/2.6...../misc.  The stock kernel modules for LIRC are in /lib/modules/2.6..../ubuntu/media/lirc.  I moved the stock modules out of that directory to avoid any duplicated module problems, then ran depmod/modprobe and my remote worked fine.

It's kind of frustrating that Ubuntu is still using an old version of LIRC.  My particular remote is included in LIRC 0.8.3 and was in SVN for months prior to that release (and prior to 8.04 coming out) but I guess Ubuntu hasn't updated the source files used for their "0.8.3pre" version in a while.
The "0.8.3preX" release was up to date as per the last time one of these snapshots was made from SVN.

The "proper" way to add support for your remote is to grab lirc-modules-source, and patch the file in /usr/src.  Run a dkms build, dkms install and you will have updated kernel modules that automatically run when a new kernel is installed.

---

