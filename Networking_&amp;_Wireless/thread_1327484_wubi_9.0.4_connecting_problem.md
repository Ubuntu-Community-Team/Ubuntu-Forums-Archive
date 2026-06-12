---
title: "wubi 9.0.4 connecting problem"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by sixm on 2009-11-15
hello 
i have a problem getting connected to the internet 
i use a d link dsl-502t router connected via ethernet card to my amd (not laptop). i tryed to create a connection with all informations that the router's software gave to me as dns, ip , gateway, mac address, etc. but i couldn't connect too.
so i deleted all connections and i let wubi choose his default connection called auto ethernet or auto etho but i still couldn't 
get connected. then i tryed to modify those parameters into auto etho (or auto ethernet) with ones inside router's informations but 
i still got that problem.
what can i do to get connected?

---

### Post by U2XS on 2009-11-15
Step (1) Connect cable from your computer to router.  Make SURE that the hardware side is working fine.  Test it in Windows/Mac if you have to.  <-- I actually think that this is the real problem.

Step (2) reboot computer

Step (3) In the Grub (boot) screen, select the second option for diagnostic.  That is to say, not the Ubuntu OS and not memtest86.  I can't remember the name

Step (4) select the option which reconfigures Networking.  There are only about 8 options so it's not hard to find.

Step (5) When finished, continue booting into the OS and enjoy

---

