---
title: "Mytharchive Create DVD stalls"
date: 2008-08-29
forum: Mythbuntu
---

### Post by Chuckels550 on 2008-08-29
Mythbuntu 8.04-1 - I have been trying to use Mytharchive to burn some recorded files.  I finally got it to at least start to transcode the recording.  The job terminated before completion. 

Now, when I got to the Optical Drives>Archive>Create DVD, the system hangs and I cannot find any logs that would bear on what is causing the system to hang.  Any thoughts?

---

### Post by anonymousdog on 2008-08-29
Two log files will be of use.  Both are in /var/lib/mytharchive/temp/logs by default.  progress.log is the output you see in the log viewer in mythfrontend.  mythburn.log is the output of the various helper apps mytharchive uses during the mytharchive job.  I had some problems too, starting with incorrect permissions set on the mytharchive temp directory and lack of symlink for /dev/dvd.

I also have been playing with the mythburn.ph scripts to correct what I believe is at least one typo or omission of an update applied to other areas of the script.  If you find that your archive jobs are stopping because mytharchive can't find the mpeg file to archive because it's looking for for a file whose name is part of the recorded show's/video's title, ping me back; I think I have the fix.

---

### Post by Chuckels550 on 2008-09-29
Sorry to take so long to respond - my windows box got trashed and had to be rebuilt, which took up all of my energies until now.

I found out why the Mytharchive Create DVD seems to stall.  Somehow or other I have over 500,000 MB of recordings in the archive listing.  The Mytharchive Create DVD function was hanging because loading this huge list took so long.  

Is there anyway to clear the list of recordings ready-to-be-archived en masse?  Doing it one by one is beyond tedious.  I cannot burn anything using the list until the collection of recordings ready-to-be-archived is trimmed down to what can fit onto a DVD.

---

### Post by anonymousdog on 2008-09-29
A mysql query will do it: (you can get your MySQL password from ~/.mythtv/mysql.txt.)
```
mysql --password=<yourmysqlpasswordhere> mythconverg
```
The rest are commands to carry out in the mysql cli:```
TRUNCATE archiveitems;
```should clear out all the files to archive, then,```
SELECT * FROM archiveitems;
```should now return an empty set.```
quit
```to quit mysql.

Now you should be able to mytharchive with a clean selection list.

---

### Post by Chuckels550 on 2008-09-29
Thank you very much.

With one adjustment, that worked.  I am using Mythbuntu and in that setup mysql uses mythtv as the database username; instead of using the mythbuntu username, which means that the mysql username has to be specified, too, and the mysql username default is 'mythtv':

mysql --username=mythtv --password=<mysql password> mythconverg

---

