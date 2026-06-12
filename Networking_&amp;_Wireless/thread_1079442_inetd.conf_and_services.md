---
title: "inetd.conf and services"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by alnilamski on 2009-02-24
Hey all,

I am trying to make sure that no superfluous networking (listening) services are running on this Ubuntu 8.04 machine. I looked into the inetd.conf file, and it was empty!

This thread: [http://ubuntuforums.org/showthread.php?t=131844](http://ubuntuforums.org/showthread.php?t=131844)
told me that this is not unusual; nowadays, Ubuntu comes with an empty inetd.conf file.

My question is: **is there anything else I should be worrying about as far as services that might be started elsewhere, or is inetd.conf the only place they would originate from?**

Also, I'm planning to set up a secure shell on this thing (about which I know little, so I still have a lot of research to do). If anyone knows off-hand, **will I need to add a line to the blank inetd.conf to allow a secure shell to listen?** Or is that a stupid question that I'll find out doesn't even make any sense once I do some more research? :p

---

