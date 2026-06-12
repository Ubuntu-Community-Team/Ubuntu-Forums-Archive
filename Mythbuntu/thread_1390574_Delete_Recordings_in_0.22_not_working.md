---
title: "Delete Recordings in 0.22 not working"
date: 2010-01-25
forum: Mythbuntu
---

### Post by jrockinl on 2010-01-25
I have had an issue since installing Mythbuntu 9.10.  I cannot reliably delete recordings using either the "info" approach or by using MythWeb.  The listings seem to indicate the recordings are deleted, but they are not deleted.  Going out the menu and coming back in, the recordings show up again.  Thinking because I have the recordings on a XFS partition, I thought maybe I should give it some time to finish.  I then would check the next day and the recordings are still there.

I also like to record most shows with episode limits and removing the oldest one if the going over the limit.  This way of deleting recordings works perfect.

---

### Post by azmyth on 2010-01-26
My first guess would be to check the permissions/owners on the video files.

---

### Post by jrockinl on 2010-01-26
The directory shows permissions consistent with the following portion of the listings:

> jim-root@Opus:/$ ls /var/lib/mythtv/recordings -all
total 967709584
drwxrwsr-x  2 mythtv   mythtv       20480 2010-01-26 17:38 .
drwxrwxr-x 13 mythtv   mythtv        4096 2009-10-20 18:05 ..
-rw-r--r--  1 mythtv   mythtv  3378746528 2009-12-11 23:00 1021_20091211223000.mpg
-rw-r--r--  1 mythtv   mythtv        8644 2009-12-30 14:59 1021_20091211223000.mpg.100x56.png
-rw-rw-rw-  1 mythtv   mythtv       66112 2010-01-17 08:52 1021_20091211223000.mpg.png
-rw-r--r--  1 mythtv   mythtv  3376675708 2009-12-18 22:30 1021_20091218220000.mpg
-rw-r--r--  1 mythtv   mythtv        8384 2009-12-30 14:59 1021_20091218220000.mpg.100x56.png
-rw-rw-rw-  1 jim-root mythtv       69362 2009-12-18 22:30 1021_20091218220000.mpg.png


---

### Post by hambone79 on 2010-01-26
I am having a similar, but slightly different problem. If I watch any live TV shows, it appears in my Recorded Programs but no matter what I do I can not delete the files from MythTV. Also several shows that MythTV has recorded are showing up on my hard drive but not in the list of recorded shows in MythTV.

---

### Post by azmyth on 2010-01-26
I'd check the log files after you try deleting a recording to see what it says. I also added my login user to the mythtv group but I doubt this is your problem but it's worth a try.

---

### Post by hambone79 on 2010-01-26
I checked the logs, permissions, groups, etc. but nothing worked. I just finished completely uninstalling MythTV, deleted the mythtv database from mysql, then reinstalled everything and it appears to be working now.

---

### Post by teet on 2010-01-26
I had the same problem of not being able to delete recordings.

Did you guys upgrade to 9.10 from 9.04 by chance?

I added my user to the mythtv group and chown'ed my recordings directory and all was well...so I guess our problems may have been different.

-teet

---

### Post by jrockinl on 2010-01-27
I have reinstalled Mythbuntu 9.10 from scratch twice.  Once was when it was first released and once after my harddrive became corrupt because of static shocks resetting the PC.  (Antec Fusion case that wasn't grounded properly - now fixed)  The problem existed after both installs.

I thought everything Myth ran as mythtv already.  I will double check if my one user is in mythtv group just in case.

I will also look into the logs as suggested.

---

