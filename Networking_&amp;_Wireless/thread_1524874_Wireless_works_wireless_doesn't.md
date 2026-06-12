---
title: "Wireless works/ wireless doesn't"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by Murdoc_of_puts on 2010-07-05
so what do I do if this doesn't work?  Does any one know of bad broadcom drivers or something else that might cause this to go poop. I'm using 10.4 Networking is enabled in network manager, and the bios, and the wired network still works.  However it says that wireless is not enabled, and the lshw shows it as *=network DISABLED.Any help would be appreciated.

---

### Post by Iowan on 2010-07-05
Moved to a new thread from [here.]("http://ubuntuforums.org/showthread.php?p=9552634")

Which driver is shown (via **sudo lshw -C network**)?

---

### Post by wenfuli on 2010-07-06
I'm having the same problem. All of a sudden my wireless doesn't work and I have a "Networking disabled" message from the internet connection icon in the panel. What's going on?

---

### Post by wenfuli on 2010-07-06
> **wenfuli said:**
> I'm having the same problem. All of a sudden my wireless doesn't work and I have a "Networking disabled" message from the internet connection icon in the panel. What's going on?

Change that: both my wired and wireless aren't working.

The problem started after I decided to try to hibernate my machine. It seemed to hibernate fine, but would not start back up, forcing me to manually restart. Since the restart, I have had the "Networking disabled" message and cannot connect. I've tried restarting to see if that would fix the problem, but nothing has helped yet. I still can't connect.

---

### Post by Iowan on 2010-07-06
wenfuli:
You should start your own thread so help can be tuned to your problem. 
In the meantime, right-click Network Manager icon and verify networking is enabled. If it is, check [this]("http://ubuntuforums.org/showthread.php?t=1505217") thread.

---

