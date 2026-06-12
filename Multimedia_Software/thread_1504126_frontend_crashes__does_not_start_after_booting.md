---
title: "frontend crashes / does not start after booting"
date: 2010-06-07
forum: Multimedia Software
---

### Post by perjojek on 2010-06-07
I have installed mythbuntu 10.04. It worked well for a few days. Now my frontend does not start or crashes just after booting. You can see the frontend background for a few seconds but the menu does not load. After that, the mythtv window disappears and you can see the ubuntu desktop. Here are the last few lines from the log file:
 
2010-06-07 07:32:49.622 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-07 07:32:49.623 Using protocol version 56
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
 
Has anyone experienced that?

---

### Post by perjojek on 2010-06-09
Christian reported the exact same problem not long time ago - [http://www.gossamer-threads.com/lists/mythtv/users/433019](http://www.gossamer-threads.com/lists/mythtv/users/433019). He has not been able to fix the problem on 0.23 and backed to 0.22. It helped..

---

### Post by perjojek on 2010-08-29
If you have such a problem, install Mythdora. This resolved the problem for me.:D

---

