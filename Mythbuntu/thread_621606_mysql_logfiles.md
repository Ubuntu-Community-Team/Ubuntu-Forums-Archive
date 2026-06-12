---
title: "mysql logfiles"
date: 2007-11-23
forum: Mythbuntu
---

### Post by mrkite00 on 2007-11-23
Hi.

I've just fired up my mythfrontend to find out it would not start. After looking the log, I've realized that mysql was not accepting connections... 

The cause: my / partition is full. A little "du" command shows me that my /var/log/mysql contains 8.7Gb of log files, thus filling my little HD (the big one is only for recordings :))

I've deleted those files manually to be able to restart mysql. Is logrotate suppose to flush those log files or is there any other job that should do it?

Thanks.

---

### Post by superm1 on 2007-11-24
Well they shouldn't be growing that large in the first place.  Check /etc/mysql/my.cnf for any verbosity options.

---

### Post by mrkite00 on 2007-11-24
Nothing really surprising in my.cnf. Pretty much defaults with those two lines:

expire_logs_days        = 10
max_binlog_size         = 100M

My log of yesterday is 6 mb and today is 11 mb. At 11 mb each, it would take 790 log files to fill 8.7 gb!

Strange...

---

### Post by superm1 on 2007-11-24
Yeah that expiring should have taken care of it.  If this happens again, post back to this thread and see if you can investigate a little further as to the contents of the logs.

---

