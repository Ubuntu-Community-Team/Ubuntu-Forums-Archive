---
title: "Failed to Scan SG Video Hosts."
date: 2012-05-12
forum: Mythbuntu
---

### Post by mapota on 2012-05-12
Hi all,
 
I am having trouble with the error message "Failed to Scan SG Video Hosts: If they no longer exist please remove them"
 
I am running 11:10 and myth 0.25 on the backend/frontend combo. It is on this machine that I am seeing the error when scanning for changes via the menu.
 
There is currently only one video in each directory for testing purposes. Using the videos list I can see both videos but still get the error.
 
I have read the following thread 
 
[http://ubuntuforums.org/showthread.php?p=11248258#post11248258](http://ubuntuforums.org/showthread.php?p=11248258#post11248258)
 
As per that thread, I can provide the following information
 
I have two storage groups set up for videos. These are 
 
/var/lib/mythtv/videos
and
/storage/mythtv/Videos
 
Performing ls -l on each directory yields the following
 
ls -l /var/lib/mythtv/videos
total 13026048
-rwxr-xr-x 1 andrew mythtv 13338673152 2012-05-12 12:48 The Notebook.mpg
 
and 
 
ls -l /storage/mythtv/Videos
total 6538880
-rwxr-xr-x 1 andrew mythtv 6695813120 2012-05-10 19:51 Gran Torino.mpg
 
So as far as I can tell the storage groups are set up correctly, the permissions look good to me, but I am not an expert and may be missing something.
 
I have set the group name to be mythtv for all the other storage groups as well , ie fanart, Coverart etc
 
Any hints on where I should be looking next? Thanks
 
I have also tried changing the owner of the files for both directories with no change to the result. I.e All files are seen but still getting the error.
 
Andrew

---

### Post by nickrout on 2012-05-12
I assume google has already found this for you?

[http://www.gossamer-threads.com/lists/mythtv/users/463828](http://www.gossamer-threads.com/lists/mythtv/users/463828)

Have you changed a hostname?

---

### Post by mapota on 2012-05-13
OK looks like that may be the issue. I was having trouble with the install, due to sound issues. So performed a full install again but restored the database. I thought I had kept the same hostname but I may have screwed up on one or more capitals. I thought the host name was something like Potter-Myth-Master-Backend. 
 
I tried doing the following search 
 
mysql -umythtv -p mythconverg -e "SELECT COUNT(*) FROM settings WHERE hostname LIKE '%otter%';"
 
and received 886 as a result. Then I did
 
mysql -umythtv -p mythconverg -e "SELECT COUNT(*) FROM settings WHERE hostname LIKE '%Potter-Myth-Master-Backend%';"
 
and received 267 as a result
 
Then once more as 
 
mysql -umythtv -p mythconverg -e "SELECT COUNT(*) FROM settings WHERE hostname LIKE '%potter-myth-master-backend%';"
 
and once again received 267 as a result.
 
So it looks like I have used a different hostname. What would be my best course of action. Should I use the steps in "23.12 Changing your hostname". If so how do I deal with the multiple entries?
 
Andrew

---

### Post by mapota on 2012-05-13
OK done a bit more checking and found the storagegroup table has 36 rows. 
 
18 where the hostname is incorrect "potter-Myth-Backend-Master" and 18 where the hostname is "Potter-Myth-Master-Backend". So really a combination of capital letters and transposition of terms.
 
Can I run a sql command to delete all database entries that refer to the old hostname?
 
Or should I as suggested in section 23.12 issue the following command
 
mythconverg_restore.pl --change_hostname --old_hostname="potter-Myth-Backend-Master" --new_hostname="Potter-Myth-MasterBackend"
 
I am concerned this will just duplicate the exiisting rows in the storage group table and elsewhere in other tables!!
 
Andrew

---

### Post by mapota on 2012-05-15
> **mapota said:**
> OK done a bit more checking and found the storagegroup table has 36 
 
Can I run a sql command to delete all database entries that refer to the old hostname?
 
Or should I as suggested in section 23.12 issue the following command
 
mythconverg_restore.pl --change_hostname --old_hostname="potter-Myth-Backend-Master" --new_hostname="Potter-Myth-MasterBackend"
 
I am concerned this will just duplicate the exiisting rows in the storage group table and elsewhere in other tables!!
 
Andrew

bump, will only bump this once!

---

### Post by nickrout on 2012-05-15
Frankly I do not know, I suspect if you backup then clear out the storage group table, then scan for videos, then add only the correct entries, then scan again, you will succeed.

However I suggest you email the users mailing list and hope Michael Dean latches on to your post, as he is the db guru.

---

### Post by mapota on 2012-05-15
Ok Thanks will do

---

### Post by singedwings on 2012-05-18
Have you seen my similar problem
[http://ubuntuforums.org/showthread.php?t=1977904]("http://ubuntuforums.org/showthread.php?t=1977904")
I hope this is of help.

---

### Post by mapota on 2012-05-18
I have gotten this fixed thanks to Nick and Michael Dean.
 
My particular issue was related to changing the hostname and then restoring a database from the older hostname.
 
To fix I followed the procedure covered in the following page [http://www.mythtv.org/wiki/Backend_migration](http://www.mythtv.org/wiki/Backend_migration)
 
This did work for me once I realised that I needed to delete the actual storage groups not just the directories. I have modified the procedure to highlight this point.
 
The following query will highlight if you have extra storage groups defined other than the ones you expect.
 
mysql -umythtv -p mythconverg -e "SELECT * FROM storagegroup;"

Thanks again,
 
Andrew

---

