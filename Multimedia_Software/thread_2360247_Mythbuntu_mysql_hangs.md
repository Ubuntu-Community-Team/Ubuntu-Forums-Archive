---
title: "Mythbuntu mysql hangs"
date: 2017-05-02
forum: Multimedia Software
---

### Post by jamoody on 2017-05-02
No input on the General forum so let me try here as well.

mysql hangs every few weeks, eating 100% CPU for hours on end.   /var/log/mysql.log is empty (zero bytes) so that doesn't seem to be the  location of the log.  Can anyone point me to the log location?

After I reboot to recover, /var/log/mysql/mysql/error.log does show  errors with timestamps right after the reboot so I don't know if the  errors are caused by the reboot with mysql hung or if the mysql hang is  due to the database errors.  

I see in syslog that cron.daily started running but it didn't seem to  get as far as my database backup (first thing my backup routine does is  touch a file to record the timestamp) so I don't believe the mysql hang  is related to backing up the database.

I believe (please correct me if I'm wrong) that cron.daily runs in  alphabetical order so mythdatabase-backup should run before  optimize_mythdb so the optimization doesn't seem to be what is hanging  mysql.

Other ideas?

I'm running Mythbuntu 14.04.5 with MythTV 0.28.1-21 (latest fixes as of 4/28).

---

### Post by deadflowr on 2017-05-03
see if what this bug is about is what you are affected by:
[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767]("https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767")

---

### Post by jamoody on 2017-05-05
I don't think so.  I have mysql performance tweaks set but I'm at Ubuntu 14.04.5, I haven't yet moved to 16.04 and this seem to be specific to when upgrading to 16.04.  In addition /var/log/mysql/error.log is completely empty.  I can run MythTV for days with no problems and then mysql will lock up.

I've recently discovered that / was getting changed sporadically to read-only mode and I wonder if that was the case when mysql was locking up, I didn't know enough to check.  I found a problem in syslog which showed that acpi was restarting every 3 seconds due to events sub-directory was missing and since taking care of that / hasn't been changing to read-only and mysql hasn't locked up, but it's only been 2 days so I'm hesitant to declare victory yet.

---

