---
title: "need urgent replay about my problem"
date: 2010-05-20
forum: Multimedia Software
---

### Post by Raihan004 on 2010-05-20
wheb i tipe terminal this code sudo apt-get install multiget this code then this msg coming
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 what can i do pls help me:( i cant download anything using terminal

---

### Post by xc3RnbFO8P on 2010-05-20
Close **Synaptic Package Manager** or **Ubuntu Software Center**

---

### Post by xzero1 on 2010-05-20
The lock is used so that only one process can access the resource at a time. Make sure you don't have synapatic or similar programs running, then try again. If you reboot and you still have the problem then you may have to delete the lock that is referenced.

---

