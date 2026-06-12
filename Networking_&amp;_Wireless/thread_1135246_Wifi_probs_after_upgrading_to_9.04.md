---
title: "Wifi probs after upgrading to 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by T4tav on 2009-04-24
Hi all, I have an acer 1360 laptop that was running 8.10 without any problem with the wifi driver working through the NDISwrapper app.

I upgraded to 9.04, when I set it to upgrade I turned my wifi off cause it was slow.

Earlier this morning I completed the upgrade to 9.04, however, now my wifi doesnt work. I have to use eth0 :(

When I go to System > Administration > Windows Wireless driver. And click on that, I get a Unable to see if hardware is present error.

So I ran sudo modprobe ndiswrapper

And I got the following 

tavis@acer:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


I also tried ndiswrapper -l and got this ...

tavis@acer:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
neti2220 : driver installed
	device (17FE:2220) present


I can't work out whats wrong :(

Help, I dont like wires :(


EDIT !!!!!!!

I have renamed  /etc/modprobe.d/ndiswrapper  to  /etc/modprobe.d/ndiswrapper.conf and now I get this ....

tavis@acer:~$ ndiswrapper -l
neti2220 : driver installed
	device (17FE:2220) present


sudo modprobe ndiswrapper 
Gives me nothing now :S

and lspci
00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

Just looked, i can see all the wifi networks using wifi radar. But ubuntus wifi icon says wireless is disabled still

---

### Post by T4tav on 2009-04-24
Edit :

Sorry for double but my first post is getting long.

I have tried uninstalling NDIS and reinstalling it , as well as the new version. I am not lost at what to do

---

### Post by arbutwarrif on 2009-04-24
clicked in error - ignore, sorry

---

