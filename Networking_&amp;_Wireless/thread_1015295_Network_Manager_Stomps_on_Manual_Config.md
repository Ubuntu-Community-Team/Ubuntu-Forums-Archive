---
title: "Network Manager Stomps on Manual Config"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by russlar on 2008-12-18
After updating network manager last night, I am unable to set a static IP. I am setting the IP using ifconfig. Immeadiately after I set the static, network manager takes over and reacquires a DHCP address. wtf!!!???

Also, network manager resets the MTU (maximum packet size) to 576, as opposed to the ethernet standard of 1500. Again, this is in spite of manual configs at the command line. wtf!!!???

---

### Post by Iowan on 2008-12-18
[Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for a static address bug in NM.

---

### Post by russlar on 2008-12-18
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround for a static address bug in NM.

Great suggestion if you _always_ want to have a static IP. On a laptop, this is simply not practical.

what I'd really like to do is downgrade to the previous version of knetworkmanager (prior to the npvember 29 update). that release worked fine, and only managed the network interfaces when I told it to.

---

### Post by kevdog on 2008-12-18
There are plenty of solutions for this problem -- but if you want a GUII --- install WICD -- NWM is full of bugs.

---

