---
title: "USB wireless makes my remote quit working"
date: 2007-11-15
forum: Mythbuntu
---

### Post by bcr821 on 2007-11-15
So i go through about 3 hours of ndiswrapping and banging my head against my computer to finally get the wifi working with the DWL-G132 wireless adapter.  However when i get the wifi working the remote control quits working correctly.

I don't understand what's stopping it from working because if i boot the computer without the wireless adapter the remote works fine.  As soon as i put the wireless adapter in the remote quits working.

When the wifi adapter is plugged in i still get the correct output of irw and my config files are still present.  I tried restarting lirc but that didn't help.  What could be causing this issue?

---

### Post by superm1 on 2007-11-15
Well what remote?  What driver did you end up having to use?

---

### Post by bcr821 on 2007-11-15
> **superm1 said:**
> Well what remote?  What driver did you end up having to use?

I'm using the Haupanauge PVR-150 remote which was working flawlessly.  The wireless adapter was the DWL-G132 from D-Link and i used the most recent XP drivers and "wrapped" them (wireless adapter drivers) with ndiswrapper

---

### Post by superm1 on 2007-11-15
That has to be one of the most bzr things i've heard.  Using the lirc_pvr150 module or the lirc_i2c module?  You can consider trying to switch among the two.

---

