---
title: "Today, failed to retrieve share list from server"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-20
However only on one win7 pc, viewing shares on the other win7 does work.

The other win7 pc can view the shares which ubuntu cant..

I tried this idea
```
name resolve order = bcast host
```
from 
[http://www.liberiangeek.net/2012/03/how-to-fix-failed-to-retrieve-share-list-from-server-in-ubuntu-12-04-11-10-when-file-sharing-with-windows/](http://www.liberiangeek.net/2012/03/how-to-fix-failed-to-retrieve-share-list-from-server-in-ubuntu-12-04-11-10-when-file-sharing-with-windows/)

then did instead of reboot
```
scott@scott-P5QC:~$ sudo restart smbd
smbd start/running, process 6776
scott@scott-P5QC:~$ 


```

still no change. also past few days samba was crashing and seems to have been fixed later perhaps by an update.

---

### Post by sdowney717 on 2013-01-20
I just tried my own ubuntu machine from itself and cant view them either. However the win7 pc's can view my machine, so I guess samba is broken.

maybe just reboot?

---

### Post by sdowney717 on 2013-01-20
well, now I reboot and smbd crashes AND I have no clickable icons for the network PC, they vanished.
Seems like I Am I the only one with problems?
This used to work.

there is one major change I made, I upgraded the kernel to 3.5 from 3.2 on ubuntu 12.04

---

### Post by sdowney717 on 2013-01-20
I solved, stupid windows pc issue needed reboot, out of resources!
Even though it works on a windows to windows lan, if ubuntu is in there you can get error

this has more info.
[http://ubuntuforums.org/showthread.php?t=2106842](http://ubuntuforums.org/showthread.php?t=2106842)

my samba was also messed up.

---

