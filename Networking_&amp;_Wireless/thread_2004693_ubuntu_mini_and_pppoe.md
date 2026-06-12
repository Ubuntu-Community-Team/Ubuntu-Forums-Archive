---
title: "ubuntu mini and pppoe"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by amusis on 2012-06-16
ok, problem : i want to install ubuntu mini on an old pc but i have a pppoe connection.
i have try 2 road:
1- pppoeconf: but i have this problem[FONT=monospace]
[/FONT]```
/usr/sbin/pppoeconf : line 523: can't create tmp.xxxxxxxxx: nonexistent directory 
cat: can't open 'tmp.xxxxxxx/tmp.yyyyyy' : no such file or directory
```2- pon provider: but i cannot ping google or other
```
un 16 11:50:39 kernel: [  589.749787] NET: Registered protocol family 24 
Jun 16 11:51:01 pppd[2665]: Plugin rp-pppoe.so loaded. 
Jun 16 11:51:01 pppd[2667]: pppd 2.4.5 started by root, uid 0 
Jun 16 11:51:02 pppd[2667]: PPP session is 5670 
Jun 16 11:51:02 pppd[2667]: Connected to 00:19:55:31:e5:48 via interface eth0 
Jun 16 11:51:02 pppd[2667]: Using interface ppp0 
Jun 16 11:51:02 pppd[2667]: Connect: ppp0 <--> eth0 
Jun 16 11:51:02 net/hw-detect.hotplug: Detected hotpluggable network interface ppp0 
Jun 16 11:51:02 pppd[2667]: PAP authentication succeeded 
Jun 16 11:51:02 pppd[2667]: peer from calling number 00:19:55:31:E5:48 authorized 
Jun 16 11:51:02 pppd[2667]: not replacing existing default route via 192.168.1.1 
Jun 16 11:51:02 pppd[2667]: local  IP address 79.42.102.221 
Jun 16 11:51:02 pppd[2667]: remote IP address 192.168.100.1 
Jun 16 11:51:02 pppd[2667]: primary   DNS address 85.37.17.50 
Jun 16 11:51:02 pppd[2667]: secondary DNS address 85.38.28.76
```I have added packages 1 by 1 to have pppoe and pon work, maybe i miss 1 or 2 packages.
so i ask 1- what is this error? and 2- if it say i am connected why i can ping out(i can ping router and other pc in lan)?
tnx

---

### Post by amusis on 2012-06-16
ok, i have added other packages and i don't know why but i can ping google now.
but i have now a new problem
```
wget : cannot connect to remote host (1.1.1.1:80) : connection timed out
```
what i don't understand is why "1.1.1.1"? how can i change it with the right ip?

---

### Post by amusis on 2012-06-18
here how you can install ubuntu mini with a pppoe connection

[http://kaliffo.livejournal.com/3360.html](http://kaliffo.livejournal.com/3360.html)

there are, maybe, errors but for me it works.

---

