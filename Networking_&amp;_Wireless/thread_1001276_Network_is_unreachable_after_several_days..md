---
title: "Network is unreachable after several days."
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by walterbetanc on 2008-12-03
After years of freebsd servers I finally tried Linux and quickly found Ubuntu. I installed Ubuntu Hardy 8.04 server and Xbuntu desktop with Lamp, Postfix and lots of utils. Everything worked great,  a little slow (my hardware)and decided to let run 24/7 as it will be used as sever. I have two virtual domains and several virtual emails installed, all work great. 

On checking the server after three days discovered it was not responding to html or email. Ping the static ip 192.168.0.4 and got response "network is unreachable". After re-booting got the same. Finally tried /sbin/ifup eth0 and network was restored to normal. Did a re-boot and again got "network is unreachable". Did /sbin/ifup eth0 and network ok again. 

Not being a whiz with this system I was hoping to get insight from the forum if anyone has had this happen before or has some suggestions before I start stumbling along to try and find problem. Would really appreciate anyone input.

thanks
Walterbetanc

---

### Post by doas777 on 2008-12-03
once every 3 months or so, my bind server will stop responding to queries, but returns to normal as soon as i ssh/vnc in and run an nslookup. weird huh?

you might wanna look at your nic powermanagment settings. I have no idea how, but I've seen some OSs power down teh nic, if it's idle for too long.

good luck

---

### Post by walterbetanc on 2008-12-04
Thanks for the input,

What really gets me is that the server on re booting 
will not bring up networking, 

but if after booting i do /sbin/ifup eth0
all networking is normal.

thanks
Walterbetanc

---

### Post by Iowan on 2008-12-05
You can check the **/etc/networking/interfaces** file to verify an "auto eth0" line... but I doubt that's the problem. Power management is a possibility.  On some Windows dual-boot systems, the NIC can get locked up unless machine is powered down and back up (not suggesting this is your problem).

---

