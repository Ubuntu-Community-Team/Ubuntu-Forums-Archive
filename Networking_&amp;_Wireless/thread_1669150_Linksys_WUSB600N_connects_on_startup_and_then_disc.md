---
title: "Linksys WUSB600N connects on startup and then disconnects"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by chevyboy_0 on 2011-01-17
Hey guys, 

Im having another problem with my wireless in Maverick, Im at my wits end with this thing and dont know what to do next. I followed Dev0's from this thread.

[http://ubuntuforums.org/showthread.php?t=1487397&page=4](http://ubuntuforums.org/showthread.php?t=1487397&page=4)

And now when ever I start my computer I get a notification that says "Linksys C" connected. Then only a few seconds later it says Disconnected and then from then on every few minutes the Password prompt pops up and then I enter my password and then it just keeps going in that cycle until I click cancel. 

I would really appreciate it if anyone could help me with this please.

Thanks 
Andrew

---

### Post by Dev0 on 2011-04-21
The compiling from source method didn't work for me on Maverick either. I was able to get by with by blacklisting method in post #46 for a while.

[http://ubuntuforums.org/showpost.php?p=9882263&postcount=46]("http://ubuntuforums.org/showpost.php?p=9882263&postcount=46")

Installing "linux-backports-modules-compat-wireless-2.6.36-maverick-generic" and its dependent package via Synaptic seems to have helped.

---

