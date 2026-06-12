---
title: "FRITZ! W-Lan USB Stick &amp; Ndiswrapper issue"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by JugglinPhil on 2011-01-16
I installed Ubuntu 10.04 alongside Windows 7 on a non-laptop pc using wubi. The pc uses the FRITZ! Wlan USB stick to connect to the internet in windows, which does not work under Ubuntu.
So I installed ndiswrapper and ndisgtk and set up the drivers for the stick (from the cd that came with the stick), and everything seems fine: ndisgtk says that hardware and driver are present, and so does ndiswrapper -l. 
I followed the tutorial in the official wiki ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)), however after step 3.5 I can not go on any further - nm-applet can not find the wireless network.
Also, the commands ifconfig and iwconfig show that there is no wireless connection, wlan0 is not listed.
How can I go on from here to get the wireless working?

---

### Post by bcbc on 2011-01-16
If you use ndisgtk you don't have to do any manual install from the command line. Just go to System, Admin, Windows wireless drivers, install the XP driver (.inf) file and wait a few seconds, and then network manager should see the connections.

---

### Post by JugglinPhil on 2011-01-17
I've done both, first command line only since I prefer it over gui, and after it did not work I uninstalled it and tried it with gui with the same result.
However I got some new idea, the installed version is 64 and the driver was for 32, so now I got the right driver and I'll see if that works in a minute.

---

### Post by JugglinPhil on 2011-01-17
Alright that was it, worked fine with the correct driver. :)

---

### Post by bcbc on 2011-01-18
> **JugglinPhil said:**
> Alright that was it, worked fine with the correct driver. :)

Good to hear!

---

