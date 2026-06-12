---
title: "[SOLVED] Looks like you can't use a static IP anymore? This is crazy."
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by xmrkite on 2008-12-19
Hello. The new network manager looks nice, but doesn't seem to work. I'm trying to use a static IP on an install i just finished 5 minutes ago. Here's what I'm doing:

Right click on the networking icon at the top

Click on Edit Connections. 

Double click on Auto eth0. 

Click on the IPv4 Settings window on the window that pops up. Change method to Manual,

Enter in the IP, the Netmask and the Gateway. Then enter in the DNS Server. I'm sure this info is correct. I've done it to all our windows computers at the office.

Then click OK. (Connect Automatically and System Setting are both checked up at the top)

Open terminal and type in ifconfig eth0 and everything looks great. Can't get online. So i switch it to dhcp and it works just fine.

Can't ping or anything. All the other computers have the exact same settings except for the IP address, and they all work great.

Any ideas? BTW, this is all the same settings that i've used in previous versions of ubuntu and have never ever had a problem getting it to work.

Is this a major bug? I can't imagine i'm the only one who uses static ip's.

-Thanks

---

### Post by jonobr on 2008-12-19
[http://ubuntuforums.org/showthread.php?t=1011034](http://ubuntuforums.org/showthread.php?t=1011034)

---

### Post by xmrkite on 2008-12-19
Problem with that is that the dhcp server i used was only a temporary one i setup on my local computer. We don't have dhcp at the office. All the computers use static ip's.

---

### Post by xmrkite on 2008-12-19
OK, figured it out. For anyone else who runs into this bug, and it is a bug because i even did a reinstall and it still doesn't work....

You need to delete the auto eth0 connection and create a new one. The new connection will work, but you must remember the mac address and input it in that new connection.

---

### Post by Iowan on 2008-12-19
Looks like I'm about an hour late (busy clearing ice/snow)...
[Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for static IP's.  Dunno if it mentioned the way you did it, or if I saw that in a different thread. Congrats! Mark this one [SOLVED] (Under Thread Tools).

---

### Post by qwertyu on 2008-12-30
It's incredible how Ubuntu pretends to be a serious Software with this class of big bugs still around for ages and it seems they don't plan to release a fix.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284298](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284298)


The best thing to solve it is to add the latest Network Manager from

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

---

