---
title: "wvdial + mobilebroadband : Cannot open /dev/ttyUSB0: Invalid argument error"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by alzaf on 2009-07-29
I use wvdial to connect to my mobile broadband connection ( a Huawei E160 dongle). This works fine but every once in a while I get this error:

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Invalid argument
--> Cannot open /dev/ttyUSB0: Invalid argument
--> Cannot open /dev/ttyUSB0: Invalid argument

I finally managed to figure out how to fix it which was to kill all the processes for NetworkManager and rebooting the machine.

Does anybody have a solution to stop this happening?

---

### Post by prat22 on 2010-12-15
[B]type sudo gnome-ppp

then you get the gui. go to modem, and you get a place to define where the modem is situated. for you, it may be /dev/ttyUSB0, but let it check itself. once done, dial again!
[/B]

---

