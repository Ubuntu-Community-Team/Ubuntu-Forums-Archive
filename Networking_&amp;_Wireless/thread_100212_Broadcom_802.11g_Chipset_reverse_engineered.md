---
title: "Broadcom 802.11g Chipset reverse engineered"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by wish on 2005-12-07
Hi All, 

As reported by osnews.com, the broadcom  43xx chipset driver has been reverse engineered, they have done a clean  room implementation, as I understand it. 

The driver is located here: [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) 

Would any ubuntu god like to make a package out of this, as the broadcom chips are used by many OEMs. 
I would be very appreciative if I could get help with this.

---

### Post by daller on 2005-12-07
The driver is not fully reverse-engineered yet... (75%)

[http://linux-bcom4301.sourceforge.net/go/progress](http://linux-bcom4301.sourceforge.net/go/progress)

---

### Post by tokyovigilante on 2005-12-07
The open-source section of the code is already in the Linux kernel, and is in Dapper as of version 2.6.15-7 as modules.

They are working as of yesterday (with open networks only, WEP and WPA are coming), but require the Airport Extreme firmware to be extracted from the Mac OS driver, which is proprietary Apple code, which you are only entitled to if you own OS X/a compatible Mac, and cannot be distributed with Ubuntu. A package is unlikely to be available for this reason.

Check the Ubuntu PPC forum for instructions on extracting the driver and installing the latest kernel.

The reverse-engineering has been completed on the important 75%, allowing another group (hence the "clean room") to write a specification for the hardware, allowing yet another group (again "clean room") to write the driver.

---

