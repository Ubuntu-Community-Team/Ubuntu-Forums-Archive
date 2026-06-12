---
title: "How do I setup so I don't have to sudo wvdialconf every time I restart"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by lonewolf454 on 2008-12-24
Every time I turn computer off/back on it will not find my usb modem until I do wvdialconf /etc/wvdial.conf 

How do I fix this and possibly add the USB Modem to the network connections tab or make a shortcut on desktop that will wvdial moto (moto is the usb modem)

Thx in advance

---

### Post by mikewhatever on 2008-12-24
Try try adding the command to startup under System/Preferences/Session.

To create a launcher on the desktop, rightclick on the desktop, select 'Create Launcher', then enter the info.

---

### Post by lonewolf454 on 2008-12-24
Thanks.  However, it will only let me enter one command.  I need to sudo modprobe agrmodem and modprobe agrserial BEFORE I sudo wvdial so wvdial will find the agr softmodem.  Is there a way to do all of this in this order?

:KS Thanks again and Happy Holidays.:KS

---

### Post by mikewhatever on 2008-12-24
I think the modules should go into /etc/modules, and the command into /etc/rc.local, and you don't need sudo there. This way, it would work for all users.

---

### Post by lonewolf454 on 2008-12-25
Please explain in more detail what goes where, and if I understand, sudo is not needed in either?  I am still a newb and trying to figure out, much different than windows obviously.  Thx.

---

