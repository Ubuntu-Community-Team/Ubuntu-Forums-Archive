---
title: "Ubuntu 9.10: Broadcom 4318 wireless problem on Dell notebook"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by hofstra14 on 2009-11-05
Did a clean 9.10 install on an old Dell Inspiron 600m notebook that uses a Broadcom 4318 wireless card.  This had worked fine under 9.04 with ndiswrapper and the bcmwl5 drivers.  I did the following;
 
[LIST=1]
[*]Installed ndisGTK
[*]copied the bcmwl5.sys and bcmwl5.inf files
[*]Installed the drivers through ndisGTK
[*]blacklisted the bcm43xx drivers in /etc/ndiswrapper/blacklist.conf
[/LIST]And, nothing.  If I run iwconfig the wlan0 interface is listed.  
 
If I then rmmod b43, b44, ssb and ndiswrapper and then reinsert ndiswrapper and b44 the interface comes up, creates an auto entry in the wireless networks list, discovers my wireless network (secured with WPA2), asks me for the key but does not connect.
 
What am I missing?
Ideas?
 
Thanks in advance

---

### Post by Ceadda on 2009-11-09
bump

---

### Post by curtHendzell on 2009-11-14
I believe the blacklist file is /etc/modprobe.d/blacklist. You might also try adding "ndiswrapper" to /etc/modules.

---

### Post by PRC09 on 2009-11-14
Maybe these will help,different models but broadcom from dell...

[http://ubuntuforums.org/showthread.php?t=1318870](http://ubuntuforums.org/showthread.php?t=1318870)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[http://ubuntuforums.org/showthread.php?t=931178&highlight=dell+d600](http://ubuntuforums.org/showthread.php?t=931178&highlight=dell+d600)

---

