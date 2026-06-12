---
title: "Wireless Trouble/Broadcom BCM4318 802.11g"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by lizard08 on 2009-01-17
Hi, I’m having trouble getting my laptop to find wireless networks using Ubuntu. This seems to be a common problem from what I’ve read in other posts, but I’m pretty new to this and I just can’t get it working. Any help would be appreciated. Here is some information I’ve tried to put together… I’m not sure what all of it means but maybe it will help.

I have a Dell Inspiron 2200
Ubuntu version 8.10
Network controller: Broadcom corporation BCM4318 [AirForce One 54g] 802.11g wireless LAN controller

When I put these commands in here is what I’m getting.
Iwconfig:
Lo   no wireless extensions
Eth0    no wireless extensions
Pan0   no wireless extensions
Sudo  lshw –c network:
Network:0 unclaimed
Iwlist scan:
Most say Interface doesn’t support scanning, but wlan0 says no scan results.
Uname –mr:
2.6.27-7-generic i686
Sudo /etc/init.d/networking restart:
Reconfiguring network interfaces…    [ok]
When I search for drivers, it says there are no drivers in use, but I’m pretty sure my wireless card is enabled.
Thanks,
Liz

---

### Post by DarkN00b on 2009-01-17
You need to install the BCM43xx firmware. Your computer can see your card but doesn't have the drivers to talk to it. 

Have a look at [this]("http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm43xx+easy") thread. it should help.

---

### Post by lizard08 on 2009-01-17
Thanks. I'll try this somewhere where I can hook up my computer to the internet using a cord.

---

