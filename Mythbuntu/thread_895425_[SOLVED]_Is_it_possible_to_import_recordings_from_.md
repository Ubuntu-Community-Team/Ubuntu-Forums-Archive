---
title: "[SOLVED] Is it possible to import recordings from another Mythbuntu Machine?"
date: 2008-08-20
forum: Mythbuntu
---

### Post by Stevi on 2008-08-20
Hi,

yesterday I had to reinstall Mythbuntu 8.04. My recordings are saved on another partition. I would like to import the old recordings because I'd like to cut and burn them to DVD. Is this possible?

I already changed the recordings-directory but the old recordings don't appear in the watchlist/recordings-menu.

Thanks in advance

Stevi.

---

### Post by klc5555 on 2008-08-20
Your recordings don't appear, because you didn't save a backup of your old database along with your old recordings. Your new database doesn't know about them.

Recordings are supposed to be addable to the database manually by means of running the mythrebuilddatabase.pl script, which is supposed to be available in one of the /contrib directories in the distro and which is supposed to ask you to fill in data for all the orphaned recordings it finds within a directory. I've never had occasion to use the script, so I can't personally vouch for it. You may also have to run "mythtranscode --buildindex", followed by  "mythcommflag" on the recovered recordings to get them ready to edit and archive to DVD, if that's what you want to do. 

But most importantly, you need to keep copies of regular database backups in the same partition as your recordings, so next time Myth fries, and it will fry again at some point, after your clean install you can just restore your database from the most recent backup and everything will be just as it was before Myth fried.

There's a super-simple daily backup script available in the "Periodic maintenance" section of the Mythtv user manual on their wiki.

The whole script is just:

---------------------
#!/bin/sh
#Dumps the mythconverg database - daily backup
#Keeps the last 7 days
DAY=`/bin/date +%u`
DUMPFILE="mythdb_$DAY.sql.gz"
/usr/bin/mysqldump -u mythtv -pmythtv mythconverg -c \
      > /mnt/foo/sqldump/$DUMPFILE
exit 0 
--------------------------------

On my own machine,I set up this particular script to run as a daily chron job, modified only by adding a line to have a second copy of the daily mythconverg backup dumped into a database backup subdirectory in the directory on the drive where I keep my recordings --keeping a mythconverg backup in the same partition as my recordings has been a lifesaver on several occasions. It only takes 5 minutes to restore a db from backup.

Cheers!:)

---

### Post by Stevi on 2008-08-20
Hi klc5555,

thank you. I tried myth.rebuilddatabase.pl (btw it's located in /usr/share/doc/mythtv-backend/contrib/) but I wasn't successful. It seems that I use the wrong parameters [Message: "DBI connect('database=mythconverg:host=mythbuntu','mythtv',...) failed: Can't connect to MYSQL server on 'mythbuntu' (111) at ./myth.rebuilddatabase.pl line 191"]. I tried --try_default, host=mythbuntu, dbhost=mythtv, user=mythtv, pass="the_one_from /etc/mythtv/mysql.txt", -database=mythconverg, etc.
:confused: :(

---

### Post by klc5555 on 2008-08-20
Just from the initial look at your message, assuming your MySQL password for the "mythtv" user is correct (i.e. the one that appears in the General setup screen for your new frontend), and assuming this new installation actually has a mythconverg database (because you've already run the setup on the new backend and have run mythfilldatabase), you might want to try substituting ip addresses for names in the host= and dbhost= variables.  127.0.0.1 for them if localhost, or whatever ip has been assigned to the machine if set up for remote access.

The mythrebuilddatabase.pl script doesn't seem to have been included on Mythbuntu 7.10, which I'm currently running, so I don't have it available to play with. And internet documentation for it appears to be nearly nonexistent.

All the best.

---

### Post by Stevi on 2008-08-20
Hey, thank you klc5555. I think it's almost done. 127.0.0.1 seems to work. But there is another strange error. The script seems to be unable to define the time:
```
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at ./myth.rebuilddatabase.pl line 55.
```
line 55 is: 
```
use Time::Format qw(time_format);
```
Running the script without this line:
```
Undefined subroutine &main::time_format called at ./myth.rebuilddatabase.pl line 389, <STDIN> line 2.
```

Any ideas?

---

### Post by newlinux on 2008-08-20
you are probably missing a needed perl library. I'm no expert on perl, but you might want to make sure  libdatetime-perl or libtime-perl is installed.

Alternatively, you could just put the recordings in your mythvideo directory, and then run one of those scripts out there (I use a tvrage based script) that automatically pulls tv episode information (this is based on the file name, so you'd need to name the file accordingly) for my tv shows I put in mythvideo. You wouldn't be able to access them from the recordings screen, and no commercial flagging, but they'd be available.

---

### Post by Stevi on 2008-08-20
> **newlinux said:**
> you are probably missing a needed perl library. I'm no expert on perl, but you might want to make sure  libdatetime-perl or libtime-perl is installed.
Yeah, that's it. Thank you very much. Now all my files appear. 
Again thanks to newlinux and klc5555!

\\:D/

---

