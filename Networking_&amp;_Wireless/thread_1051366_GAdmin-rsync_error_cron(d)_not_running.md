---
title: "GAdmin-rsync error cron(d) not running"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by walter_j on 2009-01-26
I installed GAadmin-rsync and backed up remote files - worked great. I tried to set up times when i want the backups to be run and checked all boxes, but when I save the backup settings I get error cron(d) doesn't seem to be running. service cron status shows cron is running. Needless to say, the scheduled backup isn't running. What could be wrong?

ubuntu 8.10
GAdmin-rsync 0.1

Is it just GAdmin-rsync? I tried rsync from the command line but I couldn't seem to get it to work via ssh.

rsync -avze xx.xx.xx.xx:22/home/data/tags/ ~/test
The above command run from the local pc connects, but nothing copies.

---

### Post by jonobr on 2009-01-26
Hey

Recommend you write a small script to do something and schedule via cron.


Heres a good thread showing using logger, 

[http://ubuntuforums.org/showthread.php?t=853992](http://ubuntuforums.org/showthread.php?t=853992)


Read the entire thread first before trying the recommendation

Also, note the Path problem this person had

---

