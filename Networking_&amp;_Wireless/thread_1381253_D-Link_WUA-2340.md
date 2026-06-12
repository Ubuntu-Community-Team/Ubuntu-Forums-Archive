---
title: "D-Link WUA-2340"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by Colinchocolate on 2010-01-14
I've checked the wiki and this wireless card isn't supported. Is it possible for someone to write a driver for it? I have the windows driver if it is needed.

---

### Post by bkratz on 2010-01-14
If you have the windows drivers available you might want to look into ndiswrapper, which will use the .inf and .sys files from the disk.


See the first "sticky" at the top of the page

---

### Post by Colinchocolate on 2010-01-14
**D-Link WUA-1340**

                      **From ndiswrapper**

                                                                           ** D-Link WUA-1340(USB)**

 
[LIST]
[*] Chipset:  Ralink RT73 (RT2571W)
[*] usbid:  07d1:3c04
[*] Windows Driver: The newest driver, 3.0, for the [D-Link DWL-G122 rev C1]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=D-Link_DWL-G122_rev_C1") can be used since the definition for both is in there.
[/LIST]
 ** Info**

 
[LIST]
[*] Native linux driver: Download from rt73module , and rt73firmware. I built the module under Fedora Core 5, kernel 2.6.16.20, and gcc 4.1.0.
[/LIST]
 A header file must be modified as shown in the [D-Link DWL-G122 rev C1]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=D-Link_DWL-G122_rev_C1") as stated in the section below for it. Also compiling with gcc 4.1.0 led to errors due the typecasting of a variable pass to NdisAcquireSpinLock as an unsigned long. I traced the function back to it's origins, local_irq_save, which does not appear to check for the presence of an unsigned long. This led to compilation errors. I removed all invalid typecasts and the module compiled with minor warnings. I followed the rest of the instructions in the readme file and the driver now works great with WPAPSK TKIP enabled. 
Before I was able to get the native driver to compile I used ndiswrapper with the windows drivers and was able to connect to my wireless network using WPAPSK TKIP with the help of wpa_supplicant. I had no problems with this, but I prefer to use native drivers where I can. 



[FONT=Comic Sans MS][SIZE=4]Curious, will this work with the 2340 instead of the 1340?[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=4]Also, I can't tell which header file needs modification, and what to modify![/SIZE][/FONT]

---

### Post by changingstate on 2010-01-14
No. Read this, it describes how to get it working. [http://ubuntuforums.org/showthread.php?t=861855](http://ubuntuforums.org/showthread.php?t=861855)

---

### Post by Colinchocolate on 2010-01-14
Thanks!

---

