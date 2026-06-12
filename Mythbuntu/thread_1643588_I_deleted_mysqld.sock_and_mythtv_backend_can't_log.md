---
title: "I deleted mysqld.sock and mythtv backend can't log to mysql"
date: 2010-12-12
forum: Mythbuntu
---

### Post by gunnartr on 2010-12-12
I accidentally deleted the mysqld.sock and the backend server can't login to mysql. how can get out of this mess? How to restore mysqld.sock or how to get the backend to connect to mysql.

---

### Post by ian dobson on 2010-12-12
Hi,

have a look here [http://forums.mysql.com/read.php?11,42525,45027#msg-45027](http://forums.mysql.com/read.php?11,42525,45027#msg-45027)

the file should be created by mysql on starting.

Regards
Ian Dobson

---

### Post by gunnartr on 2010-12-12
> **ian dobson said:**
> Hi,

have a look here [http://forums.mysql.com/read.php?11,42525,45027#msg-45027](http://forums.mysql.com/read.php?11,42525,45027#msg-45027)

the file should be created by mysql on starting.

Regards
Ian Dobson


Tanks a lot. I restarted the mythtv box and mythtv is ok.

---

