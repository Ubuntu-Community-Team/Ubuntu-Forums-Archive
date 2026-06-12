---
title: "D-Link Wireless 802.11g"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by sokerjunky on 2011-07-25
Hey guys, 
I'm trying to set up the wireless internet back at my cousins house. I tried just plugging the router in and running the installation disk but it didnt work. Any ideas on what I should do guys. His house  lives off of wireless internet. Any help would be appreciated. The router is a DWL-2100 AP
[B]
[/B]

---

### Post by bkratz on 2011-07-25
> **sokerjunky said:**
> Hey guys, 
I'm trying to set up the wireless internet back at my cousins house. I tried just plugging the router in and running the installation disk but it didnt work. Any ideas on what I should do guys. His house  lives off of wireless internet. Any help would be appreciated. The router is a DWL-2100 AP
[B]
[/B]

The important thing is the wireless device. If you go to the terminal and copy/paste the output of the following commands, someone will probably know where to start. Also, here is the type of information you may be requested to provide.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)


The important command is 

```
lspci -nn
```

that is LSPCI in lowercase, if this is a usb card post

lsusb

---

