---
title: "NFS mounting with fstab &gt;&gt; loop on shutdown"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by ^_Pepe_^ on 2010-05-20
Hi all.

I have this configuration on my Ubuntu server:

1. Physical HDD1, mounted in /media/MYDATA
2. Physical HDD2, mounted in /media/MYDATA/MYMOVIES

This works, and has all my information.

Unfortunately I can not use CIFS to get my data, because of a bug with wireless connection and umounting at shutdown.

Until yesterday, I have no problem at all, mounting my NFS unit automatically in /media/MYDATA perfectly.

But, when I go to /media/MYDATA/MYMOVIES in my laptops, filesystem is empty.

I've included /media/MYMOVIES in the exports file (server) and in the fstab (client) and...it worked!!

:)

But...system does not shutdown at all.

If I manually try to umount /media/MYDATA the message received is "resource busy". :/ so...I guess this is the problem. If I manually umount /media/MYDATA/MYMOVIES first, laptop shutdown perfectly.

Is there any workaround for this? Any idea to force to umount first the second unit?

Thanks in advance.

^_Pepe_^

---

### Post by Sianegad on 2010-06-05
I just setup NFS to map my /home folder to my laptop and i`m getting the same problem.  From the little research i did yet, i understood that the problems is caused by the network being closed before the NFS link, wich then hangs the system.

It seems to be an old bug too, there is a fix, but i don't clearly understand it yet. 
 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/113095](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/113095)

hopefully it will help you and you could then explain here...

---

