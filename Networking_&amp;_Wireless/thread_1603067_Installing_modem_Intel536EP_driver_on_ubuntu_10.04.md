---
title: "Installing modem Intel536EP driver on ubuntu 10.04.1"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by irmtfan on 2010-10-22
i follow this guide:
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

then i find my modem:
$ lspci | grep 536EP
> 
01:06.0 Communication controller: Intel Corporation 536EP Data Fax Modem

and reach to this page:
[http://groups.google.com/group/ubuntu-modems/web/modem-driver-downloads-for-536ep](http://groups.google.com/group/ubuntu-modems/web/modem-driver-downloads-for-536ep)

there is a deb package for ubuntu 10.04 but my kernel version is  2.6.32-[COLOR=Red]25[/COLOR]-generic
by the way i install this package but gnome ppp can not detect modem.
i get this using command line: $ sudo modprobe Intel536 
> 
FATAL: Error inserting Intel536 (/lib/modules/2.6.32-25-generic/kernel/drivers/char/Intel536.ko): Invalid module format
what can i do now?

---

### Post by irmtfan on 2010-10-28
i try to solve this problem but still i didnt find anything.
anybody can help?

---

### Post by ink_rus on 2012-01-11
same problem under oneric :( I'm using "deb" driver from [https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

---

