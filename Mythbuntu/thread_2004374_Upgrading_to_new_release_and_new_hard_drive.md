---
title: "Upgrading to new release and new hard drive"
date: 2012-06-15
forum: Mythbuntu
---

### Post by crbnrod on 2012-06-15
This seems pretty straightforward, which means there's probably something I'm overlooking. 

Currently running two backends (master/slave) and a frontend with .23 on 10.04, will be upgrading to .25 and 12.04. Both backends currently have old-fashioned spinny hard drives with recordings on them, and I'd like to put the OS and everything on shiny new SSD's. 

So the plan, then, would be to run a database backup on both backends, put the SSD's in the machines, install the new version on the SSDs, point the respective backends to the appropriate place on the old spinny hard drives, and then restore the database. This of course seems like a flawless plan to me - is there anything I'm overlooking (or a simpler way of accomplishing what I wish to accomplish)?

Question #2 - I assume once I have everything up and working, I can just manually delete everything on the old hard drives that isn't recordings, correct?

---

### Post by crbnrod on 2012-06-19
So the answer to the above scenario is basically "yes, but there's only one database," but I've encountered a strange situation I can't seem to resolve.

Primary backend is 192.168.0.2 and was upgraded first. After upgrading, I restored database, which gave me all the recordings in a frontend but none would play. So then I used storage groups to point the directories in question at the actual files (/media/data/var/lib/mythtv/recordings) that already existed on the old hard drive for that particular backend. this worked fine.

Secondary backend is 192.168.0.3 and also has recordings on the hard drive. Since the database was already restored, the recordings on the secondary backend show up in frontends but won't play because it can't find the file. Makes sense, so I went to the primary backend and added the directory in question, in this case /media/datalr/var/lib/mythtv/recordings, to the default storage group. This is as near as I can understand, what [http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups) wants me to do. Permissions are all set so myth has read/write access to this directory, etc.
I can successfully record a new program on the secondary backend, and I can also successfully watch that program from any other frontend.

