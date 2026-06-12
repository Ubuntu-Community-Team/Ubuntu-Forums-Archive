---
title: "connecting to ad hoc network renamed my interfaces"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by jimmybarcelona on 2010-06-04
For the past few days I've found a new ad hoc wireless network called "Free Public Wifi" coming from somewhere in my work building. Some googling has revealed that this is caused by a bug in Windows XP. I knew it didn't belong, so I tried to connect to it hoping to be able to get an IP address from it so I can figure out where it's coming from and hopefully get rid of it. I connect, nothing happens, I disconnect. Next thing I know my wireless network interface has changed from eth1 (as it has always been) to eth0_renamed. Then my wireless won't connect to anything. I did manage to find the offending computer here on our network and shut it down. Once I did that and restarted my computer everything worked fine. My wireless works and my interfaces are back to normal, except for firestarter will not start because "interface eth0_rename" isn't ready.

So now I know that my mistake was even connecting to it in the first place. But I would also like to know what happened? How did connecting to a ad hoc network allow it to change my interface configurations?

---

