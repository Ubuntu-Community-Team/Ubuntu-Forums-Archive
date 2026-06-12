---
title: "Should I Have Three Backend Processes Running?"
date: 2010-02-02
forum: Mythbuntu
---

### Post by w6fm on 2010-02-02
I am new to Mythbuntu but have been running Myth TV for many years. Is it normal to have 3 backend processes running? This box is a combination front and backend with 2 PVR-250 capture cards.

Ron

rpatters@mythtv:~$ apt-cache policy mythtv
mythtv:
  Installed: 0.22.0+fixes22594-0ubuntu1
  Candidate: 0.22.0+fixes22594-0ubuntu1
  Version table:
 *** 0.22.0+fixes22594-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
        100 /var/lib/dpkg/status

rpatters@mythtv:~$ ps -ef | grep mythbackend
mythtv     653     1  0 16:46 ?        00:00:00 /bin/su -c /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log mythtv
mythtv     894   653  0 16:46 ?        00:00:00 sh -c /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
mythtv     895   894  0 16:46 ?        00:00:07 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
rpatters  2454  2038  0 20:34 pts/0    00:00:00 grep --color=auto mythbackend

---

### Post by superm1 on 2010-02-03
Until upstream decides to go and apply the patch at [http://svn.mythtv.org/trac/ticket/7832](http://svn.mythtv.org/trac/ticket/7832), yes.

---

### Post by w6fm on 2010-02-05
Thanks for the reply and all your good work.

Ron w6fm

---

