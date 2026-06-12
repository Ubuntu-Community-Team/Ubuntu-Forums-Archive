---
title: "SSH fails after reboot"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by MrGrey1 on 2009-12-22
Ubuntu 9.10. 

SSHD is not starting on boot. It has to be manually started. Anyone know why sshd might not start automatically?

Another post here seems to be the same issue.
[http://ubuntuforums.org/showthread.php?p=8550800#post8550800](http://ubuntuforums.org/showthread.php?p=8550800#post8550800)

As it appears this is a bug is there any work around to get sshd to start/restart on boot? I need to be able to connect to the box before login as I tunnel vnc to the login window.

I have been trying to get ssh to restart after the login screen appears by using /etc/rc.local however it deosn't seem to work.
I have tried adding '/etc/init.d/ssh restart' with no success.

Solution:
Got sshd starting again on boot by downgrading Upstart 0.6.3-11 to 0.6.3-10.
[http://ubuntuforums.org/showthread.php?t=1305226&page=2](http://ubuntuforums.org/showthread.php?t=1305226&page=2)

---

