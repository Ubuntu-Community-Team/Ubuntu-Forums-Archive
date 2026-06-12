---
title: "Upgrade from 14.04 LTS to 16.04 LTS fails: mysql for mythtv configuration"
date: 2016-04-25
forum: Mythbuntu
---

### Post by Caysho on 2016-04-25
In addition to Launchpad Bug #1571865 the /etc/mysql/conf.d/mythtv-tweaks.cnf contains variable table_cache which has now been deprecated - refer [https://bugs.mysql.com/bug.php?id=68315](https://bugs.mysql.com/bug.php?id=68315) for details.

I found this when the installation hung and I went looking for log files to try figure out what was happening.

There is a loop involving mysqld being started and then shutdown with an error about table_cache=128
This is evident from the /var/log/mysql/error.log file (I think that is where I found the problem)

Last week I upgraded to .28 and that seems to be working fine, so it looks like the installation scripts need to check the mysql version as part of the upgrade to 16.04

I do not have the logs available now as I have reverted the machine to it's previous state (14.04 / 0.28)

---

### Post by orange-wedge on 2016-04-27
I was having the same problem. You can either comment out "table_cache = 128" or change it to "table_open_cache = 128"

table_cache is a deprecated variable. Frustrating, I know.

---

### Post by Caysho on 2016-04-29
I reran the upgrade and submitted a bug report with the mysql error log:
[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767)

---

### Post by tcb2 on 2016-10-16
I recently upgraded my Mythubuntu backend to 16.04 (myth 0.28, mysql 5.7), which worked fine, but my Mac frontends would lock after a few minutes. No odd findings on front or back end logs, except that occasionally I would get malformed packet errors from mysql. I increased the max_allowed_packet setting to 1G. Front ends still locked, so then I commented out the mythtv-tweaks.cnf setting of query_cache_type = 1. Now front ends work.

---

