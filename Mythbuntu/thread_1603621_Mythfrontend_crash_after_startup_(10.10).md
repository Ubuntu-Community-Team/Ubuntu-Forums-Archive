---
title: "Mythfrontend crash after startup (10.10)"
date: 2010-10-22
forum: Mythbuntu
---

### Post by jrockinl on 2010-10-22
My mythfrontend crashes (exits) 1/2 second after the main menu appears.

I have just installed Mythbuntu 10.10 on a Acer Revo 3610 - frontend only.  I have another Revo set up with 10.4 and auto builds to get mythtv 23.1.  I need 23.1 because the ABC station in town has a messed up signal for which 23.1 has a work-around.

I don't know what is going on and I do not see any mythtv directory inside /var/logs to see if there is any indications what is occurring.

Any ideas?

---

### Post by ian dobson on 2010-10-23
Hi,

Maybe try creating a directory /var/log/mythtv (make sure the permissions are setup correctly) then reboot. It could well be that the frontend is crashing as the log directory is missing.

```

ls /var/log/ -o
drwxr-xr-x 2 root      4096 2010-05-04 20:39 fsck
drwxrwx--T 2 root      4096 2010-10-23 09:41 gdm
drwxr-xr-x 2 root      4096 2010-05-04 20:39 installer
-rw-r--r-- 1 root         0 2010-08-19 06:35 jockey.log
-rw-r----- 1 syslog 1018321 2010-10-23 09:41 kern.log
-rw-rw-r-- 1 root    292292 2010-10-23 09:42 lastlog
-rw-r--r-- 1 syslog       0 2009-01-10 08:36 lpr.log
-rw-r----- 1 syslog       0 2008-10-30 05:57 mail.err
-rw-r----- 1 syslog       0 2008-10-30 05:57 mail.info
-rw-r--r-- 1 syslog       0 2009-01-10 08:36 mail.log
-rw-r----- 1 syslog       0 2008-10-30 05:57 mail.warn
-rw-r--r-- 1 root         0 2009-11-28 12:48 mcc.log
-rw-r----- 1 syslog  807418 2010-10-23 09:41 messages
drwxr-x--- 2 munin     4096 2010-10-19 19:32 munin
drwxr-s--- 2 mysql     4096 2009-09-13 10:42 mysql
-rw-r----- 1 mysql        0 2009-11-27 17:35 mysql.err
-rw-r----- 1 mysql        0 2010-10-19 19:32 mysql.log
drwxrwsr-x 2 mythtv    4096 2010-09-09 05:45 mythtv

```

Regards
Ian Dobson

---

### Post by jrockinl on 2010-11-02
Thanks for the idea.  It didn't directly solve the problem but it did lead to actually getting a log file for the frontend which pointed straight to the problem.

It turned out my backend had a different timezone setting than the frontend (even though they both are in the USA Central).

---

