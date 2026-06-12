---
title: "WANBuntu?"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by GiftMatcher on 2008-12-22
I'm looking to simulate some network imperfections.  I could do this with Wanem but I would perfer to do this from the command line with a well vetted OS.  My setup is a windows 2003 server, a windows xp client, and a Ubuntu 8.10 server edition install.  All three of these os's are vms and on the same subnet.  My intent is to have all traffic between the windows xp client and server travel through the Ubuntu machine, get slowed down there, and then travel to its destination.  I have configured both the windows xp client and server to forward all of their traffic to the Ubuntu box.  This is where my knowledge ends.  I need to set the Ubuntu vm to accept incoming traffic and forward it directly out the same interface that it comes in - is this even possible?

---

### Post by superprash2003 on 2008-12-23
this should give you an idea.. [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

