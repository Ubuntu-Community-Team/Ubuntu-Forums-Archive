---
title: "amstart.sh"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by BKK on 2006-05-10
I followed the directions found online to compile kernel and load amedyn driver
any insights on the following??

jkbo@ubuntu:~$ sudo amstart.sh
Password:
>>> Inits Zyxel 630-11 & Asus AAM6000UG <<<

>>> Removing amedyn driver...

>>> Loading firmware...
Zyxel 630-11 & Asus AAM6000UG microcode upload program. 02/08/2004
Josep Comas <jcomas@gna.es>
Sundar <sundar@cynaptix.biz>
Eduardo Espejo <eespejo@users.sourceforge.net>

I found ADSL modem with VendorID = 06b9 & ProductID = a5a5
Loading and sending /usr/sbin/fw-usb.bin...
Firmware is sent!
Waiting ADSL line is up (until -1 seconds)...
......
ADSL line is up
>>> Loading driver...
FATAL: Module crc32 not found.
Launching driver in normal mode...

/usr/sbin/amload.sh successful
Setting PPP over Ethernet...
>>> Setting PPPoE <<<

>>> Activating send/receive data...
Zxyel 630-11 & Asus AAM6000UG ioctl call. 24/9/2003
Josep Comas <jcomas@gna.es>
Sundar <sundar@cynaptix.biz>
Eduardo Espejo <eespejo@users.sourceforge.net>

I found ADSL modem with VendorID = 06b9 & ProductID = a5a5

>>> Loading br2684 kernel module...

>>> Loading ppp_generic...

>>> Loading br2684ctl...
/usr/sbin/amnet4up.sh: line 64: /br2684ctl: No such file or directory
jkbo@ubuntu:~$

---

