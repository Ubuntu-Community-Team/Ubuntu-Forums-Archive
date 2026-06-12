---
title: "Networkmanager removing dns entries when wireless is connected"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by sagarpinninti on 2009-11-05
Dear Members,

**The following is my scenario and issue **:


I am using Ubuntu 9.10
I am having wireless and wired connections in my office ,

Wired network having 
staticip :192.168.0.15 in  "/etc/network/interface" 
DNS entries in "/etc/resolv.conf "

For wireless ip is issued by dhcp 

But when iam enabling wireless ,"**networkmanager**" is acting and removing DNS entries in /etc/resolv.conf 
 
Again if i want use wired connection i have to manually provide DNS entries then only i could able to connect to internet.

I installed chkconfig using apt-get and stopped network-manger service , but still the problem continues .

So how to solve this issue ?.

Thanks&Regards,
Sagar.Pinninti

---

### Post by Iowan on 2009-11-05
Somewhere around here is a thread that explains how to disable NM on startup.  I'll need to search for it.

---

