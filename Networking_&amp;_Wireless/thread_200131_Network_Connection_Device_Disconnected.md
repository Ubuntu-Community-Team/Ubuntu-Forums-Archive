---
title: "Network Connection Device Disconnected"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by dizbah on 2006-06-19
All,

I need help please.  My network wireless device (eth1) continues to show disconnected.  I tried activating, deactivating, rebooting ect and no matter what I do it shows disconnected and I cannot use it.  My wired connection is ok.  When I use Knetwork manager to connect to any wireless network it gets stuck at 28% (configuring device).  I am currently using a dell laptop with a broadcom wireless card.  Any advise would be greatly appreciated. ](*,)

---

### Post by dizbah on 2006-06-19
anyone have an idea on this?  I really want to get ubuntu going full time!

---

### Post by skelooth on 2006-06-19
i want to know too.... only I already have ubuntu going full time :(

---

### Post by jennie on 2006-06-22
I was having the same problem.  After upgrading to dapper my wireless changed from wlan0 to eth1.

I tried a lot of different things, but I think what finally worked was blacklisting my default driver (temporarily removing it didn't seem to work).  After restarting, my wireless was back to wlan0, then I just had to configure as usual. (I had already installed the proper drivers with ndiswrapper)  You can also check the ndiswrapper file in etc/modprobe.d

This thread helped me... [http://ubuntuforums.org/showthread.php?t=197195](http://ubuntuforums.org/showthread.php?t=197195)

Good luck.

---

