---
title: "Wireless Authentication Required for Unsecured Networks"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by slurpee2k5 on 2009-05-27
I'm working for an organization testing a mesh network in a neighborhood. Basically I just connect to the closest node and get signal data. Everything was working fine for a week but out of nowhere whenever I try to connect to the network (which is unsecured and unencrypted) it the Wireless Network Authentication box pops up and says a password or encryption key is required to access the network. In the wireless security field the only option available is 'None' but the 'Connect' button is not able to be clicked. The thing is this only happens when I try to connect to public unsecured networks. If I connect to a private network and enter the appropriate password it connects fine. I have no idea what could be wrong because it was literally working one minute and the next I am unable to connect to any public unsecured network.

Thanks for any help.

---

### Post by smithzvk on 2011-02-07
I know this is old, but it is all I found when trying to fix this same problem under 10.04.

I fixed this like so: I deleted the connection under "Edit connections" by right clicking on the connection icon (nm-applet).  After that I was able to manually select from the detected networks and it connected fine.

---

