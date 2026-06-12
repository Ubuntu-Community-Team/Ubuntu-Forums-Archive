---
title: "Cannot retrieve share list from server"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by bahamut920 on 2009-10-21
I'm running Ubuntu 9 and trying to get it connected to a workgroup composed primarily of Windows XP systems (entirely at the moment, actually, but there's another Ubuntu 9 system I'm going to set up after this).  Whenever I try to access the network, it gives me an error message saying "Cannot retrieve share list from server". I can connect to the Internet, so it's not a network problem, and I'm using an ethernet connection. Can Ubuntu use peer-to-peer workgroups, or does it have to have a server?  If it can access peer-to-peer networks, what am I doing wrong?

---

### Post by Iowan on 2009-10-21
Semantics, but Samba is a server/client system. The machine that shares the files must have Samba (server component) installed... or be Windows with sharing enabled. Ubuntu normally has the client pre-installed, so it *should* be able to access files shared form a Windows box.  
I've seen the "Cannot retrieve share list" error in other threads, but don't know if I've seen a real fix.  That error is reportedly a firewall issue, but... 
You can see if anything [here]("http://ubuntuforums.org/showthread.php?t=1169149") is helpful.

---

### Post by bahamut920 on 2009-10-22
Thank you.  It was a domain name issue, and the thread you referred me to helped solve it.

... Or at least part of the problem, anyway.  I can access two computers on the network (coincidentally, they're both my computers), and others can access the shares from this system, but the Ubuntu system can't access any other computers on the network.  I get the same "Failed to retrieve share list from server" message I was getting when trying to access the network, before.

---

