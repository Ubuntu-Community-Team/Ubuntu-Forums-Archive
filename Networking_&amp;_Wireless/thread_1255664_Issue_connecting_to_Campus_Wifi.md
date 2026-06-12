---
title: "Issue connecting to Campus Wifi"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2009-09-01
So I have never had any issues with the Ubuntu network manager before but today I started at a new school and for some reason I am unable to connect to any of their public wifi (un-secure) access points. It starts to connect but hangs when it is trying to obtain an IP address. I loaded up the nm-applet via terminal to see if it threw any sort f error message but none was given when it fails to connect. At the moment I am connected via my 3g device (which works alright) but I would much prefer to get on the wifi. I also have the "Wifi Radar" application installed and it fails to connect to the network(s) as well.

Any suggestions on things I get do to debug the issue/get it to work would be wonderful.

Thanks,
~Jeff

---

### Post by beastrace91 on 2009-10-13
Hey all - if anyone else has a similar issue it ended up being that network manager was having issues connecting to a network that contained so many repeaters (common in schools and other places that have wifi over large areas). When I upgraded to Ubuntu 9.10 (and thus Gnome 2.28 and newer networkmanager) the issue was resolved.

~Jeff

---

### Post by zkriesse on 2009-10-13
Since you figured out what your problem was I won't post an answer but Kudos to you for posting on how to fix such a problem!

---

