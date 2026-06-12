---
title: "bcm43xx tip"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by LazyBoy on 2006-06-24
Wireless card not working?  Are there messages in /var/log/syslog referencing "bcm43xx"?  This tip may be for you.


I was already running knetworkmanager, which said it saw my card but I couldn't connect to my network.  This was in the log:

> Jun 24 09:08:55 spaceghost kernel: [17181002.644000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load failed.
Jun 24 09:11:00 spaceghost firmware_helper[6360]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:03:00.0' with driver 'bcm43xx'

This means that the OS found a driver, but it doesn't have the firmware. You do not need ndiswrapper!!

I did the extraction [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#head-34d552a556ad5be07dbae4bafb73a6125139c9d8") (***just*** section 1.2.2.1) and it came right up! knetworkmanager was trying every two minutes and generating those log messages. Next time around, it worked.

LB

---

