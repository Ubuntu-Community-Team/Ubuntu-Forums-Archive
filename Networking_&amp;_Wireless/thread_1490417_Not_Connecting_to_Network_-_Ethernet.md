---
title: "Not Connecting to Network - Ethernet"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by Schema456 on 2010-05-22
Ok, first of all, hi to everyone again. This is what happens, basically one day i was using my laptop normally, doing everything i usually do. Turned off. Next day after coming from college my computer was not connecting to the internet. I checked everything and i realized that the out of the 2 led lights that turn on when you plug in the thernet cable to the laptop only the green one is on, the yellowrange one that blinks out of activit is not on. This kind of tells me that it is making contact. At first i thought that my network port was damaged, but a while ago it worked... i got into the internet and then after that i had to restart my computer and it was not connecting again... so i think the port is working as well as the ethernet cable... can somebody help me with this?

---

### Post by Iowan on 2010-05-22
Any recent updates? Sometimes they break more than they fix (hopefully not often...). From a terminal (Applications>Accessories>Terminal) check 
**ifconfig -a** - it will probably confirm no IP address. **sudo lshw -C network** should provide more information about your interface(s).

[Here]("http://ubuntuforums.org/showthread.php?p=9341723#post9341723") is a similar thread...

---

### Post by Bucky Ball on 2010-05-22
+1. Also, what release of Ubuntu are you using?

---

