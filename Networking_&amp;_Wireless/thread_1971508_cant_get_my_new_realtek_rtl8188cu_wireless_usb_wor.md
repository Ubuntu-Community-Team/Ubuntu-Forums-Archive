---
title: "cant get my new realtek rtl8188cu wireless usb working"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by uraliss on 2012-05-02
Hi Folks,
Im having trouble getting this device working on ubuntu 10.10

i have downloaded the drivers from realteks website and I have run the installer.

Network manager doesn't see the device.

> ls /lib/firmware/RTL8192SU
rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin

> lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 047f:c007 Plantronics, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> modprobe rtl8192cu
FATAL: Module rtl8192cu not found.


Ive done a search on the forum but i'm not getting anywhere with it.

Can anybody help please?

---

### Post by uraliss on 2012-05-03
anyone?

---

### Post by Aussie John on 2012-05-10
I think you may be using the wrong driver.
your device is RTL8188CU  you need driver 8192CU NOT 8192DU

They are different

                                    rgds   Auss John

---

