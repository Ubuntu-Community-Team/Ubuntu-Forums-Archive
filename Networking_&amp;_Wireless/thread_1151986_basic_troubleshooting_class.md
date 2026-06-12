---
title: "basic troubleshooting class"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by dec7m2 on 2009-05-07
i have an assignment for basic troubleshooting where i have been given a zonet zew1602 wireless pci adapter and i have to install the drivers
but here is the problem i am the only one in my class using linux the rest are using xp.

i have no cd
i have to install the drivers for them
and i don't know how to install drivers

---

### Post by bkratz on 2009-05-07
Here is a link for the drivers:  [http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/Zonet-ZEW1602-Driver.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/Zonet-ZEW1602-Driver.shtml) 

You are in luck they have the sys and inf files in the xp package and you will able to follow the excellent ndiswrapper document above.

---

### Post by dec7m2 on 2009-05-08
i have the driver now but when i type in
"sudo ndiswrapper -i netmw125.inf"
it says 
Couldn't open netmw125.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

and i have been tyring to fallow this thread
[http://ubuntuforums.org/showthread.php?t=403139&highlight=zew1602](http://ubuntuforums.org/showthread.php?t=403139&highlight=zew1602)

---

