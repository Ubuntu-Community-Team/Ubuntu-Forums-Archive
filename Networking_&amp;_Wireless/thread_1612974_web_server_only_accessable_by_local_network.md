---
title: "web server only accessable by local network"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by derrabe on 2010-11-03
I just setup a ubuntu 10.10 box learn linux and to play around with, and want it  to host my website.  I can see the web site on my local network no  problem but the outside world gets a time out message.  I check to make  sure everything is forwarded correctly on my router and the dns so i has  to be something in ubuntu blocking out-of-network traffic how do i turn port 80 on to  the outside world

---

### Post by SeijiSensei on 2010-11-03
Some ISPs block inbound port 80.  What are the terms of service of your Internet connection?  Are you allowed to run a web server?

Try forwarding a non-standard port on the router to port 80 on the web server, then use [http://www.example.com:12345/](http://www.example.com:12345/) if you've forwarded port 12345 to the server's port 80.  If that works, but 80 doesn't, you're probably being blocked.

---

### Post by derrabe on 2010-11-04
It is definitely not my isp i have been running a windows apache server on port 80 for the last 2 years.  The ubuntu box replaced the windows box yesterday.  It has the same ip as my previous windows box that was working.  The only addition software I installed was moblock and samba so far never used moblock is it possible that it is blocking inbound connections from out side the network and if so how do i tell it to allow 80

---

### Post by SeijiSensei on 2010-11-04
Given its [description](http://moblock.berlios.de/) it's certainly possible that moblock is the culprit.  It looks like it mucks with iptables rules.

Why not simply remove it from the machine for now and see if the problem disappears?

If that doesn't help, show us the results of "sudo iptables -L -nv".

---

### Post by jre on 2010-11-06
> **derrabe said:**
> The only addition software I installed was moblock and samba so far never used moblock is it possible that it is blocking inbound connections from out side the network and if so how do i tell it to allow 80

Certainly moblock. Have a look at [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) and [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) and know why you install software!

Just set WHITE_TCP_IN="80" in /etc/blockocntrol/blockcontrol.conf and do a "sudo blockcontrol restart".

---

