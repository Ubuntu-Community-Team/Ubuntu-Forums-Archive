---
title: "Network Interface/Internet Problems"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by tamu70 on 2006-03-08
I initially loaded Ubuntu 5.10 as a dual boot with Windows XP using my PATA hd and everything worked fine.  Since then I have installed a SATA hd and once again I am dual booting with XP.  Now I can't get an internet connection with Ubuntu (Windows internet connect OK).  The Network Interface Configuration takes almost one minute during the Ubuntu boot up and then I am unable to get any internet connection once I log in.  Does anyone have any solutions, recommendations, or thoughts?  It would be greatly appreciated.

---

### Post by ivoencarnacao on 2006-03-08
[QUOTE=tamu70]I initially loaded Ubuntu 5.10 as a dual boot with Windows XP using my PATA hd and everything worked fine.  Since then I have installed a SATA hd and once again I am dual booting with XP.  Now I can't get an internet connection with Ubuntu (Windows internet connect OK).  The Network Interface Configuration takes almost one minute during the Ubuntu boot up and then I am unable to get any internet connection once I log in.  Does anyone have any solutions, recommendations, or thoughts?  It would be greatly appreciated.[/QUOTE]
Have you tried to go to your System>Administration>Network and check if everything is OK?

---

### Post by randomnote1 on 2006-03-08
well, assuming that Ubuntu has recognized your ethernet card correctly, try opening a terminal and use 

sudo ifdown -v eth0
sudo ifup -v eth0

the first line should disconnect you from the network and the second you will be able to see if it actually obtains an IP address when connecting to the DHCP server.  Give that a try and let me know how that works out for ya.

---

