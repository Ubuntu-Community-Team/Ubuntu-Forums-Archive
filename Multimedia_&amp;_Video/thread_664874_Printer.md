---
title: "Printer"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by dmsn on 2008-01-11
Hey im trying to install my HP 1018 printer.

lpstat -t
scheduler is running
no system default destination
device for HP_LaserJet_1018_USB_1: usb://HP/LaserJet%201018
device for laserjet_1018: usb://HP/LaserJet%201018
device for laserjet_1018_1: usb://HP/LaserJet%201018
HP_LaserJet_1018_USB_1 accepting requests since Fri 11 Jan 2008 11:51:46 PM CET
laserjet_1018 accepting requests since Fri 11 Jan 2008 11:59:29 PM CET
laserjet_1018_1 accepting requests since Fri 11 Jan 2008 11:59:56 PM CET
printer HP_LaserJet_1018_USB_1 disabled since Fri 11 Jan 2008 11:51:46 PM CET -
        Filter "foomatic-rip" for printer "HP_LaserJet_1018_USB_1" not available: No such file or directory
printer laserjet_1018 is idle.  enabled since Fri 11 Jan 2008 11:59:29 PM CET
printer laserjet_1018_1 is idle.  enabled since Fri 11 Jan 2008 11:59:56 PM CET


lsusb
Bus 005 Device 002: ID 03f0:4117 Hewlett-Packard


But it doesnt work to print  out.
lp test.txt
lp: Error - no default destination available.


What should i do ?


Thanks for help.

---

### Post by wolfen69 on 2008-01-11
read this page [http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018) for more info on getting it to work. it seems you will need the foo2zjs driver.

---

