---
title: "infinite loop in network manager log prevents connecting to one wap"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by teryret on 2010-08-14
Hello all,

I'm working on a buddy's machine (helping him make the switch) and he has two wireless networks (long story), one from a Linksys WRT300N, and one from some art-deco looking Belkin (can't remember the model number).  I'm connecting from a Linksys WUSB300N running via ndiswrapper in 10.04.

The two networks are Truk (the broken one, on the Belkin) and Gaucho (the working one), and both of them work in Windows/Android/iPhone.  The problem is that when I try to connect to truk it will struggle for a while, time out and then revert to the default connection of Gaucho (which has an appreciably worse signal).

To trouble shoot it I ran "tail -f /var/log/daemon.log | grep NetworkManager > Desktop/netlog" and then attempted to switch from Gaucho to Truk.  I've attached the generated log file.  Starting on line 57 there is an infinite loop when it tries to run DHCP, but the question is why would that happen, and how can it be fixed?  My next step is going to be connecting a hard line and logging into the router to reset its DHCP cache, but I'd like to see if anyone here has any ideas.

Edit:  DHCP flush didn't work, and switching it to WAP only (ie moving the dhcp and routing responsibilities to Gaucho's router) didn't either, I'm quickly running out of ideas.

---

