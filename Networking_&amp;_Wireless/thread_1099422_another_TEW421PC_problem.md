---
title: "another TEW421PC problem"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by jberkery on 2009-03-18
I installed Ubuntu 8.10 on an old laptop that only had a pcmcia wireless card, Trendnet TEW-421PC and followed the instructions at:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I installed the latest ndiswrapper v1.54 and the latest drivers from the vendor (net8185). Ndiswrapper does see the driver and the network icon shows my router name with a decent power level, iwconfig reports that wlan0 is looking at that router ESSID. I disabled wep/wpa on the router to make it even easier.

When I try to connect, all I get is "The network connection has been disconnected." I've tried both the winxp and win2000 drivers. Does anyone have any other tricks for getting this to work?

---

### Post by jberkery on 2009-03-19
Hold on now. I'll answer my own question. I used the WIN98 driver and it made the connection. Why it is happy with an archaic one and not more recent WINXP or WIN2000 drivers I don't know and don't especially care as long as it works.

---

### Post by jberkery on 2009-03-21
Nope, not working well though. It's intermittent. This is beyond annoying. Sometimes it connects fine but most of the time it simply won't connect at all. I'm in the same room as the router, so it's not a signal level problem.

---

### Post by jberkery on 2009-03-22
I'm nothing if not persistent. I may have gotten it working. Only time will tell. At least it came back up twice after a reboot, which is something it hasn't done before.

What I did this time, was blacklist one other driver in addition to these items from section 3.1 of:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Configuring%20Wireless%20Network%20Settings%20using%20command%20line](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Configuring%20Wireless%20Network%20Settings%20using%20command%20line)

"edit the /etc/modprobe.d/blacklist file and add blacklist bcm43xx, blacklist b43, blacklist b43legacy and blacklist ssb to the end of the file.) Note: This only effects what is loaded at startup, so you will have to reboot to have the bcm43xx drivers disabled."

I added rtl8180 to the blacklist. I think it was using 8180 by default instead of the WIN98/net8185.inf I told ndiswrapper to install.

Here's a few extra words, for the sake of search engines: 
Trendnet TEW-421PC wireless NET8185 net8185.inf tew421 tew 421pc pcmcia

---

