---
title: "hostname change in mythconverg error"
date: 2009-06-13
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-06-13
I changed my slave backend's hostname and I found this tutorial on fixing it: [http://www.mythtv.org/docs/mythtv-HOWTO-23.html](http://www.mythtv.org/docs/mythtv-HOWTO-23.html)

I did everything but when I restored the database it returned an error. I used gedit (find and replace) instead of sed just as an FYI.


mysql -u mythtv -pgq3clAyj mythconverg < mythtv_restore.sql
ERROR 1062 (23000) at line 733: Duplicate entry 'JobQueueRecover-mythbuntu' for key 1

DO I need to worry about this. if so, can you please spell it out as I am not familar with mysql at all! thanks so much.

---

