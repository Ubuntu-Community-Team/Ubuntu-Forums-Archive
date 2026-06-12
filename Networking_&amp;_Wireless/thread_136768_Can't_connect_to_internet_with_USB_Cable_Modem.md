---
title: "Can't connect to internet with USB Cable Modem"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by x-ph on 2006-02-26
The situation is rather confusing. When I put Ubuntu 5.10 Live CD and open Networking there is eth0 and eth1 devices. eth0 is not active (and it should be) and eth1 (the usb cable modem) is active and configured with DHCP. The internet is working just fine. 
But when I install the Ubuntu on my PC and open Networing there is only eth0 device. How can I add my usb cable modem as eth1 so that I can connect to the internet? Thanks in advance.

---

### Post by pestilence4hr on 2006-02-26
Figure out what module you need for the cable modem, then modprobe it.  In the live cd, you can see what modules are loaded with "lsmod"

---

### Post by x-ph on 2006-02-27
Thanks, I'll try to find the module. After that I just type "modprobe <module>" or need to do something else? I'm sorry for the stupid questions but I'm not familiar with the console stuff.

---

### Post by pestilence4hr on 2006-03-03
Essentially, yes.  You will probably need a "sudo" in front of that as well (to give yourself superuser priveleges).

---

