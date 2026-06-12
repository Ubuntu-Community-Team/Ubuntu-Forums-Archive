---
title: "[SOLVED] mythbuntu hard system freeze"
date: 2007-12-09
forum: Mythbuntu
---

### Post by a_posse_ad_esse on 2007-12-09
Hello all.  I have been experiencing hard system locks on my server which is currently running Mythbuntu Gutsy (this was also the case when using the gutsy server edition w/ mythtv).  It is recording with a Hauppauge 500.

Every so often, the system will lock up with mythweb unable to connect and constant disk activity.  Restarting the machine fixes the issue.

I am not sure if it is caused by two shows recording at once, or if me observing this is simply coincidence.  I often don't see the exact moment when it happens, or when processes freeze when this occurs.

Is anyone having difficulty with this?  Are there any known fixes?  Better uptime would be nice for the coming semester as I am attempting to implement a data mirroring/backup system on the server as well.  Thanks

---

### Post by barney_1 on 2007-12-09
Check your logs and post anything that looks fishy.

take a look at:
```
/var/log/Xorg.0.log.old
/var/log/syslog.0
/var/log/mythtv/mythbackend.log.1
/var/log/mythtv/mythfrontend.log.1
```

---

### Post by a_posse_ad_esse on 2007-12-09
I just recovered the system again, and couldn't find anything wrong with the logs from around the time it would have crashed.  There was a lot of complaints about 
```

Dec  8 23:29:47 server mysqld[4774]: 071208 23:29:47 [ERROR] /usr/sbin/mysqld: Table './mythconverg/recordedseek' is marked as crashed and should be repaired
Dec  8 23:29:47 server last message repeated 9 times

```

This is from yesterday of course, and I didn't have any problems with it then.  The only thing I could think of is the daily maintenance done on the mysql tables that wasn't able to fix the problem, thereby crashing the system...

Realtime priority has been disabled for a while now too.  Any ideas?

---

### Post by barney_1 on 2007-12-10
Try running this to repair your MySQL database:
```
mysqlcheck -u root -p --repair mythconverg

```

Without other errors being thrown I don't really know how to start troubleshooting the problem.

---

### Post by a_posse_ad_esse on 2007-12-10
The command ran ok, no errors.

The only other thing that I can think of is that the freezes seem to happen most often during times of high recording/transcoding activity.  The card is a dual-tuner, so it can record 2 shows at once.  All of the shows that we have set to record are on around the same time, so I wonder if it would be too much for the system?

The machine itself is a Tyan Tiger MP with 2x AMD 1500MP, 1 GB RAM, ~3GB of swap.  Would recording be too much strain on either processors or hard disk?

I wish there was a setting to have transcoding and such done when all recording activity is finished in order to test this theory, but I don't think that there is.

---

### Post by a_posse_ad_esse on 2007-12-12
Is anyone else having problems with this?  I know that this had been an issue a little while back, but I haven't seen anything about it recently.

---

### Post by a_posse_ad_esse on 2008-02-05
It seems that the hard freeze is from a lack of available RAM.

---

