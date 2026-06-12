---
title: "How to OPEN a Port in Ubuntu for VirtualBox OSE"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Habboblob on 2010-03-13
Hello Ubuntu Users, I am very new to Ubuntu and am needing to open a port in ubuntu, then use it for my VirtualBox Pc.

My VirtualBox is running -  Windows XP
I have a router connected to my network - Linksys WRT54G

Now lets begin, I have tried opening via there router homepage.


But when I go to [http://canyouseeme.org](http://canyouseeme.org) and test port 4900 is still says that it is closed.

Can anyone please help me out with noob friendly steps.
Thanks, bye for now.

---

### Post by soc200 on 2010-03-13
Are you sure the IP address of your computer is 192.168.2.100?  If you are unsure, look under status or administration of your router settings to see what ip address the router assigned you.  If the IP is correct, the port should be open.  I had the same thing happen today with Transmission BitTorrent...after I "saved" the settings in the router...i had to reboot...check to make sure the port was still opened...and only then did it pass the check.  

You have the same router I do btw.

---

### Post by Habboblob on 2010-03-15
Firstly, how do I find out my network IP Address?

---

### Post by aeiah on 2010-03-17
in windows use the command:
```
ipconfig
```

in linux:
```
ifconfig
```

---

