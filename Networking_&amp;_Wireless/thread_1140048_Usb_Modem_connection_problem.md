---
title: "Usb Modem connection problem"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by psriram on 2009-04-27
hi,

I Was trying to fix my Connexant USB modem with Ubuntu from last year but my efforts are in vain.

Can anyone help me to fix it out.. Windows OS detected my usb modem and install drivers for it now working fine

In ubuntu the led light in modem is blinks and it is stable but cannot connect to internet

was trying that cxacru patch which was advised by many users around but never worked out..

can anyone help me from this problem

My modem is Connexant Beetel 100cx USB modem provided by Airtel,India

Image here 
[http://beetel.net/cache/thumbnail_100cx_small_f30f2fabaaa8d838b1c7a9e1f4ae5749.jpg](http://beetel.net/cache/thumbnail_100cx_small_f30f2fabaaa8d838b1c7a9e1f4ae5749.jpg)

---

### Post by inobe on 2009-04-27
hi

have you read the community documentation.

[https://help.ubuntu.com/community/UsbAdslModem/AccessRunner](https://help.ubuntu.com/community/UsbAdslModem/AccessRunner)

---

### Post by psriram on 2009-04-28
this is my latest screen shot

somehow link established

[[IMG]http://img262.imageshack.us/img262/1497/22222m.th.png[/IMG]](http://img262.imageshack.us/my.php?image=22222m.png)

what do  i have to do for ppp0?

do this here
/etc/network/interface

 iface ppp0 inet ppp ?

can some one help me to  connect to internet

---

### Post by khelben1979 on 2009-04-29
What happens if you try to use the DHCP command:
```
sudo dhclient restart
```

Other than that, there is a pain on getting usb modems to work with Linux and I would suggest that you get yourself an ethernet modem instead, however, there can still be hope on gettng this work, but I'm not positive.

---

### Post by psriram on 2009-04-29
khelben i am postive after long struggle i am successfull i configuring my modem.NOw i am browsing via ubuntu :)very happy Mods can close this thread

---

### Post by khelben1979 on 2009-04-29
Okay! Sounds positive.

One thing that you may not know about usb modems is that they take more cpu power also. Just a note. Glad that you got it working.

---

### Post by ababa on 2010-01-09
psriram , i too have a airtel connection with beetel 100cx usb modem . can you give me a step by step procedure to get it working in ubuntu . I am really new to linux so a step by step guide would be really appreciated

---

### Post by omar91089 on 2010-05-11
[http://www.ae.iitm.ac.in/pipermail/ilugc/2006-August/027978.html](http://www.ae.iitm.ac.in/pipermail/ilugc/2006-August/027978.html)

check out this.....it may he helpful

---

### Post by upsla on 2011-01-13
some body help me. i too have beetel 100 cx modem. i have the same problem.

---

