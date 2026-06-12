---
title: "{ubuntu 9.04} Need help with wireless card"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by windowsh8tor on 2009-06-24
I am currrently using a Netopia 802.11b USB wireless adapter to connect to the internet. However, I swapped to Ubuntu 9.04 (sweet!!!!!) it was not recognized. When I plug the card into the computer (USB port -yes the usb port works-) the "active" light continuosly blinks, and nothing else. If there is any way to re-program / activate it I would be very appreciative. There is no other online tutorials on how to work with it.
 
-thanks in advance.

---

### Post by DiegoTc on 2009-06-24
Hi 
you should do on terminal this command.
[PHP]
sudo lshw -C network[/PHP]

And you should paste all the information it gives.
This is to check if you computer does recognize your usb wifi

---

### Post by windowsh8tor on 2009-06-24
tried it in terminal and it said that there was a unrecognizable command??? 
 
-sorry I'm new to linux. haha been on XP forever, know how to do anything on xp, different story with linux.
 
EDIT: forgot "sudo" will try again. *smacks head*

---

### Post by windowsh8tor on 2009-06-24
sweet, heres the results. thanks a lot man
 
```
 
*-network                      description: Ethernet interface       product: 82562EZ 10/100 Ethernet Controller       vendor: Intel Corporation       physical id: 8       bus info: pci@0000:01:08.0       logical name: eth0       version: 02       serial: 00:13:20:ad:ee:7c       size: 10MB/s       capacity: 100MB/s       width: 32 bits       clock: 33MHz       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s  *-network DISABLED       description: Ethernet interface       physical id: 1       logical name: pan0       serial: 7e:6d:93:33:61:6a       capabilities: ethernet physical       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by DiegoTc on 2009-06-24
Well its first time I know about this wifi card.
It  will sound strange but probably no.

Go to Systems---Administration----Hardware Control and  see if there is a driver for your wifi card. If not I am lost also :S

---

### Post by windowsh8tor on 2009-06-25
crap...nothing there. (insalled linux to a blank 80GB hard drive)

---

