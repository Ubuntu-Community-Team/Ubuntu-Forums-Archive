---
title: "USB Modeswitch uninstallable?"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by iamleaf on 2010-08-08
My make install command does not seem to be able to install anything. It gives error, even if I want to install the lsusb package. 

error for modeswitch: dereferencing pointer to incomplete type
and so on and so forth

error for lsusb: permission denied

please help. I just want to log online, I can't even do that. to be honest ubuntu is quite useless without the internet.


when i downloaded the .deb package and tried installing, the error message was as follows:

Error: Dependency is not satisfiable: usb-modeswitch-data (>=20100127

So what do I do?

---

### Post by alexfish on 2010-08-08
hi

are you just installing usb modeswitch and the data or are you installing other software that depends on them

you will have to install when installing modeswitch

[usb-modeswitch-data]("http://packages.debian.org/sid/usb-modeswitch-data")  (>= 20100127) [not m68k]

can also have a look here

[How To : Mobile Broadband Connections [ Ubuntu 10.04 :  9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

---

