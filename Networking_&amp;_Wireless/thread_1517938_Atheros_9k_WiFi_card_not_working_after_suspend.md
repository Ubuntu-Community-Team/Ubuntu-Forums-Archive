---
title: "Atheros 9k WiFi card not working after suspend"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by rprice on 2010-06-25
Hello-
I am a beginner with Linux.  I am currently using Ubuntu 10.04 Lucid Lynx.  Although it has worked fine for the past couple of weeks, I have recently encountered a problem with my wireless card.  It is an Atheros AR928X card on a Toshiba satellite U405D-S2874 model laptop.  Recently, I attempted to put the computer into suspend mode for the first time.  The computer failed to wake up, and I performed a hard reboot.  After this, everything seems to work *except for the wireless card*.  I am now unable to connect to any wireless network with my laptop, and the wireless manager doesn't seem to be working either.  Any help would be greatly appreciated.  :confused:

---

### Post by rprice on 2010-06-28
I've been unable to fix this problem, or find help for it.  Due to its rather serious nature, I'm going to have to reinstall vista.  :(

---

### Post by mentar on 2011-05-31
Sorry to hear that it didn't work for you and that no-one managed to answer your question.
It's probably a driver issue, to start troubleshooting you should go into a terminal (Ctrl + T) and run **dmesg** and lookout for lines with **ath** there may be something of help there, I had a similar problem and mine says **ath: Failed to wake up in 500us**
Probably a bit late, but hope it helps others.

---

