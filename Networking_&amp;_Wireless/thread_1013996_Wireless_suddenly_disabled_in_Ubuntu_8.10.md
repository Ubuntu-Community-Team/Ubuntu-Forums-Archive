---
title: "Wireless suddenly disabled in Ubuntu 8.10"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by Dantes1976 on 2008-12-17
Hey, sorry for intruding in this thread but I have a related/similar question. Yesterday I installed Ubuntu 8.10 on my Fujitsu Siemens Amilo Pro V3505, over the pre-existing Vista installation (and format of whole hd). The wireless internet worked perfectly until when I first started it up today, when both the wireless (it says it's disabled and I can't re-enable it) and the wifi on/off button and led light wouldn't work anymore. My wifi card is an internal Intel PRO/Wireless 3945ABG [Golan] Network Connection (rev 02). How do I fix this?

Lshw result:
> 
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 76:93:b6:88:c7:51
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I already tried this but it didn't work:

> 
sudo modprobe -r wl iwl3945
sudo modprobe iwl3945
sudo /etc/init.d/networking restart


---

### Post by PinkFloyd102489 on 2008-12-17
According to your lshw output, the wireless interface isnt even on. Check the switch?

---

### Post by Dantes1976 on 2008-12-17
If you mean the enable Wireless selection, it's grayed out, I can't re-enable it. Else I don't know what you mean, I'm new to Ubuntu.

---

### Post by Dantes1976 on 2008-12-18
The wireless switch and led also don't work anymore since yesterday, as I stated in my first post.

---

