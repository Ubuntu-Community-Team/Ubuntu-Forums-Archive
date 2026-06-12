---
title: "Mythtv database problems - where are my recordings?"
date: 2010-10-31
forum: Mythbuntu
---

### Post by Brasil on 2010-10-31
Hi all, I've been having some real issues with mythtv's database. Recordedseek became corrupted and couldn't be fixed no matter what I tried, so I went in, truncated the table and rebuilt it with mythcommflag. I also did some myisamchk repairs on a couple of other tables (settings and eit_cache). Now myisamchk tells me all the tables are fine. But when I restart the database I'll get an error like:

ERROR 126 (HY000) at line 1: Incorrect key file for table '/tmp/#sql_2506_0.MYI'; try to repair it

In terms of the effect, I have lost all my recordings. Listings seems fine (although it has crashed a couple of times, I think I've fixed whatever was wrong), recording schedules seems fine, but even though there is stuff that should be due to record upcoming recordings is empty. Mysqlcheck isn't showing any problems, I'm at a loss as to where to go from here.

---

### Post by klc5555 on 2010-10-31
> **Brasil said:**
> Hi all, I've been having some real issues with mythtv's database. Recordedseek became corrupted and couldn't be fixed no matter what I tried, so I went in, truncated the table and rebuilt it with mythcommflag. I also did some myisamchk repairs on a couple of other tables (settings and eit_cache). Now myisamchk tells me all the tables are fine. But when I restart the database I'll get an error like:

ERROR 126 (HY000) at line 1: Incorrect key file for table '/tmp/#sql_2506_0.MYI'; try to repair it

In terms of the effect, I have lost all my recordings. Listings seems fine (although it has crashed a couple of times, I think I've fixed whatever was wrong), recording schedules seems fine, but even though there is stuff that should be due to record upcoming recordings is empty. Mysqlcheck isn't showing any problems, I'm at a loss as to where to go from here.

Normally at this point, you'd probably restore a clean mythconverg database from your most recent daily backup dating before the difficulties began. [http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore) . Then add back in any recordings that are more recent than that last backup using something like myth.rebuilddatabase.pl (described here: [http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl) )

Failing the existence of daily backups, depending on the mythtv version you may find gzipped automatic weekly backups in /var/backups from which you could restore a clean mythconverg, and then again add back any recordings that may be more recent than this backup. And then set up a daily mythconverg backup routine. 

mythcommflag has long seemed unreliable for fixing the seektable on dvb recordings (works fine for analog recordings). For individual dvb recordings that need their seektable rebuilt, mythtranscode seems to be a better choice, i.e.: mythtranscode --mpeg2 --buildindex -c [channel-code] -s [full-start-time] See [http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode)

---

### Post by Brasil on 2010-11-01
Well blow me down!

I went in to do my restore and I couldn't download the restore script becamse /tmp/ was full. So I rebooted and Tadaaa! all my recordings are back.

Thanks for your advice, I'm very grateful for it.

---

