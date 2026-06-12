---
title: "HOW TO: Schedules Direct - Converting FromZapToIt Myth 20.2"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by tagra123 on 2007-09-13
Getting the data from previous mythtv versions wasn't honoring previously recorded settings. IT was re-recording programs that had been recorded before.

RECOMMENDED

sudo apt-get install phpmyadmin

Here are the steps that can make it work correctly.


This is from version .18 to .20.2 but it should work for other versions.

Before upgrading -- backup the database.
[B]
[SIZE="5"][COLOR="Red"]My actual recordings are on a separate disk/partition if you should back these up too especially if they are on the same partition. Copy the nuv files to another disk just to be safe. The steps for backing up the recording _are not described below_ (.nuv files)[/COLOR][/SIZE][/B]


```

cd ~
mysqldump -u mythtv -pmythtv mythconverg -c >mythconvergbackup-olddatabase.sql

```

Now extract the important pieces of the database from you current version.
(assuming username is mythtv and password is mythtv in this example)

  ```
 mysqldump -u mythtv -pmythtv mythconverg -c > mythtv_backup-olddatabase.sql
    
    grep "INSERT INTO \`record\` "  mythtv_backup-olddatabase.sql >record.sql
    grep "INSERT INTO \`recorded\` "  mythtv_backup-olddatabase.sql >> recorded.sql
    grep "INSERT INTO \`oldrecorded\` " mythtv_backup-olddatabase.sql >>oldrecorded.sql
    grep "INSERT INTO \`recordedprogram\` "  mythtv_backup-olddatabase.sql >>recordedprogram.sql
    grep "INSERT INTO \`recordedrating\` "  mythtv_backup-olddatabase.sql >> recordedrating.sql
    grep "INSERT INTO \`recordedmarkup\` "  mythtv_backup-olddatabase.sql >> recordedmarkup.sql
    grep "INSERT INTO \`recordedseek\` "  mythtv_backup-olddatabase.sql >> recordedseek.sql

```

SAVE ALL THESE FILES TO CD OR DVD


Now I was going from breezy to feisty with a complete new install so I installed feisty and them the mythtv backend.



COPY ALL THE FILE SAVE TO CD TO YOUR HOME DIRECTORY  in the newly installed system

Install PHPMYADMIN
```
sudo apt-get install phpmyadmin
```


BACKUP THE NEW DATABASE
```

cd ~
mysqldump -u mythtv -pmythtv mythconverg -c >mythconvergbackup-new.20.2database.sql

```

RESTORING THE DATA (assuming username is mythtv and password is mythtv in this example)

```
cd ~
mysql -u mythtv -p  mythconverg < record.sql
mysql -u mythtv -p  mythconverg < recorded.sql
mysql -u mythtv -p  mythconverg < oldrecorded.sql
mysql -u mythtv -p  mythconverg < recordedprogram.sql
mysql -u mythtv -p  mythconverg < recordedrating.sql
mysql -u mythtv -p  mythconverg < recordedmarkup.sql
mysql -u mythtv -p  mythconverg < recordedseek.sql

```

Now I receive a NULL value not allowed on one of these but don't remember which one. When it happens just go to phpmyadmin and empty the table that caused the problem and then open the sql file that caused the problem and use find and replace to change null to 0. and the reissue the mysql statememnt that caused the problem.


There are other places that tell how to setup a schedules direct account you'll want to do that. (Theres a free 7 day trial)

All data imported, schedules direct setup and mythtv working, but the system is re-recording programs that were previously recorded -- and this isnt the behavior that you want.

I posted the follow steps at schedules direct but here they are:

My original posts: [http://forums.schedulesdirect.org/viewtopic.php?f=5&t=309](http://forums.schedulesdirect.org/viewtopic.php?f=5&t=309)

This is easiest to do when using phpmyadmin (sql tab at top of page)

To fix the programid using sql to the 12 digits (Added two zeros) I ran the following command using phpmyadmin (mysql will work too)

```
UPDATE recorded
SET programid=CONCAT(SUBSTRING(programid, 1, 2),
'00',
SUBSTRING(programid, 3))
WHERE length(programid) = 12;
UPDATE oldrecorded
SET programid=CONCAT(SUBSTRING(programid, 1, 2),
'00',
SUBSTRING(programid, 3))
WHERE length(programid) = 12; 
```

To fix the duplicate field I ran the following command using phpmyadmin (mysql will work too)

```
update oldrecorded set duplicate=1
```

Now the final step I took was to do the following ( not completely sure if these are necessary but it seem to make everything work the way I wanted it to)

MYTHWEB recommended for these steps:

Go to your recording schedules using mythweb.

Go through each of your scheduled programs.

I turned of auto expire (I create dvds and don't want them auto expiring)

Now any schedules relying on a certain channel change to anytime any channel or any of the options that do not rely on a specific channel. 

Now all my previously recorded program arent being rescheduled. Yeah!

---

### Post by michwill on 2007-09-26
But how do you actually set up the "schedulesdirect.org" info?  I keep missing this.

---

