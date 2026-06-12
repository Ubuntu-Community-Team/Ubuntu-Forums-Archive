---
title: "recordings drive replaced, but not working"
date: 2013-06-26
forum: Mythbuntu
---

### Post by davidstoll on 2013-06-26
I mounted a separate drive for storing recordings.  The drive went bad, I replaced it, put the files back and now it doesn't seem to be able to find the recordings, but can record new shows.  In the mythtv frontend it lists the previously recorded shows, I can confirm the file name (info, info), the file exists, but it can't play with the following error:  "Recording Unavailable.  The file for this recording can not be found"

mythbackend.log
```
Jun 26 19:56:08 MythBuntu mythbackend[2616]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 26 19:56:22 MythBuntu mythbackend[2616]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Jun 26 19:56:22 MythBuntu mythbackend[2616]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 176 items in 0.6 = 0.08 match + 0.55 place
Jun 26 19:56:28 MythBuntu mythbackend[2616]: E ProcessRequest programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(2060_20130618200000.mpg): GetPlaybackURL: '2060_20130618200000.mpg' should be local, but it can not be found.
```

Any suggestions?

---

### Post by klc5555 on 2013-06-27
Normally incorrect owner:group/permissions on the new drive. Assuming the new drive was mounted under /var/lib/mythtv/ , check drive, path, and files for mythtv:mythtv and permissions usually 755 or 775.

---

### Post by davidstoll on 2013-06-27
Mounted in /etc/fstab using uuid.  I just changed to the new uuid.
Mounted as /mythtv, but also made a symlink from /var/lib/mythtv.  I checked the backend to make sure it was pointing at the right path...tried both, just in case.
Everything was root:root, including the mount, so that was also changed to mythtv:mythtv and 755.

Seems to record just fine and the new files have the same perms as the old and are saved in the same location.

It just can't seem to play the old files.



> **klc5555 said:**
> Normally incorrect owner:group/permissions on the new drive. Assuming the new drive was mounted under /var/lib/mythtv/ , check drive, path, and files for mythtv:mythtv and permissions usually 755 or 775.

---

### Post by klc5555 on 2013-06-27
New files record on the drive, but do they play? This isn't clear from the posts. If nothing on the drive plays, then this would still point to permission issues. Maybe from mounting the drive as a root directory (/mythtv) with a symlink to /var/lib/mythtv rather than mounting the drive directly to (or under) /var/lib/mythtv/ with the correct owner:group permissions set. Was there a reboot/restart after all the permissions editing? Was mythbackend restarted?

If new recordings play but not older ones with which they are interfiled in the same directory, then I'd suspect (if the restored recordings files are not themselves corrupt or otherwise altered) that something is amiss with mythconverg, but I'm not presently sure what.

---

### Post by davidstoll on 2013-06-27
The new recordings play also.  The old files were from a backup and they play outside of mythtv (vlc or whatever), so they are not corrupted.  I just remounted to /var/lib/mythtv/ and changed the pointer in the backend, but still no luck.  In any case, mounting to a different location worked before and the new recordings are going whereever I tell it.

Yes the backend has been stopped and restarted several times and I have also rebooted a couple of times.

Is there a command to refresh mythconverg (something non-destructive...i.e. not a sledge hammer)?

David



> **klc5555 said:**
> New files record on the drive, but do they play? This isn't clear from the posts. If nothing on the drive plays, then this would still point to permission issues. Maybe from mounting the drive as a root directory (/mythtv) with a symlink to /var/lib/mythtv rather than mounting the drive directly to (or under) /var/lib/mythtv/ with the correct owner:group permissions set. Was there a reboot/restart after all the permissions editing? Was mythbackend restarted?

If new recordings play but not older ones with which they are interfiled in the same directory, then I'd suspect (if the restored recordings files are not themselves corrupt or otherwise altered) that something is amiss with mythconverg, but I'm not presently sure what.

---

### Post by klc5555 on 2013-06-27
Well, if there is a problem with mythconverg, mysqlcheck may pull it up.

Probably something along the lines of ```
$mysqlcheck -u mythtv -p[mysql-password-with-no-space-after-the-"p"] -A -e
``` to perform the most thorough check, which will take a bit of time. Then if something is reported amiss, it can be normally be fixed running mysqlcheck again with the "--auto-repair" option added.

Of course, as always, before running any repair routine on your database, if you decide to run one, do a mythconverg backup first.

---

### Post by davidstoll on 2013-06-27
Everything basically looks ok.
```
$ mysqlcheck -u mythtv -pXXXXXXXX -A -e
mythconverg.archiveitems                           OK
mythconverg.callsignnetworkmap                     OK
mythconverg.capturecard                            OK
mythconverg.cardinput                              OK
mythconverg.channel                                OK
mythconverg.channelgroup                           OK
mythconverg.channelgroupnames                      OK
mythconverg.channelscan                            OK
mythconverg.channelscan_channel                    OK
mythconverg.channelscan_dtv_multiplex              OK
mythconverg.codecparams                            OK
mythconverg.credits                                OK
mythconverg.customexample                          OK
mythconverg.diseqc_config                          OK
mythconverg.diseqc_tree                            OK
mythconverg.displayprofilegroups                   OK
mythconverg.displayprofiles                        OK
mythconverg.dtv_multiplex                          OK
mythconverg.dtv_privatetypes                       OK
mythconverg.dvdbookmark                            OK
mythconverg.dvdinput                               OK
mythconverg.dvdtranscode                           OK
mythconverg.eit_cache                              OK
mythconverg.filemarkup                             OK
mythconverg.gallerymetadata                        OK
mythconverg.gamemetadata                           OK
mythconverg.gameplayers                            OK
mythconverg.housekeeping                           OK
mythconverg.inputgroup                             OK
mythconverg.internetcontent                        OK
mythconverg.internetcontentarticles                OK
mythconverg.inuseprograms                          OK
mythconverg.jobqueue                               OK
mythconverg.jumppoints                             OK
mythconverg.keybindings                            OK
mythconverg.keyword                                OK
mythconverg.livestream                             OK
mythconverg.logging                                OK
mythconverg.movies_movies                          OK
mythconverg.movies_showtimes                       OK
mythconverg.movies_theaters                        OK
mythconverg.music_albumart                         OK
mythconverg.music_albums                           OK
mythconverg.music_artists                          OK
mythconverg.music_directories                      OK
mythconverg.music_genres                           OK
mythconverg.music_playlists                        OK
mythconverg.music_smartplaylist_categories         OK
mythconverg.music_smartplaylist_items              OK
mythconverg.music_smartplaylists                   OK
mythconverg.music_songs                            OK
mythconverg.music_stats                            OK
mythconverg.mythexport                             OK
mythconverg.mythexport_job_queue                   OK
mythconverg.mythlog                                OK
mythconverg.mythweb_sessions                       OK
mythconverg.networkiconmap                         OK
mythconverg.newssites                              OK
mythconverg.oldfind                                OK
mythconverg.oldprogram                             OK
mythconverg.oldrecorded                            OK
mythconverg.people                                 OK
mythconverg.phonecallhistory                       OK
mythconverg.phonedirectory                         OK
mythconverg.pidcache                               OK
mythconverg.playgroup                              OK
mythconverg.powerpriority                          OK
mythconverg.profilegroups                          OK
mythconverg.program                                OK
mythconverg.programgenres                          OK
mythconverg.programrating                          OK
mythconverg.recgrouppassword                       OK
mythconverg.record                                 OK
mythconverg.record_tmp                             OK
mythconverg.recorded                               OK
mythconverg.recordedartwork                        OK
mythconverg.recordedcredits                        OK
mythconverg.recordedfile                           OK
mythconverg.recordedmarkup                         OK
mythconverg.recordedprogram                        OK
mythconverg.recordedrating                         OK
mythconverg.recordedseek                           OK
mythconverg.recordfilter                           OK
mythconverg.recordingprofiles                      OK
mythconverg.recordmatch                            OK
mythconverg.romdb                                  OK
mythconverg.schemalock                             OK
mythconverg.settings                               OK
mythconverg.storagegroup                           OK
mythconverg.tvchain                                OK
mythconverg.tvosdmenu                              OK
mythconverg.upnpmedia                              OK
mythconverg.videocast                              OK
mythconverg.videocategory                          OK
mythconverg.videocollection                        OK
mythconverg.videocountry                           OK
mythconverg.videogenre                             OK
mythconverg.videometadata                          OK
mythconverg.videometadatacast                      OK
mythconverg.videometadatacountry                   OK
mythconverg.videometadatagenre                     OK
mythconverg.videopathinfo                          OK
mythconverg.videosource                            OK
mythconverg.videotypes                             OK
mythconverg.weatherdatalayout
Error    : Table 'mythconverg.weatherdatalayout' doesn't exist
status   : Operation failed
mythconverg.weatherscreens
Error    : Table 'mythconverg.weatherscreens' doesn't exist
status   : Operation failed
mythconverg.weathersourcesettings
Error    : Table 'mythconverg.weathersourcesettings' doesn't exist
status   : Operation failed
mythconverg.websites                             OK
```

