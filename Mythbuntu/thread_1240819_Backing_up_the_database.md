---
title: "Backing up the database"
date: 2009-08-15
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-15
I am trying to automate daily backups of my database. I have read the instructions at [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance), and I put the following script in /etc/cron.daily/

```
# !/bin/sh
# Dumps the mythconverg database - daily backup
# Keeps the last 7 days
DAY=`/bin/date +%u`
DUMPFILE="mythdb_$DAY.sql.gz"
/usr/bin/mysqldump -u mythtv -p[password] mythconverg -c | gzip > /var/backups/$DUMPFILE
exit 0
```

It doesn't work.

Now, sorry if these seem like really basic questions, as I'm rather new to Linux and all this scripting stuff. Is simply putting the script in the /etc/cron.daily/ folder enough to make it run automatically, or do I have to do something else to let the system know I want to run it every day?

Or is it something to do with permissions? If I manually run the script as the root user, it works, but if I manually run it without root permissions, it doesn't.

The folder into which the backup is supposed to go (/var/backups/) is read only for users other than root, although the backup script built into Mythbuntu that backs up the database weekly seems to work OK and puts weekly backups in that folder, so I assume that it is not actually necessary to make /var/backups/ read/write for all users. Is that correct?

Many thanks
NM

---

### Post by wojox on 2009-08-15
All scripts in anacron are run as root. So you should be good there. If you named the file backup.sh rename it backup. Drop the file extension and see if that helps.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by jb5 on 2009-08-15
Periods in anacron script file names are "not allowed".
As above, either use a "-" instead of "." in the filename, or lose the "." altogether.

[Lost a few hours myself until I discovered this].

---

### Post by NautiusMaximus on 2009-08-15
Hm. Well there were no periods in the filename, but it was rather long. Could that have anything to do with it?

Anyway, I've now renamed it from mythtv_db_backup to mybackup

Let's see if that does the trick.

---

### Post by jb5 on 2009-08-16
Hmmm, should have read your post properly, just noticed the backup.sh commented above and confirmed that "." are problematic. 
Anyhow, not sure what to suggest, but here are my cron.daily & cron.weekly scripts for reference.

```
#!/bin/bash

  # Directory & file root to store backup
  cBackup="/hmv/mythconverg" ;

  # First run optimize tables perl script
  perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

  # Now backup the mysql database to backup directory
  mysqldump -u mythtv -pYourPassword mythconverg > ${cBackup}.$(date +%F) ;

  chown jb:jb ${cBackup}.$(date +%F)
  ls -lh ${cBackup}.*
```

& weekly```
#!/bin/bash

  cBackup_Dir=/hmv ;
  cd ${cBackup_Dir} ; 


tar --remove-files -cjvf "DB.$(date +%F).tar.bz2" "mythconverg."* ;

chown jb:jb DB.$(date +%F).tar.bz2 ;
```


The only thing that looks odd is the -ps, but if you have it running manually then it probably isn't that.

I'm not at my machine at the moment, but are the cron.daily scripts executable?```
sudo chmod a+x <filename>
```
I'm not sure if they also need to be owned by root also```
sudo chown root:root <filename>
```

The contents of the other scripts in cron.daily directory will give you your clue as to the correct properties your script should follow.

---

### Post by NautiusMaximus on 2009-08-16
Ah, I've noticed that your scripts begin 

```
#!/bin/bash
```

whereas mine begins

```
# !/bin/sh
```

and in fact the script on the page where I got the instructions began

```
#!/bin/sh
```

so is it possible that the extra space is what's screwing things up? And does it matter whether it's "bash" or "sh"?

Anyway, I've removed the space, so let's see if that solves the problem.

---

### Post by jb5 on 2009-08-16
I've just performed a quick test and the space doesn't appear to matter, unfortunately. (Certainly when running the script in a terminal).

The bin/bash & bin/sh will provide availability to slightly different instruction sets.

I found this out by accident as I was testing a script on my desktop which worked perfectly. 
On my MythBox I "thought" I had the same script - but it did not work as expected. 
It was only when I noticed that I'd used bash for one and sh for the other that the penny dropped and a change to bash solved the problem!

However, if your script runs manually, then other than the permissions and ownership I'm not sure what to suggest next.

---

### Post by NautiusMaximus on 2009-08-17
Hurrah! It was the space.

I removed the space, and now the script runs.

Strange that it only seems to affect it running as a cron job. It was quite happy to run manually with the space in it.

---

### Post by jb5 on 2009-08-17
Glad you got it working.

Some commands that I discovered along the way that might be useful.```
ls -l /var/spool/anacron
```The timestamps show when the scripts were last run.```
sudo gedit /var/mail/mail
```My scripts tend to output to this mail log. (It used to e-mail my user account, but after a fresh install I haven't managed to get back to that situation!) 
This file will grow as time passes, so it is worth keeping an eye on it.

---