What's odd is the old recordings won't play. They exist in the same directory as the new recordings, but they show grayed out in all frontends and give a popup indicating the file can't be found. The frontend log also indicates it can't find the file (this is when I try to access the file from the 192.168.0.3 machine):
```
E  PlaybackBoxHelper: CHECK_AVAILABILITY 'myth://192.168.0.2:6543/4363_2012206130500000.mpg' file not found
```
(If I try to access the same file from 192.168.0.2, it checks the other backend like so:
```
E  PlaybackBoxHelper: CHECK_AVAILABILITY 'myth://192.168.0.3:6543/4363_2012206130500000.mpg' file not found
```
However I can manually navigate to the directory and play the file myself, and the file, or at least the metadata and the filename exist in the database.

If I use mythweb on the secondary backend, I can stream/download the old recordings without a problem. If I use mythweb for the primary backend, any recording on the secondary backend shows up with correct data, but when I attempt to download/stream, I get: 
```
4101_20120619142648.mpg does not exist in any recognized storage group directories for this host.
```

Here's the default storage group, livetv is set up similarly:
Default:
/media/data/var/lib/mythtv/recordings/ (primary be)
/media/datalr/var/lib/mythtv/recordings/ (secondary be)

Any ideas?

---

### Post by MrMic on 2012-06-19
Have you checked the permissions on the directories and the files?It maybe that it is still set to allow only your old myth setup to access

---

### Post by crbnrod on 2012-06-19
Thanks for the response - permissions seem to be ok for both the folder and for individual files. It's able to write to the directory, and the permissions of the files match the permissions of the directory.

---

### Post by MrMic on 2012-06-20
Do the server hostnames match to the previous installs from which you made the backups? 
One thing I notice is the path to your recordings storage directory.I assume you have the old drives mounted on media,but originally they were may have been /var/lib/mythtv/recordings as per a standard mythbuntu install.  If you check in your database there are two places that define where your recording are.
 
The storagegroup table , groupname  > [default] , dirname > [*currentpath*] 
and also 
 the settings table > RecordFilePrefix >[*currentpath*] .

 Both of these are worth checking they are pointing to your current recordings directory [*currentpath*] = the path of your recordings

---

### Post by crbnrod on 2012-06-20
> **MrMic said:**
> Do the server hostnames match to the previous installs from which you made the backups? 
One thing I notice is the path to your recordings storage directory.I assume you have the old drives mounted on media,but originally they were may have been /var/lib/mythtv/recordings as per a standard mythbuntu install.  If you check in your database there are two places that define where your recording are.
 
The storagegroup table , groupname  > [default] , dirname > [*currentpath*] 
and also 
 the settings table > RecordFilePrefix >[*currentpath*] .

 Both of these are worth checking they are pointing to your current recordings directory [*currentpath*] = the path of your recordings

I may be revealing my lack of expertise here, but I opened /usr/share/mythtv/sql/mythtv_0.25.0.sql (not sure if this is where to look?) in a text editor and looked for the information in quetion:

```
('RecordFilePrefix','/var/lib/mythtv/recordings','OLDHOSTNAME')
```

```
(1,'Default','OLDHOSTNAME','/var/lib/mythtv/recordings')
```

I have a feeling I"m looking in the wrong place, because none of the directories on the storage group table match what's in the backend setup, and I defined the storage groups after I did the DB restore.

---

### Post by nickrout on 2012-06-20
> **crbnrod said:**
> I may be revealing my lack of expertise here, but I opened /usr/share/mythtv/sql/mythtv_0.25.0.sql (not sure if this is where to look?) in a text editor and looked for the information in quetion:

```
('RecordFilePrefix','/var/lib/mythtv/recordings','OLDHOSTNAME')
```

```
(1,'Default','OLDHOSTNAME','/var/lib/mythtv/recordings')
```

I have a feeling I"m looking in the wrong place, because none of the directories on the storage group table match what's in the backend setup, and I defined the storage groups after I did the DB restore.

What is the hostname of your current backend?

What was the hostname of the previous backend?

---

### Post by crbnrod on 2012-06-20
I definitely changed the hostname - the new one is myth-master, my best guess is the old one was myth2, which I'm guessing is causing the problem...

I also got the actual database fields from the current DB, below:
```
('RecordFilePrefix','/var/lib/mythtv/recordings','myth2')
```

storage groups:
```
(1,'Default','myth2','/var/lib/mythtv/recordings'),
(2,'Videos','myth2','/var/lib/mythtv/videos/'),
(3,'Fanart','myth2','/var/lib/mythtv/fanart/'),
(4,'Trailers','myth2','/var/lib/mythtv/trailers/'),
(5,'Coverart','myth2','/var/lib/mythtv/coverart/'),
(7,'Screenshots','myth2','/var/lib/mythtv/screenshots/'),
(8,'Banners','myth2','/var/lib/mythtv/banners/'),
(9,'DB Backups','myth2','/var/lib/mythtv/db_backups/'),
(10,'LiveTV','myth2','/var/lib/mythtv/livetv/'),
(11,'Default','myth-master','/media/data/var/lib/mythtv/recordings/'),
(12,'Default','myth-master','/media/datalr/var/lib/mythtv/recordings/'),
(13,'LiveTV','myth-master','/media/data/var/lib/mythtv/livetv/'),
(14,'LiveTV','myth-master','/media/datalr/var/lib/mythtv/livetv/'),
(15,'DB Backups','myth-master','/media/data/var/lib/mythtv/db_backups/'),
(16,'Videos','myth-master','/media/data/var/lib/mythtv/videos/'),
(17,'Trailers','myth-master','/media/data/var/lib/mythtv/trailers/'),
(18,'Coverart','myth-master','/media/data/var/lib/mythtv/coverart/'),
(19,'Fanart','myth-master','/media/data/var/lib/mythtv/fanart/'),
(20,'Screenshots','myth-master','/media/data/var/lib/mythtv/screenshots/'),
(21,'Screenshots','myth-master','/media/datalr/var/lib/mythtv/screenshots/'),
(22,'Banners','myth-master','/media/data/var/lib/mythtv/banners/'),
(23,'Default','myth-lr','/media/datalr/var/lib/mythtv/recordings/'),
(24,'LiveTV','myth-lr','/media/datalr/var/lib/mythtv/livetv/');
```

I realize the wiki says not to define groups on a secondary backend (lines 23 & 24 above), but if I didn't it kept trying to use the /var/lib/mythtv directory on the main partition...which may be because of old storage groups pertaining to the 'myth2' hostname.

---

### Post by MrMic on 2012-06-20
From your last post it shows  your recordings are being stored on 3  different servers.Assuming you only want to use one server to store,  then I can guess what went wrong.
The easiest way to correct this would be to restore your database again  from your backups before you connected the new servers.This time make  sure all myth programs are shut down before you do the restore, including any slaves and all frontends.
```
sudo stop mythtv-backend
```and after you do the database restore but before you start any myth  program run this.
In /usr/share/mythtv/ you should have mythconverg_restore.pl
```
mythconverg_restore.pl --change_hostname --old_hostname="XXXX" --new_hostname="YYYY"
```Make sure you run this before you allow any mythprogram to connect, or you may end up with double lot of settings which may cause unpredictable behaviour 
Here is a link to the wiki about this [http://www.mythtv.org/wiki/Database_Backup_and_Restore#Replacing_an_existing_database](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Replacing_an_existing_database)

---

### Post by crbnrod on 2012-06-20
> **MrMic said:**
> From your last post it shows  your recordings are being stored on 3  different servers.Assuming you only want to use one server to store,  then I can guess what went wrong.

I am looking to use two machines for storage (directional antenna-related reasons). they are currently named 'myth-master' and 'myth-lr'. Not sure if that changes what to do anyo since I assume I will just redefine the storage groups after I change the. 

Also when you're saying to do this before letting anything connect, do you mean I should reinstall, or just make sure all BE/FE are not running?

Thanks for the assistance!

---

### Post by MrMic on 2012-06-20
You don't need to reinstall.You can drop the database you have with the out of date data and restore your backup again.Then run that code I linked to update the server names from the old server to the new servername
in your case it would be
```
mythconverg_restore.pl --change_hostname --old_hostname="myth2" --new_hostname="myth-master"
```this will update all occurrences of "myth2" to "myth-master" .Just make sure no FE or BE are running after you restore(which means its fine to be at the desktop in Ubuntu, just the mythbackend and mythfrontend programs should not be running).If you allowed  myth-master BE to run after the db restore and before running that code it would create two copies of  settings for that server in the database, which could cause problems.Once you have updated the server name,then its fine to run the FE/BE program and correct the storage paths and any other settings via the gui

---

### Post by crbnrod on 2012-06-21
We are solved, thanks a bunch for your help. Turns out I had also changed the hostname of the slave backend, so I ended up using the restore script three times: once to drop the current & add the old database, once the change the hostname of the master BE, and once to change the hostname of the slave BE. 
After that, pretty smooth sailing. 
Thanks again.

---