Should I go ahead and run the auto repair?  I'm not sure it's going to do anything for me.

One strange thing, I did a mythconverge backup and the file is very small (a few kb vs 15MB) compared to some much older backups (unfortunately, I don't have a recent backup).

Thanks again



> **klc5555 said:**
> Well, if there is a problem with mythconverg, mysqlcheck may pull it up.

Probably something along the lines of ```
$mysqlcheck -u mythtv -p[mysql-password-with-no-space-after-the-"p"] -A -e
``` to perform the most thorough check, which will take a bit of time. Then if something is reported amiss, it can be normally be fixed running mysqlcheck again with the "--auto-repair" option added.

Of course, as always, before running any repair routine on your database, if you decide to run one, do a mythconverg backup first.

---

### Post by klc5555 on 2013-06-27
> **davidstoll said:**
> 

Should I go ahead and run the auto repair?  I'm not sure it's going to do anything for me.

One strange thing, I did a mythconverge backup and the file is very small (a few kb vs 15MB) compared to some much older backups (unfortunately, I don't have a recent backup).

Thanks again

No, I don't think a repair operation here will actually give you anything useful.

Like you, I find the small size of the backup a little odd --a pity you didn't have your installation set up do a standard daily mythconverg backup. Still, there should at least be weekly automatic backups that have been dropped in some directory like /var/lib/db_backups in a default installation.

I confess I have no idea at this point what the issue might be that would affect the accessibility of older and only older recordings. I wonder what the find_orphans.py script would show regarding orphaned recordings files and/or orphaned database entries. Maybe some unusual path issue, in case the older recordings are in a different directory than the newer ones are landing in, somewhere other than where mythbackend knows the newer recordings to be located. But at this juncture it's just guesswork.

---

### Post by PhilWig on 2013-06-27
I have had an instance of a stable backup strategy which inexplicably started failing due a lost link.  In my case, I was running the backups under mythtv and the lost link was:

/home/mythtv/.mythtv/config.xml  --> /etc/mythtv/config.xml 

but check your appropriate backup user.

As klc5555 suggests, find_orphans.py is a good consistency checker.

Phil

---

### Post by davidstoll on 2013-06-27
The (small) backup contains only this:
```
$ cat mythconverg-1299-20130627113604.sql
-- MySQL dump 10.13  Distrib 5.5.31, for debian-linux-gnu (i686)
--
-- Host: localhost    Database: mythconverg
-- ------------------------------------------------------
-- Server version       5.5.31-0ubuntu0.12.04.2

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;
```

I did a find for the file find_orphans.py, but I guess I don't have it.



> **PhilWig said:**
> I have had an instance of a stable backup strategy which inexplicably started failing due a lost link.  In my case, I was running the backups under mythtv and the lost link was:

/home/mythtv/.mythtv/config.xml  --> /etc/mythtv/config.xml 

but check your appropriate backup user.

As klc5555 suggests, find_orphans.py is a good consistency checker.

Phil

---

### Post by klc5555 on 2013-06-27
> **davidstoll said:**
> The (small) backup contains only this:
```
$ cat mythconverg-1299-20130627113604.sql
-- MySQL dump 10.13  Distrib 5.5.31, for debian-linux-gnu (i686)
--
-- Host: localhost    Database: mythconverg
-- ------------------------------------------------------
-- Server version       5.5.31-0ubuntu0.12.04.2

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;
```

I did a find for the file find_orphans.py, but I guess I don't have it.

Clearly the backup you're getting is defective. Try one by hand, with something like:```
$mysqldump -u mythtv -p[mysql-password-with-no-space-after-"p"] mythconverg -c | gzip -c > mythconvergbackup.sql.gz 
```If it blows up and the gzip file "mythconvergbackup.sql.gz" comes out way short again, then there really is a problem with mythconverg for repair --mysqldump won't process a defective database.

The find_orphans.py script is gotten from the wiki: [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

---

### Post by davidstoll on 2013-06-27
So, find_orphans.py found all the files and categorized them under "Recordings with missing files", but I can only delete them....but at least it sees them.

I ran mysqlcheck with --auto-repair, but as we suspected, no help.

Also,
```
$mysqldump -u mythtv -pXXXXXXXX mythconverge -c | gzip -c mythconvergbackup.sql.gz
gzip: mythconvergbackup.sql.gz: No such file or directory
mysqldump: Got error: 1044: Access denied for user 'mythtv'@'localhost' to database 'mythconverge' when selecting the database
```


> **klc5555 said:**
> Clearly the backup you're getting is defective. Try one by hand, with something like:```
$mysqldump -u mythtv -p[mysql-password-with-no-space-after-"p"] mythconverg -c | gzip -c > mythconvergbackup.sql.gz 
```If it blows up and the gzip file "mythconvergbackup.sql.gz" comes out way short again, then there really is a problem with mythconverg for repair --mysqldump won't process a defective database.

The find_orphans.py script is gotten from the wiki: [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

---

### Post by klc5555 on 2013-06-27
Misspelled "mythconverg" in the mysqldump command.

Also, if find_orphans.py found all earlier as "recordings with missing files", then it found the database entries for the recordings, but not the actual files. If the actual files had been found (but not the database entries), then the files would have been categorized as "Orphaned video files" This would imply that the files are in some directory other than where the backend (and mythconverg) expect to find them. Are the new recordings that can be found really ending up in the same directory as the old ones that can't?

---

### Post by davidstoll on 2013-06-27
I know exactly what you are saying and I know it sounds strange based on the orphan script, but the newly recorded files are being saved in the same folder as dozens and dozens of other previously recorded files.

There have only been a couple of test recordings (2-3), but when I do an "ls -l", I see those 2-3 files and dozens of other mpg files using that same numeric naming convention...I can play them with vlc and know they are the old recordings.




> **klc5555 said:**
> Misspelled "mythconverg" in the mysqldump command.

Also, if find_orphans.py found all earlier as "recordings with missing files", then it found the database entries for the recordings, but not the actual files. If the actual files had been found (but not the database entries), then the files would have been categorized as "Orphaned video files" This would imply that the files are in some directory other than where the backend (and mythconverg) expect to find them. Are the new recordings that can be found really ending up in the same directory as the old ones that can't?

---

### Post by PhilWig on 2013-06-28
Some shots in the dark:

1.  Any hints here?     [http://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions](http://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions)

2.  Is your symlink:    /var/lib/mythtv/recordings ->  /mythtv ?

I've seen somewhere that recordings cannot be at top level in a partition.  This url suggests it unwise but I've seen a stronger issue somewhere else:   [http://www.mythtv.org/wiki/Storage_Groups#Directory_Structure](http://www.mythtv.org/wiki/Storage_Groups#Directory_Structure)

3.  If you compare an old and a new recording with fronted 'watch recordings',  right arrow, recording options, show recording details, then 'i'  then do you see any differences near the bottom of the list?

Phil

---

### Post by davidstoll on 2013-06-28
1.  The problem here is that the old and new files have the same perms.  Nothing looks out of sorts according to this page.

2.  No, the symlink is /var/lib/mythtv/ -> /mythtv/
So, /var/lib/mythtv/recordings/  goes to  /mythtv/recordings/

3. i, i (i.e. info twice) gives me the name of the file 2060_2013xxxxxxx.mpg (where xxxx's are whatever numbers), whether is be old or new.  For old recordings, I did an ls for that exact file name in /recordings, and it finds the file.  Everything else looks basically in order.

Is there a different log that can clue me in (different from what I referenced before)?



> **PhilWig said:**
> Some shots in the dark:

1.  Any hints here?     [http://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions](http://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions)

2.  Is your symlink:    /var/lib/mythtv/recordings ->  /mythtv ?

I've seen somewhere that recordings cannot be at top level in a partition.  This url suggests it unwise but I've seen a stronger issue somewhere else:   [http://www.mythtv.org/wiki/Storage_Groups#Directory_Structure](http://www.mythtv.org/wiki/Storage_Groups#Directory_Structure)

3.  If you compare an old and a new recording with fronted 'watch recordings',  right arrow, recording options, show recording details, then 'i'  then do you see any differences near the bottom of the list?

Phil

---

### Post by klc5555 on 2013-06-28
Since we're at the shot-in-the-dark stage:

I might try closing down your frontend, which runs as your normal user, and run one from a terminal sudo:```
$sudo mythfrontend
``` If a frontend run with root permissions can find and run the old recordings along with the new from the same directory, then there must be a permissions issue to correct with the old files. 

Conversely, you could temporarily open up access on your recordings drive to wide open, to see if the old recordings are now accessible for user's mythfrontend along with the new:```
$sudo chmod -R 777  /mythtv
``` If this works, the permissions will eventually be clamped down again later.

I'm reluctant to suggest any tests that involve the database, since you haven't managed to get a usable backup yet. In the long run, this is a more serious problem than the current frustration of fixing the accessibility of the older recordings.

---

### Post by tgm4883 on 2013-06-28
> **klc5555 said:**
> Since we're at the shot-in-the-dark stage:

I might try closing down your frontend, which runs as your normal user, and run one from a terminal sudo:```
$sudo mythfrontend
``` If a frontend run with root permissions can find and run the old recordings along with the new from the same directory, then there must be a permissions issue to correct with the old files. 


I've not read though this whole thread yet, but I had to comment on this. This will not work, as the frontend should be asking the backend for the recording and not looking at the filesystem directly.

> **klc5555 said:**
> 
Conversely, you could temporarily open up access on your recordings drive to wide open, to see if the old recordings are now accessible for user's mythfrontend along with the new:```
$sudo chmod -R 777  /mythtv
``` If this works, the permissions will eventually be clamped down again later.

I'm reluctant to suggest any tests that involve the database, since you haven't managed to get a usable backup yet. In the long run, this is a more serious problem than the current frustration of fixing the accessibility of the older recordings.

I agree that there shouldn't be any reason to mess with the database.

---

### Post by tgm4883 on 2013-06-28
Ok, just read though the rest of the thread. I don't think it's a permissions problem, as you can already write and read from there (I'm assuming you mean recordings and not live tv). Can you please post the output from the following commands?



```
mysql -u mythtv -p mythconverg -e 'select title, subtitle, basename, storagegroup from recorded;'
```

```
mysql -u mythtv -p mythconverg -e 'select * from storagegroup;'
```

---

### Post by davidstoll on 2013-06-28
$sudo mythfrontend
```
You must be a member of the "mythtv" group before starting any mythtv applications.
Would you like to automatically be added to the group?
(Note: sudo access required).
```

So, I canceled out.




> **tgm4883 said:**
> I've not read though this whole thread yet, but I had to comment on this. This will not work, as the frontend should be asking the backend for the recording and not looking at the filesystem directly.



I agree that there shouldn't be any reason to mess with the database.

---

### Post by davidstoll on 2013-06-28
mysql -u mythtv -p mythconverg -e 'select title, subtitle, basename, storagegroup from recorded;'
```
+----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------+--------------+
| title                                                          | subtitle                            | basename                 | storagegroup |
+----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------+--------------+
| Unknown                                                        |                                     | 66261_20110521235143.mpg | LiveTV       |
| Family Guy                                                     | Stuck Together, Torn Apart          | 1171_20110522005340.mpg  | LiveTV       |
| Unknown                                                        |                                     | 12924_20110522011244.mpg | LiveTV       |
| Unknown                                                        |                                     | 3927_20110522011248.mpg  | LiveTV       |
| Unknown                                                        |                                     | 12945_20110522011250.mpg | LiveTV       |
| Unknown                                                        |                                     | 66429_20110522011253.mpg | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235145.mpg  | LiveTV       |
| Unknown                                                        |                                     | 66261_20110521235144.mpg | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235309.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235319.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110522005352.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110522005353.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235227.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235226.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110521235232.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110521235233.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235250.mpg  | LiveTV       |
| Unknown                                                        |                                     | 66391_20110521235300.mpg | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235308.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235156.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235157.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235158.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235205.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235206.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110521235208.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110521235209.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3131_20110521235256.mpg  | LiveTV       |
| Fringe                                                         | Of Human Action                     | 1171_20110521235320.mpg  | LiveTV       |
| Unknown                                                        |                                     | 66423_20110522011233.mpg | LiveTV       |
| Unknown                                                        |                                     | 3877_20110522011235.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3880_20110522011237.mpg  | LiveTV       |
| Unknown                                                        |                                     | 12908_20110522011241.mpg | LiveTV       |
| Family Guy                                                     | Stuck Together, Torn Apart          | 1171_20110522005341.mpg  | LiveTV       |
| Unknown                                                        |                                     | 3761_20110522005400.mpg  | LiveTV       |
| Unknown                                                        |                                     | 66421_20110522011230.mpg | LiveTV       |
| Family Guy                                                     | Blue Harvest, Part 1                | 3761_20110613210000.mpg  | Default      |
| Family Guy                                                     | Blue Harvest, Part 2                | 3761_20110613213000.mpg  | Default      |
| Family Guy                                                     | Something, Something, Something Dark Side, Part 1          | 3761_20110613220000.mpg  | Default      |
| Family Guy                                                     | Something, Something, Something Dark Side, Part 2          | 3761_20110613223000.mpg  | Default      |
| Planet Mancow                                                  |                                     | 2060_20120805010000.mpg  | Default      |
| NOVA                                                           | Venom: Nature's Killer              | 1521_20120530210000.mpg  | Default      |
| NOVA                                                           | The Fabric of the Cosmos: The Illusion of Time             | 1521_20120718210000.mpg  | Default      |
| PBS NewsHour                                                   |                                     | 1521_20120713192503.mpg  | LiveTV       |
| NOVA                                                           | The Fabric of the Cosmos: Quantum Leap                     | 1521_20120725210000.mpg  | Default      |
| The Electric Playground                                        |                                     | 1082_20120715003000.mpg  | Default      |
| NOVA                                                           | The Elegant Universe: Welcome to the 11th Dimension          | 1521_20120728040000.mpg  | Default      |
| WordWorld                                                      | Robots to the Rescue!; Radio Read-a-Thon                   | 1521_20120808112700.mpg  | Default      |
| Everybody Loves Raymond                                        | Fun With Debra                      | 1171_20120903010000.mpg  | Default      |
| NOVA                                                           | What Are Dreams?                    | 1521_20120822210000.mpg  | Default      |
| Falling Skies                                                  | A More Perfect Union                | 2054_20120819210000.mpg  | Default      |
| Everybody Loves Raymond                                        | Debra at the Lodge                  | 1171_20120910010000.mpg  | Default      |
| Friends                                                        | The One With Phoebe's Cookies                              | 1171_20120907150000.mpg  | Default      |
| Seinfeld                                                       | The Suicide                         | 1082_20120906230000.mpg  | Default      |
| Friends                                                        | The One With the Prom Video                                | 1171_20120907153000.mpg  | Default      |
| Seinfeld                                                       | The Subway                          | 1082_20120907230000.mpg  | Default      |
| NOVA                                                           | Making Stuff: Making Stuff Smaller                         | 1521_20120919220000.mpg  | Default      |
| NOVA                                                           | Making Stuff: Making Stuff Stronger                        | 1521_20120919210000.mpg  | Default      |
| Franklin & Bash                                                | Jango and Rossi                     | 3761_20120922220000.mpg  | Default      |
| South Park                                                     |                                     | 2057_20121003220000.mpg  | Default      |
| Franklin & Bash                                                | Waiting on a Friend                 | 3761_20120929220000.mpg  | Default      |
| NOVA                                                           | Making Stuff: Making Stuff Cleaner                         | 1521_20120926210000.mpg  | Default      |
| South Park                                                     | Sarcastaball                        | 2057_20120926220000.mpg  | Default      |
| NOVA                                                           | Making Stuff: Making Stuff Smarter                         | 1521_20120926220000.mpg  | Default      |
| Top 20 Most Shocking                                           | Summer Blowouts                     | 2061_20121027180000.mpg  | Default      |
| NOVA                                                           | Secrets of the Viking Sword                                | 1521_20121010210000.mpg  | Default      |
| South Park                                                     | Insecurity                          | 2057_20121010220000.mpg  | Default      |
| NOVA                                                           | Forensics on Trial                  | 1521_20121017210000.mpg  | Default      |
| South Park                                                     |                                     | 2057_20121017220000.mpg  | Default      |
| Top 20 Most Shocking                                           | Practical Jokers Gone Wild 4                               | 2061_20121020180000.mpg  | Default      |
| Top 20 Most Shocking                                           | Summer Blowouts 2                   | 2061_20121021180000.mpg  | Default      |
| WordWorld                                                      | A Kooky Spooky Halloween; Sheep's Halloween Costume          | 1351_20121026120000.mpg  | Default      |
| The King of Queens                                             | Raygin' Bulls                       | 3761_20121022183000.mpg  | Default      |
| Top 20 Most Shocking                                           |                                     | 2061_20121025210000.mpg  | Default      |
| Conan                                                          |                                     | 3761_20121025230000.mpg  | Default      |
| NOVA                                                           | Iceman Murder Mystery               | 1521_20121024210000.mpg  | Default      |
| South Park                                                     | A Nightmare On FaceTime             | 2057_20121024220000.mpg  | Default      |
| Franklin & Bash                                                | Good Lovin'                         | 2054_20130626205900.mpg  | Default      |
| Jeopardy!                                                      |                                     | 1031_20130626194000.mpg  | Default      |
| Conan                                                          |                                     | 3762_20130626230000.mpg  | Default      |
| The Colbert Report                                             | Bill Moyers                         | 2057_20130627093000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130627213000.mpg  | Default      |
| South Park                                                     | A Scause for Applause               | 2057_20121031220000.mpg  | Default      |
| America's Got Talent                                           |                                     | 1081_20130627220100.mpg  | Default      |
| Conan                                                          |                                     | 3762_20130627225900.mpg  | Default      |
| The Colbert Report                                             | The Postal Service                  | 2057_20130628092900.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130609195800.mpg  | Default      |
| NOVA                                                           | Oklahoma's Deadliest Tornadoes                             | 1521_20130529220000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130228182900.mpg  | Default      |
| The Colbert Report                                             | Daniel Bergner                      | 2057_20130618093000.mpg  | Default      |
| The Numbers Game                                               | Will You Make a Million?            | 2048_20130527190000.mpg  | Default      |
| South Park                                                     | City Sushi                          | 2057_20130515220000.mpg  | Default      |
| Black Knight                                                   |                                     | 2023_20121109224753.mpg  | LiveTV       |
| Tosh.0                                                         |                                     | 2057_20130618115000.mpg  | Default      |
| Brain Games                                                    | Focus Pocus                         | 2048_20130422210000.mpg  | Default      |
| America's Got Talent                                           |                                     | 1081_20130618200000.mpg  | Default      |
| Falling Skies                                                  | Badlands                            | 2054_20130616220000.mpg  | Default      |
| Black Knight                                                   |                                     | 2023_20121109224807.mpg  | LiveTV       |
| NOVA                                                           | Building Pharaoh's Chariot          | 1521_20130209030000.mpg  | Default      |
| Black Knight                                                   |                                     | 2023_20121109224808.mpg  | LiveTV       |
| NOVA                                                           | Building the Great Cathedrals                              | 1521_20121226210000.mpg  | Default      |
| The Numbers Game                                               | Will You Make a Million?            | 2048_20130603150000.mpg  | Default      |
| Impractical Jokers                                             | Sound EffeXXX                       | 2061_20130307213000.mpg  | Default      |
| Ron White's Vegas Salute to the Troops 2013                    |                                     | 2075_20130315220000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130531182000.mpg  | Default      |
| Brain Games                                                    | Remember This!                      | 2048_20130425200000.mpg  | Default      |
| Unknown                                                        |                                     | 10000_20121126220743.mpg | LiveTV       |
| Unknown                                                        |                                     | 10000_20121126231500.mpg | LiveTV       |
| Unknown                                                        |                                     | 10000_20121126230612.mpg | LiveTV       |
| Saturday Night Live                                            |                                     | 1081_20130518232800.mpg  | Default      |
| NOVA                                                           | Space Shuttle Disaster              | 1521_20130203180000.mpg  | Default      |
| WordWorld                                                      | The Christmas Star; A Christmas Present for Dog            | 1351_20121221120000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130605000100.mpg  | Default      |
| Brain Games                                                    | Seeing is Believing                 | 2048_20130603170000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130529182600.mpg  | Default      |
| NOVA                                                           | Who Killed Lindbergh's Baby?                               | 1521_20130202030000.mpg  | Default      |
| NOVA                                                           | Rise of the Drones                  | 1521_20130126030000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130201003000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130611132300.mpg  | Default      |
| America's Got Talent                                           | Premiere                            | 1081_20130609210000.mpg  | Default      |
| Yule Log                                                       |                                     | 1171_20121225073200.mpg  | Default      |
| Brain Games                                                    | It's About Time                     | 2048_20130422213000.mpg  | Default      |
| South Park                                                     | Fatbeard                            | 2057_20130501220000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130614182000.mpg  | Default      |
| Conan                                                          |                                     | 3762_20130618230000.mpg  | Default      |
| America's Got Talent                                           |                                     | 1081_20130611210100.mpg  | Default      |
| Brain Games                                                    | Watch This!                         | 2048_20130429200000.mpg  | Default      |
| Brain Games                                                    | You Decide                          | 2048_20130603210000.mpg  | Default      |
| Insanity Workout                                               |                                     | 2058_20130407160600.mpg  | Default      |
| NOVA                                                           | Russian Meteor Strike               | 1521_20130330030000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130612000000.mpg  | Default      |
| Brain Games                                                    | Use It or Lose It                   | 2048_20130610210000.mpg  | Default      |
| South Park                                                     | You Have 0 Friends                  | 2057_20130529215900.mpg  | Default      |
| Brain Games                                                    | Pay Attention!                      | 2048_20130603200000.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130603182700.mpg  | Default      |
| Tosh.0                                                         |                                     | 2057_20130530182100.mpg  | Default      |
+----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------+--------------+
```


mysql -u mythtv -p mythconverg -e 'select * from storagegroup;'
```
+----+-------------+-----------+----------------------+
| id | groupname   | hostname  | dirname              |
+----+-------------+-----------+----------------------+
| 19 | Default     | MythBuntu | /mythtv/recordings/  |
| 14 | Videos      | MythBuntu | /mythtv/videos/      |
| 16 | Fanart      | MythBuntu | /mythtv/fanart/      |
| 15 | Trailers    | MythBuntu | /mythtv/trailers/    |
| 11 | Coverart    | MythBuntu | /mythtv/coverart/    |
| 17 | Screenshots | MythBuntu | /mythtv/screenshots/ |
| 18 | Banners     | MythBuntu | /mythtv/banners/     |
| 13 | DB Backups  | MythBuntu | /mythtv/db_backups/  |
| 12 | LiveTV      | MythBuntu | /mythtv/livetv/      |
+----+-------------+-----------+----------------------+
```


> **tgm4883 said:**
> Ok, just read though the rest of the thread. I don't think it's a permissions problem, as you can already write and read from there (I'm assuming you mean recordings and not live tv). Can you please post the output from the following commands?



```
mysql -u mythtv -p mythconverg -e 'select title, subtitle, basename, storagegroup from recorded;'
```

```
mysql -u mythtv -p mythconverg -e 'select * from storagegroup;'
```

---

### Post by tgm4883 on 2013-06-28
Ok, can you also give us the following information.

1) The Title & Subtitle of a show that DOES work.

2) The Title & Subtitle of a show that does NOT work.

3) The output of the following 3 commands.

```
ls -l /mythtv
```

```
ls -l /mythtv/livetv/
```

```
ls -l /mythtv/recordings/
```

Also, can you confirm that new RECORDINGS (read, NOT livetv) work?

---

### Post by davidstoll on 2013-07-02
1)
Tosh.0
Daniel tackles the issue of bullying...

2)
Tosh.0
Interview with Fred...

3)
```
$ls -l /mythtv
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 banners
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 coverart
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 db_backups
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 fanart
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 livetv
drwxrwxr-x  2 mythtv mythtv  16384 May 15  2011 lost+found
drwxrwxr-x  2 mythtv mythtv   4096 May 15  2011 music
drwxrwxr-x  2 mythtv mythtv   4096 May 15  2011 mythexport
drwxrwxr-x  2 mythtv mythtv   4096 May 15  2011 pictures
drwxrwxr-x  4 mythtv mythtv  28672 Jul  2 17:55 recordings
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 screenshots
drwxrwxr-x  6 mythtv mythtv   4096 May 23  2011 temp
drwxrwxr-x  2 mythtv mythtv   4096 Jul  2 17:48 trailers
drwxrwxr-x  3 mythtv mythtv   4096 Jul  2 17:48 videos
```

```
$ ls -l /mythtv/livetv/
total 4488
-rw-r--r-- 1 mythtv mythtv       0 Jul  2 17:59 2057_20130702175950.mpg
-rw-r--r-- 1 mythtv mythtv 4487104 Jul  2 18:00 2057_20130702175951.mpg
-rw-rw-rw- 1 mythtv mythtv   89907 Jul  2 18:01 2057_20130702175951.mpg.png
```

```
$ ls -l
total 367210488
-rw-r--r-- 1 mythtv mythtv  2045129988 Jun 26 20:01 1031_20130626194000.mpg
-rw-rw-rw- 1 mythtv mythtv       76833 Jun 26 20:01 1031_20130626194000.mpg.png
-rw-r--r-- 1 mythtv mythtv  9939012544 May 19 01:08 1081_20130518232800.mpg
-rw-rw-rw- 1 mythtv mythtv       10006 Jun  7 10:51 1081_20130518232800.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       83785 May 21 21:27 1081_20130518232800.mpg.png
-rw-r--r-- 1 mythtv mythtv 12223475744 Jun  9 23:01 1081_20130609210000.mpg
-rw-rw-rw- 1 mythtv mythtv       32109 Jun 15 08:08 1081_20130609210000.mpg.png
-rw-r--r-- 1 mythtv mythtv 12368296092 Jun 11 23:01 1081_20130611210100.mpg
-rw-rw-rw- 1 mythtv mythtv      112225 Jun 11 23:01 1081_20130611210100.mpg.png
-rw-r--r-- 1 mythtv mythtv  6019757368 Jun 27 23:01 1081_20130627220100.mpg
-rw-rw-rw- 1 mythtv mythtv       82061 Jun 27 23:01 1081_20130627220100.mpg.png
-rw-r--r-- 1 mythtv mythtv   920352308 Jul 15  2012 1082_20120715003000.mpg
-rw-rw-rw- 1 mythtv mythtv      114618 Jul 15  2012 1082_20120715003000.mpg.png
-rw-r--r-- 1 mythtv mythtv   802968492 Sep  6  2012 1082_20120906230000.mpg
-rw-rw-rw- 1 mythtv mythtv      105096 Sep  6  2012 1082_20120906230000.mpg.png
-rw-r--r-- 1 mythtv mythtv   836520476 Sep  7  2012 1082_20120907230000.mpg
-rw-rw-rw- 1 mythtv mythtv      115600 Sep 14  2012 1082_20120907230000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2105891964 Sep  3  2012 1171_20120903010000.mpg
-rw-rw-rw- 1 mythtv mythtv       83782 Sep  3  2012 1171_20120903010000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1969287028 Sep  7  2012 1171_20120907150000.mpg
-rw-rw-rw- 1 mythtv mythtv       76523 Sep  7  2012 1171_20120907150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2128996036 Sep  7  2012 1171_20120907153000.mpg
-rw-rw-rw- 1 mythtv mythtv       95087 Sep  7  2012 1171_20120907153000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1894881704 Sep 10  2012 1171_20120910010000.mpg
-rw-rw-rw- 1 mythtv mythtv       80776 Sep 10  2012 1171_20120910010000.mpg.png
-rw-r--r-- 1 mythtv mythtv  7574615692 Dec 25  2012 1171_20121225073200.mpg
-rw-rw-rw- 1 mythtv mythtv        9974 Feb  5 22:41 1171_20121225073200.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       80472 Dec 26  2012 1171_20121225073200.mpg.png
-rw-r--r-- 1 mythtv mythtv 10968585896 Jun  7 09:01 1171_20130607070000.mpg
-rw-rw-rw- 1 mythtv mythtv       10323 Jun  7 10:51 1171_20130607070000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv      102239 Jun  7 18:09 1171_20130607070000.mpg.png
-rw-r--r-- 1 mythtv mythtv   531362636 Jun 15 08:17 1171_20130615081100.mpg
-rw-rw-rw- 1 mythtv mythtv       79400 Jun 15 15:34 1171_20130615081100.mpg.png
-rw-r--r-- 1 mythtv mythtv  2868252456 Oct 26  2012 1351_20121026120000.mpg
-rw-rw-rw- 1 mythtv mythtv       11366 Feb  5 22:41 1351_20121026120000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       92077 Oct 26  2012 1351_20121026120000.mpg.png
-rw-r--r-- 1 mythtv mythtv  3191763044 Dec 21  2012 1351_20121221120000.mpg
-rw-rw-rw- 1 mythtv mythtv        9750 Feb  5 22:41 1351_20121221120000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       77594 Dec 21  2012 1351_20121221120000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5755116160 May 30  2012 1521_20120530210000.mpg
-rw-rw-rw- 1 mythtv mythtv       36848 Jan 28 21:29 1521_20120530210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5675920596 Jul 18  2012 1521_20120718210000.mpg
-rw-rw-rw- 1 mythtv mythtv      122372 Dec  9  2012 1521_20120718210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5696849132 Jul 25  2012 1521_20120725210000.mpg
-rw-rw-rw- 1 mythtv mythtv       50825 Dec 14  2012 1521_20120725210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5747373192 Jul 28  2012 1521_20120728040000.mpg
-rw-rw-rw- 1 mythtv mythtv        1148 Dec 27  2012 1521_20120728040000.mpg.png
-rw-r--r-- 1 mythtv mythtv  3109198520 Aug  8  2012 1521_20120808112700.mpg
-rw-rw-rw- 1 mythtv mythtv       79709 Aug  8  2012 1521_20120808112700.mpg.png
-rw-r--r-- 1 mythtv mythtv  5554307532 Aug 22  2012 1521_20120822210000.mpg
-rw-rw-rw- 1 mythtv mythtv       66478 Jan 16 21:39 1521_20120822210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5763744796 Sep 19  2012 1521_20120919210000.mpg
-rw-rw-rw- 1 mythtv mythtv       10734 Feb  5 22:41 1521_20120919210000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       77940 Sep 19  2012 1521_20120919210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5807212840 Sep 19  2012 1521_20120919220000.mpg
-rw-rw-rw- 1 mythtv mythtv       11939 Feb  5 22:41 1521_20120919220000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       93353 Sep 19  2012 1521_20120919220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5832715792 Sep 26  2012 1521_20120926210000.mpg
-rw-rw-rw- 1 mythtv mythtv       11274 Feb  5 22:41 1521_20120926210000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv      100234 Sep 26  2012 1521_20120926210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5835803692 Sep 26  2012 1521_20120926220000.mpg
-rw-rw-rw- 1 mythtv mythtv        7505 Feb  5 22:41 1521_20120926220000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       59145 Sep 29  2012 1521_20120926220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5769477292 Oct 10  2012 1521_20121010210000.mpg
-rw-rw-rw- 1 mythtv mythtv      101803 Jan 21 21:12 1521_20121010210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5782737496 Oct 17  2012 1521_20121017210000.mpg
-rw-rw-rw- 1 mythtv mythtv       12700 Feb  5 22:41 1521_20121017210000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv      107147 Mar 14 22:49 1521_20121017210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5849686928 Oct 24  2012 1521_20121024210000.mpg
-rw-rw-rw- 1 mythtv mythtv       46167 Jan 20 05:47 1521_20121024210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6310649392 Dec 26  2012 1521_20121226210000.mpg
-rw-rw-rw- 1 mythtv mythtv       11584 Feb  5 22:41 1521_20121226210000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       98329 Dec 26  2012 1521_20121226210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6199192464 Jan 26 04:01 1521_20130126030000.mpg
-rw-rw-rw- 1 mythtv mythtv        7969 Feb  5 22:41 1521_20130126030000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       64252 Jan 26 04:01 1521_20130126030000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6205887708 Feb  2 04:01 1521_20130202030000.mpg
-rw-rw-rw- 1 mythtv mythtv        6190 Feb  5 22:40 1521_20130202030000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       51994 Feb  2 04:01 1521_20130202030000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6248558256 Feb  3 19:01 1521_20130203180000.mpg
-rw-rw-rw- 1 mythtv mythtv        9901 Feb  5 22:40 1521_20130203180000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       80215 Feb  3 19:01 1521_20130203180000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6337486956 Feb  9 04:01 1521_20130209030000.mpg
-rw-rw-rw- 1 mythtv mythtv       11206 Jun  7 10:51 1521_20130209030000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       86297 Feb  9 04:01 1521_20130209030000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6262811288 Mar 30 04:01 1521_20130330030000.mpg
-rw-rw-rw- 1 mythtv mythtv       11462 Jun  7 10:51 1521_20130330030000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       94816 Apr  1 00:10 1521_20130330030000.mpg.png
-rw-r--r-- 1 mythtv mythtv  6404848296 May 29 23:01 1521_20130529220000.mpg
-rw-rw-rw- 1 mythtv mythtv        7044 Jun  7 10:51 1521_20130529220000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       54271 Jun  1 20:15 1521_20130529220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1175853056 Apr 22 21:31 2048_20130422210000.mpg
-rw-rw-rw- 1 mythtv mythtv        7886 Jun  7 10:51 2048_20130422210000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       63689 Apr 22 21:31 2048_20130422210000.mpg.png
-rw-r--r-- 1 mythtv mythtv           0 Apr 22 21:29 2048_20130422213000.mpg
-rw-r--r-- 1 mythtv mythtv  2315564992 Apr 25 21:01 2048_20130425200000.mpg
-rw-rw-rw- 1 mythtv mythtv        9287 Jun  7 10:51 2048_20130425200000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       83044 Apr 25 21:01 2048_20130425200000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1194848192 Apr 29 20:31 2048_20130429200000.mpg
-rw-rw-rw- 1 mythtv mythtv        7965 Jun  7 10:51 2048_20130429200000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       74953 Apr 29 20:31 2048_20130429200000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2330687424 May 27 20:01 2048_20130527190000.mpg
-rw-rw-rw- 1 mythtv mythtv       12203 Jun  7 10:51 2048_20130527190000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      102461 May 28 23:51 2048_20130527190000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2317897664 Jun  3 16:01 2048_20130603150000.mpg
-rw-rw-rw- 1 mythtv mythtv        9395 Jun  7 10:51 2048_20130603150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       81235 Jun  3 16:01 2048_20130603150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1178693568 Jun  3 17:31 2048_20130603170000.mpg
-rw-rw-rw- 1 mythtv mythtv       12429 Jun  7 10:51 2048_20130603170000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       98422 Jun  3 17:31 2048_20130603170000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2277144512 Jun  3 21:00 2048_20130603200000.mpg
-rw-rw-rw- 1 mythtv mythtv        8669 Jun  7 10:51 2048_20130603200000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       71241 Jun  3 21:00 2048_20130603200000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1175797760 Jun  3 21:31 2048_20130603210000.mpg
-rw-rw-rw- 1 mythtv mythtv        9921 Jun  7 10:51 2048_20130603210000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       82135 Jun  3 21:31 2048_20130603210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1194088384 Jun 10 21:31 2048_20130610210000.mpg
-rw-rw-rw- 1 mythtv mythtv       85005 Jun 10 21:31 2048_20130610210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2393216960 Aug 19  2012 2054_20120819210000.mpg
-rw-rw-rw- 1 mythtv mythtv       67849 Oct  9  2012 2054_20120819210000.mpg.png
-rw-r--r-- 1 mythtv mythtv   211521694 Jun 16 22:08 2054_20130616220000.mpg
-rw-rw-rw- 1 mythtv mythtv         284 Jun 26 19:59 2054_20130616220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2334427072 Jun 26 22:01 2054_20130626205900.mpg
-rw-rw-rw- 1 mythtv mythtv       76566 Jun 26 22:01 2054_20130626205900.mpg.png
-rw-r--r-- 1 mythtv mythtv  1705633728 Jun 30 23:01 2054_20130630221600.mpg
-rw-rw-rw- 1 mythtv mythtv       97312 Jun 30 23:01 2054_20130630221600.mpg.png
-rw-r--r-- 1 mythtv mythtv  1225500608 Sep 26  2012 2057_20120926220000.mpg
-rw-rw-rw- 1 mythtv mythtv       10580 Feb  5 22:41 2057_20120926220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       94749 Sep 29  2012 2057_20120926220000.mpg.png
-rw-r--r-- 1 mythtv mythtv           0 Oct  3  2012 2057_20121003220000.mpg
-rw-r--r-- 1 mythtv mythtv  1223843776 Oct 10  2012 2057_20121010220000.mpg
-rw-rw-rw- 1 mythtv mythtv         413 Feb  5 22:41 2057_20121010220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv        2407 Oct 10  2012 2057_20121010220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1224998848 Oct 17  2012 2057_20121017220000.mpg
-rw-rw-rw- 1 mythtv mythtv       12233 Feb  5 22:41 2057_20121017220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      105654 Oct 17  2012 2057_20121017220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1224560576 Oct 24  2012 2057_20121024220000.mpg
-rw-rw-rw- 1 mythtv mythtv        9873 Feb  5 22:41 2057_20121024220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       90843 Oct 24  2012 2057_20121024220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1224826816 Oct 31  2012 2057_20121031220000.mpg
-rw-rw-rw- 1 mythtv mythtv        3027 Feb  5 22:41 2057_20121031220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       37284 Nov  1  2012 2057_20121031220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1192572864 Dec 23  2012 2057_20121223023400.mpg
-rw-rw-rw- 1 mythtv mythtv       14469 Feb  5 22:41 2057_20121223023400.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      130545 Dec 23  2012 2057_20121223023400.mpg.png
-rw-r--r-- 1 mythtv mythtv  1186340800 Feb  1 01:01 2057_20130201003000.mpg
-rw-rw-rw- 1 mythtv mythtv       14264 Feb  5 22:41 2057_20130201003000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      132940 May 12 21:58 2057_20130201003000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1194528704 Feb 28 19:01 2057_20130228182900.mpg
-rw-rw-rw- 1 mythtv mythtv       15631 Jun  7 10:51 2057_20130228182900.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      128628 Mar 22 00:59 2057_20130228182900.mpg.png
-rw-r--r-- 1 mythtv mythtv  1192976320 May  1 22:31 2057_20130501220000.mpg
-rw-rw-rw- 1 mythtv mythtv       14911 Jun  7 10:51 2057_20130501220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      121475 May  1 22:31 2057_20130501220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1182050240 May 15 22:31 2057_20130515220000.mpg
-rw-rw-rw- 1 mythtv mythtv       12033 Jun  7 10:51 2057_20130515220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      106077 May 15 22:31 2057_20130515220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1217779648 May 29 18:58 2057_20130529182600.mpg
-rw-rw-rw- 1 mythtv mythtv       12894 Jun  7 10:51 2057_20130529182600.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      107861 May 29 18:58 2057_20130529182600.mpg.png
-rw-r--r-- 1 mythtv mythtv  1194936256 May 29 22:31 2057_20130529215900.mpg
-rw-rw-rw- 1 mythtv mythtv       12778 Jun  7 10:51 2057_20130529215900.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      111155 May 30 21:31 2057_20130529215900.mpg.png
-rw-r--r-- 1 mythtv mythtv  1217918912 May 30 18:53 2057_20130530182100.mpg
-rw-rw-rw- 1 mythtv mythtv       13892 Jun  7 10:51 2057_20130530182100.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      121981 May 30 18:53 2057_20130530182100.mpg.png
-rw-r--r-- 1 mythtv mythtv  1217099776 May 31 18:52 2057_20130531182000.mpg
-rw-rw-rw- 1 mythtv mythtv       13011 Jun  7 10:51 2057_20130531182000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      104094 May 31 18:52 2057_20130531182000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1180026816 Jun  3 18:58 2057_20130603182700.mpg
-rw-rw-rw- 1 mythtv mythtv        9576 Jun  7 10:51 2057_20130603182700.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       86159 Jun  3 18:58 2057_20130603182700.mpg.png
-rw-r--r-- 1 mythtv mythtv  1178863552 Jun  5 00:32 2057_20130605000100.mpg
-rw-rw-rw- 1 mythtv mythtv       13857 Jun  7 10:51 2057_20130605000100.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      115057 Jun  6 22:16 2057_20130605000100.mpg.png
-rw-r--r-- 1 mythtv mythtv  1217855424 Jun  9 20:30 2057_20130609195800.mpg
-rw-rw-rw- 1 mythtv mythtv       90150 Jun  9 20:30 2057_20130609195800.mpg.png
-rw-r--r-- 1 mythtv mythtv  1193963456 Jun 11 13:54 2057_20130611132300.mpg
-rw-rw-rw- 1 mythtv mythtv      124850 Jun 11 13:54 2057_20130611132300.mpg.png
-rw-r--r-- 1 mythtv mythtv  1193365440 Jun 12 00:32 2057_20130612000000.mpg
-rw-rw-rw- 1 mythtv mythtv      121492 Jun 12 00:32 2057_20130612000000.mpg.png
-rw-r--r-- 1 mythtv mythtv   539983912 Jun 14 18:33 2057_20130614182000.mpg
-rw-rw-rw- 1 mythtv mythtv      115592 Jun 14 23:42 2057_20130614182000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1192472512 Jun 27 10:01 2057_20130627093000.mpg
-rw-rw-rw- 1 mythtv mythtv       79746 Jun 27 10:01 2057_20130627093000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1194715072 Jun 27 22:01 2057_20130627213000.mpg
-rw-rw-rw- 1 mythtv mythtv      104197 Jul  2 17:55 2057_20130627213000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1195055040 Jun 28 10:01 2057_20130628092900.mpg
-rw-rw-rw- 1 mythtv mythtv       99922 Jun 28 10:01 2057_20130628092900.mpg.png
-rw-r--r-- 1 mythtv mythtv  1230706624 Jun 28 18:52 2057_20130628182000.mpg
-rw-rw-rw- 1 mythtv mythtv      119833 Jun 28 18:52 2057_20130628182000.mpg.png
-rw-r--r-- 1 mythtv mythtv   706117632 Jun 30 23:22 2057_20130630230400.mpg
-rw-rw-rw- 1 mythtv mythtv      121557 Jul  2 17:53 2057_20130630230400.mpg.png
-rw-r--r-- 1 mythtv mythtv    35557312 Apr  7 16:07 2058_20130407160600.mpg
-rw-rw-rw- 1 mythtv mythtv       98902 Apr  7 16:07 2058_20130407160600.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392672192 Jun  4  2012 2060_20120604000000.mpg
-rw-rw-rw- 1 mythtv mythtv       99847 Jun  4  2012 2060_20120604000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2393372608 Jun  9  2012 2060_20120609150000.mpg
-rw-rw-rw- 1 mythtv mythtv       10281 Feb  5 22:41 2060_20120609150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       88283 Jun 10  2012 2060_20120609150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2393251776 Jun 16  2012 2060_20120616150000.mpg
-rw-rw-rw- 1 mythtv mythtv        9720 Feb  5 22:41 2060_20120616150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       82342 Jun 16  2012 2060_20120616150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392819648 Jun 18  2012 2060_20120618000000.mpg
-rw-rw-rw- 1 mythtv mythtv       12002 Feb  5 22:41 2060_20120618000000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       96252 Jun 18  2012 2060_20120618000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392524736 Jun 23  2012 2060_20120623150000.mpg
-rw-rw-rw- 1 mythtv mythtv        7529 Feb  5 22:41 2060_20120623150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       61323 Jun 24  2012 2060_20120623150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392080320 Jun 25  2012 2060_20120625000000.mpg
-rw-rw-rw- 1 mythtv mythtv        9820 Feb  5 22:41 2060_20120625000000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       86124 Jun 25  2012 2060_20120625000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392496064 Jun 30  2012 2060_20120630150000.mpg
-rw-rw-rw- 1 mythtv mythtv       12073 Feb  5 22:41 2060_20120630150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      100413 Jun 30  2012 2060_20120630150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2391939008 Jul 14  2012 2060_20120714150000.mpg
-rw-rw-rw- 1 mythtv mythtv        9924 Feb  5 22:41 2060_20120714150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       87498 Jul 16  2012 2060_20120714150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2391478208 Jul 28  2012 2060_20120728000000.mpg
-rw-rw-rw- 1 mythtv mythtv       11394 Feb  5 22:41 2060_20120728000000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       94000 Jul 28  2012 2060_20120728000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392659904 Aug  5  2012 2060_20120805010000.mpg
-rw-rw-rw- 1 mythtv mythtv        7677 Feb  5 22:41 2060_20120805010000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       66459 Aug  5  2012 2060_20120805010000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392197056 Aug 19  2012 2060_20120819010000.mpg
-rw-rw-rw- 1 mythtv mythtv       10887 Feb  5 22:41 2060_20120819010000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       84021 Aug 19  2012 2060_20120819010000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392592320 Aug 25  2012 2060_20120825150000.mpg
-rw-rw-rw- 1 mythtv mythtv       10909 Feb  5 22:41 2060_20120825150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       89932 Oct  6  2012 2060_20120825150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392235968 Sep 23  2012 2060_20120923220000.mpg
-rw-rw-rw- 1 mythtv mythtv       10311 Feb  5 22:41 2060_20120923220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       89447 Oct  3  2012 2060_20120923220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392403904 Oct 15  2012 2060_20121015000000.mpg
-rw-rw-rw- 1 mythtv mythtv       10434 Feb  5 22:41 2060_20121015000000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       84732 Oct 15  2012 2060_20121015000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2393208768 Nov 10  2012 2060_20121110215900.mpg
-rw-rw-rw- 1 mythtv mythtv        9946 Feb  5 22:41 2060_20121110215900.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       85260 Nov 11  2012 2060_20121110215900.mpg.png
-rw-r--r-- 1 mythtv mythtv  2393223104 Nov 11  2012 2060_20121111005900.mpg
-rw-rw-rw- 1 mythtv mythtv       10351 Feb  5 22:41 2060_20121111005900.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       86497 Nov 11  2012 2060_20121111005900.mpg.png
-rw-r--r-- 1 mythtv mythtv  2391054272 Nov 11  2012 2060_20121111050000.mpg
-rw-rw-rw- 1 mythtv mythtv       11791 Feb  5 22:41 2060_20121111050000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       91546 Dec  5  2012 2060_20121111050000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392670144 Nov 17  2012 2060_20121117150000.mpg
-rw-rw-rw- 1 mythtv mythtv       11811 Feb  5 22:41 2060_20121117150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       94048 Dec 11  2012 2060_20121117150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2333648832 Dec 22  2012 2060_20121222150000.mpg
-rw-rw-rw- 1 mythtv mythtv        9307 Feb  5 22:41 2060_20121222150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       80519 Jan 25 20:50 2060_20121222150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2332325888 Jan  5 16:01 2060_20130105150000.mpg
-rw-rw-rw- 1 mythtv mythtv       11480 Feb  5 22:41 2060_20130105150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       96921 Jan 25 20:57 2060_20130105150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2332491712 Jan 12 16:01 2060_20130112150000.mpg
-rw-rw-rw- 1 mythtv mythtv       10369 Feb  5 22:41 2060_20130112150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       89124 Jan 13 21:53 2060_20130112150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2333452224 Jan 19 16:01 2060_20130119145900.mpg
-rw-rw-rw- 1 mythtv mythtv       11237 Feb  5 22:41 2060_20130119145900.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       96494 Jan 19 22:11 2060_20130119145900.mpg.png
-rw-r--r-- 1 mythtv mythtv  2320428992 Jan 26 16:01 2060_20130126150000.mpg
-rw-rw-rw- 1 mythtv mythtv        9836 Feb  5 22:41 2060_20130126150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       86738 Jan 30 00:12 2060_20130126150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2324729792 Feb  2 16:01 2060_20130202150000.mpg
-rw-rw-rw- 1 mythtv mythtv        9582 Feb  5 22:40 2060_20130202150000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       82647 Feb  2 16:01 2060_20130202150000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2326360000 Feb 24 23:01 2060_20130224220000.mpg
-rw-rw-rw- 1 mythtv mythtv       12397 Jun  7 10:51 2060_20130224220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       99980 Mar 21 23:21 2060_20130224220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2330052544 Apr 15 01:01 2060_20130415000000.mpg
-rw-rw-rw- 1 mythtv mythtv       10121 Jun  7 10:51 2060_20130415000000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       84303 Apr 15 01:01 2060_20130415000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2332688320 Apr 28 23:01 2060_20130428220000.mpg
-rw-rw-rw- 1 mythtv mythtv       10708 Jun  7 10:51 2060_20130428220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       91357 May 29 19:59 2060_20130428220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2318467008 Jun 10 01:01 2060_20130610000000.mpg
-rw-rw-rw- 1 mythtv mythtv       88263 Jun 10 01:01 2060_20130610000000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2331578304 Jun 26 21:01 2060_20130626200000.mpg
-rw-rw-rw- 1 mythtv mythtv       72541 Jun 26 21:01 2060_20130626200000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2332204992 Jun 27 21:01 2060_20130627200000.mpg
-rw-rw-rw- 1 mythtv mythtv       93079 Jun 27 21:01 2060_20130627200000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2330326976 Jun 28 21:01 2060_20130628200000.mpg
-rw-rw-rw- 1 mythtv mythtv       99625 Jun 28 21:01 2060_20130628200000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1705539520 Jun 30 23:01 2060_20130630221600.mpg
-rw-rw-rw- 1 mythtv mythtv      107939 Jun 30 23:01 2060_20130630221600.mpg.png
-rw-r--r-- 1 mythtv mythtv  2394152896 Oct 20  2012 2061_20121020180000.mpg
-rw-rw-rw- 1 mythtv mythtv       12112 Feb  5 22:41 2061_20121020180000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       87474 Mar 10 14:34 2061_20121020180000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392111040 Oct 21  2012 2061_20121021180000.mpg
-rw-rw-rw- 1 mythtv mythtv        9939 Feb  5 22:41 2061_20121021180000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       77133 Oct 22  2012 2061_20121021180000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392518592 Oct 25  2012 2061_20121025210000.mpg
-rw-rw-rw- 1 mythtv mythtv       11666 Feb  5 22:41 2061_20121025210000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       87824 Mar 18 00:48 2061_20121025210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2392121280 Oct 27  2012 2061_20121027180000.mpg
-rw-rw-rw- 1 mythtv mythtv       13191 Feb  5 22:41 2061_20121027180000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv      101769 Mar 18 00:48 2061_20121027180000.mpg.png
-rw-r--r-- 1 mythtv mythtv  1193625536 Mar  7 22:01 2061_20130307213000.mpg
-rw-rw-rw- 1 mythtv mythtv       12179 Jun  7 10:51 2061_20130307213000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       95515 Mar  7 22:01 2061_20130307213000.mpg.png
-rw-r--r-- 1 mythtv mythtv  3471112128 Mar 15 23:31 2075_20130315220000.mpg
-rw-rw-rw- 1 mythtv mythtv        9586 Jun  7 10:51 2075_20130315220000.mpg.-1.100x75.png
-rw-rw-rw- 1 mythtv mythtv       78120 Mar 15 23:31 2075_20130315220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2409546368 Jun 13  2011 3761_20110613210000.mpg
-rw-rw-rw- 1 mythtv mythtv        1514 Sep 17  2011 3761_20110613210000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv        1514 Jun 20  2011 3761_20110613210000.mpg.94.100x56.png
-rw-rw-rw- 1 mythtv mythtv        9860 Jun 13  2011 3761_20110613210000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2382677596 Jun 13  2011 3761_20110613213000.mpg
-rw-rw-rw- 1 mythtv mythtv        8530 Sep 17  2011 3761_20110613213000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv        8530 Jun 20  2011 3761_20110613213000.mpg.94.100x56.png
-rw-rw-rw- 1 mythtv mythtv       63895 Jun 13  2011 3761_20110613213000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2339614504 Jun 13  2011 3761_20110613220000.mpg
-rw-rw-rw- 1 mythtv mythtv        8713 Sep 17  2011 3761_20110613220000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv        8713 Jun 20  2011 3761_20110613220000.mpg.94.100x56.png
-rw-rw-rw- 1 mythtv mythtv       66382 Jun 13  2011 3761_20110613220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  2318275564 Jun 13  2011 3761_20110613223000.mpg
-rw-rw-rw- 1 mythtv mythtv        9702 Sep 17  2011 3761_20110613223000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv        9702 Jun 20  2011 3761_20110613223000.mpg.94.100x56.png
-rw-rw-rw- 1 mythtv mythtv       80889 Jun 13  2011 3761_20110613223000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5477583416 Sep 22  2012 3761_20120922220000.mpg
-rw-rw-rw- 1 mythtv mythtv       84033 Jan 28 01:28 3761_20120922220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5731532124 Sep 29  2012 3761_20120929220000.mpg
-rw-rw-rw- 1 mythtv mythtv       47503 Jan 28 00:59 3761_20120929220000.mpg.png
-rw-r--r-- 1 mythtv mythtv  3039591144 Oct 22  2012 3761_20121022183000.mpg
-rw-rw-rw- 1 mythtv mythtv       10870 Feb  5 22:41 3761_20121022183000.mpg.-1.100x56.png
-rw-rw-rw- 1 mythtv mythtv       93773 Oct 23  2012 3761_20121022183000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5564188812 Oct 26  2012 3761_20121025230000.mpg
-rw-rw-rw- 1 mythtv mythtv       79331 Dec  8  2012 3761_20121025230000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5904604172 Jun 27 00:01 3762_20130626230000.mpg
-rw-rw-rw- 1 mythtv mythtv       81470 Jun 27 00:01 3762_20130626230000.mpg.png
-rw-r--r-- 1 mythtv mythtv  5867900368 Jun 28 00:01 3762_20130627225900.mpg
-rw-rw-rw- 1 mythtv mythtv       92143 Jun 28 00:01 3762_20130627225900.mpg.png
```

Yes, I can confirm that new recordings do work.


> **tgm4883 said:**
> Ok, can you also give us the following information.

1) The Title & Subtitle of a show that DOES work.

2) The Title & Subtitle of a show that does NOT work.

3) The output of the following 3 commands.

```
ls -l /mythtv
```

```
ls -l /mythtv/livetv/
```

```
ls -l /mythtv/recordings/
```

Also, can you confirm that new RECORDINGS (read, NOT livetv) work?

---

### Post by davidstoll on 2013-07-02
Well, something got reset.  Some of my old shows (inside mythtv) are gone, but many of the older shows are still there and are now playing.  The database sort of relinked to what it could and deleted what it couldn't.

Hard drive crashes are not fun.  :(

I tried to create a scheduled database backup in the myth control panel and got the attached error.  I tried several different setups...daily, weekly, monthly..etc.

```
DBus Exception

org.freedesktop.DBus.Python.IOError

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 280, in scriptedchanges
    plugin_instances[instance].root_scripted_changes(plugin_dictionary[plugin])
  File "/usr/share/mythbuntu/plugins/python/mythbuntu-bare.py", line 500, in root_scripted_changes
    with open(CONFIGFILE, 'wb') as conffile:
IOError: [Errno 2] No such file or directory: '/var/lib/mythtv/bare-client/mythbuntu-bare-client.conf'
```

---

### Post by klc5555 on 2013-07-02
> **davidstoll said:**
> Well, something got reset.  Some of my old shows (inside mythtv) are gone, but many of the older shows are still there and are now playing.  The database sort of relinked to what it could and deleted what it couldn't.

Hard drive crashes are not fun.  :(

I tried to create a scheduled database backup in the myth control panel and got the attached error.  I tried several different setups...daily, weekly, monthly..etc.

```
DBus Exception

org.freedesktop.DBus.Python.IOError

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 280, in scriptedchanges
    plugin_instances[instance].root_scripted_changes(plugin_dictionary[plugin])
  File "/usr/share/mythbuntu/plugins/python/mythbuntu-bare.py", line 500, in root_scripted_changes
    with open(CONFIGFILE, 'wb') as conffile:
IOError: [Errno 2] No such file or directory: '/var/lib/mythtv/bare-client/mythbuntu-bare-client.conf'
```

I'd take the error message at its word and suspect that the mythbuntu-bare-client installed package is now a bit corrupt. More may be missing than just the .conf file. 

For reasonably reliable no-frills daily mythconverg backups, I've always been a bit leery of relying on multi-hundred line python scripts and plugins to accomplish what can be reasonably gotten from a 5-line bash script. One version of a script I still use that has been standard since about Mythtv 0.19 or earlier can be found here: [http://hoast.dk/how-tos/backup-mythtv-database-automatically/](http://hoast.dk/how-tos/backup-mythtv-database-automatically/)

The standard and only recommended way of treating your recordings that no longer have database entries would be to move them to mythvideo. But if you feel exceptionally adventurous, or are disinclined to use mythvideo (and have successfully backed up mythconverg!), the mythtv wiki still provides the old and deprecated myth.rebuilddb.pl script to add orphaned recordings files to the recordings database. [http://www.mythtv.org/wiki/Myth.rebuilddb.pl](http://www.mythtv.org/wiki/Myth.rebuilddb.pl) It still works on mysql 5.5 as I can attest, but can only handle recordings for the local backend it's installed on (not network or storage group aware). Whether it still works with mythtv versions 0.25+ and above is anyone's guess.

---

