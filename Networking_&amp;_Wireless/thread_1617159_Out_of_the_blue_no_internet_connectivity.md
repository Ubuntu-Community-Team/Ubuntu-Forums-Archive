---
title: "Out of the blue no internet connectivity"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Cyked on 2010-11-09
Weird issue started today.  I can connect to anything locally, I can SSH in locally but nothing works from outside my network (can't access pages in apache, can SSH, etc.)

I've checked the logs I can think of, but what should I be looking for?  The last thing I did today was add a FW rule to log and drop from an IP, saved my iptables to a file in /etc. (this was at 10:45am).  The last time I successfully logged in remotely 1:03pm.  I connected multiple times in between. I've rebooted remotely once or twice.  That's it.


I've already flushed iptables.  Any thoughts?  See below for what was in auth.log towards the end of the day.  Thanks!

---

### Post by Cyked on 2010-11-09
Nevermind.  Not sure what happened.  I have other machines connected to the same router that had no issues.  I rebooted my network equipment this morning and it started working again.

---

