---
title: "mythfilldatabase is shredding my disk"
date: 2012-05-15
forum: Mythbuntu
---

### Post by wo_shi_big_stomach on 2012-05-15
Running a current version Mythbuntu 0.25, there is perpetual disk activity  when running mythfilldatabase. The mythfilldatabase program does not get to the point of getting new entries; see output below.

I've tried running repair on the mythconverg database (it was fine) and even backing up, deleting, and restoring the database with no luck. Also, there are no errors related to this in the logs in /var/log/mythtv or /var/log/mysql logs. 

The disk sounds like it's trying to write over and over. If there is a bad spot on the disk, I would have thought deleting and re-importing the database would have caused it to be written to a different spot.

Thanks in advance for troubleshooting clues. 

/wsbs

output of mythfilldatabase:

2012-05-14 21:09:39.144338 C  mythfilldatabase version: fixes/0.25 [v0.25] [www.mythtv.org](www.mythtv.org)
2012-05-14 21:09:39.144350 N  Enabled verbose msgs:  general
2012-05-14 21:09:39.144362 N  Setting Log Level to LOG_INFO
2012-05-14 21:09:39.144395 I  Added logging to the console
2012-05-14 21:09:39.144400 I  Added database logging to table logging
2012-05-14 21:09:39.144454 N  Setting up SIGHUP handler
2012-05-14 21:09:39.144518 N  Using runtime prefix = /usr
2012-05-14 21:09:39.144529 N  Using configuration directory = /home/mythtv/.mythtv
2012-05-14 21:09:39.144618 I  Assumed character encoding: en_US.UTF-8
2012-05-14 21:09:39.145104 N  Empty LocalHostName.
2012-05-14 21:09:39.145129 I  Using localhost value of buster
2012-05-14 21:09:39.161875 N  Setting QT default locale to en_US
2012-05-14 21:09:39.162000 I  Current locale en_US
2012-05-14 21:09:39.162079 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-05-14 21:09:39.175269 I  Loading en_us translation for module mythfrontend
2012-05-14 21:09:39.178493 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-05-14 21:09:39.179441 I  Updating source #1 (TWC) with grabber schedulesdirect1
2012-05-14 21:09:39.179736 I  Found 109 channels for source 1 which use grabber
2012-05-14 21:09:39.179823 I  Checking day @ offset 0, date: Mon May 14 2012
2012-05-14 21:09:39.263889 N  Data is already present for Mon May 14 2012, skipping
2012-05-14 21:09:39.263959 I  Checking day @ offset 1, date: Tue May 15 2012
2012-05-14 21:09:39.263966 I  Data Refresh always needed for tomorrow
2012-05-14 21:09:39.263972 N  Refreshing data for Tue May 15 2012
2012-05-14 21:09:39.264062 I  New static DB connectionDataDirectCon
2012-05-14 21:09:39.266586 I  Retrieving datadirect data.
2012-05-14 21:09:39.266661 I  Grabbing data for Mon May 14 2012 offset 1
2012-05-14 21:09:39.266705 I  From Tue May 15 07:00:00 2012 to Wed May 16 07:00:00 2012 (UTC)
2012-05-14 21:09:39.266743 I  DataDirect: Grabbing listing data
2012-05-14 21:09:39.266808 I  Downloading DataDirect feed
content-type missing in HTTP POST, defaulting to application/octet-stream
content-type missing in HTTP POST, defaulting to application/octet-stream
2012-05-14 21:09:46.778647 I  Downloaded 256588 bytes
2012-05-14 21:09:46.778663 I  Uncompressing DataDirect feed
2012-05-14 21:09:46.794706 I  Uncompressed to 2205208 bytes
2012-05-14 21:09:47.213334 I  DataDirect: Your subscription expires on Sat Jun 23 5:05 PM
2012-05-14 21:09:52.879383 I  DataDirect: sourceid 1 has lineup type: CableDigital

<disk noises from here forward>

---

### Post by nickrout on 2012-05-15
There is a recent thread with a fix for this I think. I think it is the one entitled "0.25 upgrade experiences" or something similar.

---

### Post by wo_shi_big_stomach on 2012-05-15
Thanks, nickrout! This thread did have a fix:

[http://ubuntuforums.org/showthread.php?t=1956370](http://ubuntuforums.org/showthread.php?t=1956370)

The fix involves two config edits and a reboot:

1. Put the /tmp directory in a tmpfs filesystem by adding this line to /etc/fstab:

tmpfs   /tmp   tmpfs   nodev,nosuid    0 0

2. Add the following line to /etc/mysql/conf.d/mythtv.cnf:

default_storage_engine=MyISAM

This is different than the posts on page 4 of the thread above, which suggest putting this line either in /etc/mysql/conf.d/mythtv-tweaks.cnf or in /etc/init.d/mysql.

3. Reboot.

After this, mythfilldatabase ran at about the same speed as in 0.24, without all the disk thrashing. The thread above also explains what changed in MySQL that requires these changes.

Thanks again for the pointer!

---

### Post by nickrout on 2012-05-16
> **wo_shi_big_stomach said:**
> Thanks, nickrout! This thread did have a fix:

[http://ubuntuforums.org/showthread.php?t=1956370](http://ubuntuforums.org/showthread.php?t=1956370)

The fix involves two config edits and a reboot:

1. Put the /tmp directory in a tmpfs filesystem by adding this line to /etc/fstab:

tmpfs   /tmp   tmpfs   nodev,nosuid    0 0

2. Add the following line to /etc/mysql/conf.d/mythtv.cnf:

default_storage_engine=MyISAM

This is different than the posts on page 4 of the thread above, which suggest putting this line either in /etc/mysql/conf.d/mythtv-tweaks.cnf or in /etc/init.d/mysql.

3. Reboot.

After this, mythfilldatabase ran at about the same speed as in 0.24, without all the disk thrashing. The thread above also explains what changed in MySQL that requires these changes.

Thanks again for the pointer!

Glad you found it and it worked! That was the thread I was thinking of :)

---

