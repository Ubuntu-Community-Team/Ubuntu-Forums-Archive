---
title: "Lots and Lots of missing recordings"
date: 2008-09-22
forum: Mythbuntu
---

### Post by budge31 on 2008-09-22
Hi all,

I was wondering whether someone can help me with a problem thats driving me nuts. I have been running the same backend now for about 15 months, and it has been pretty faultless. In the last month or so I have started to have recordings disappear off the backend to the point I am losing about 4 a day. (I have about 220 stored at the moment. Ican see in Mythweb that they recordings existed, it gives me a file size, and if scanned for commercials, how many commercials were found. I can see the image grab for the recording in Mythweb, however when I go to watch the file on a frontend it comes up as a missing recording.

Looking at the Backend log I am seeing a lot of this:

2008-09-22 13:40:17.233 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:17.263 adding: backend as a client (events: 0)
2008-09-22 13:40:19.985 Reschedule requested for id 0.
2008-09-22 13:40:21.520 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:21.526 adding: backend as a client (events: 0)
2008-09-22 13:40:22.056 Scheduled 145 items in 2.1 = 0.01 match + 2.06 place
2008-09-22 13:40:22.078 scheduler: Scheduled items: Scheduled 145 items in 2.1 = 0.01 match + 2.06 place
2008-09-22 13:40:24.487 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:24.490 adding: backend as a client (events: 0)
2008-09-22 13:40:26.265 Reschedule requested for id 0.
2008-09-22 13:40:26.569 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:26.574 adding: backend as a client (events: 0)
2008-09-22 13:40:27.253 MythSocket(7f32881fe480:-1): writeStringList: Error, socket went unconnected.
2008-09-22 13:40:28.496 Scheduled 145 items in 2.2 = 0.16 match + 2.07 place
2008-09-22 13:40:28.503 scheduler: Scheduled items: Scheduled 145 items in 2.2 = 0.16 match + 2.07 place
2008-09-22 13:40:28.791 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:28.793 adding: backend as a client (events: 0)
2008-09-22 13:40:30.806 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:30.807 adding: backend as a client (events: 0)
2008-09-22 13:40:32.519 Reschedule requested for id 0.
2008-09-22 13:40:33.261 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:33.270 adding: backend as a client (events: 0)
2008-09-22 13:40:34.648 Scheduled 145 items in 2.1 = 0.01 match + 2.11 place
2008-09-22 13:40:34.656 scheduler: Scheduled items: Scheduled 145 items in 2.1 = 0.01 match + 2.11 place
2008-09-22 13:40:36.479 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:36.481 adding: backend as a client (events: 0)
2008-09-22 13:40:38.615 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:38.619 adding: backend as a client (events: 0)
2008-09-22 13:40:38.699 Reschedule requested for id 0.
2008-09-22 13:40:39.405 MainServer::HandleAnnounce Monitor
2008-09-22 13:40:39.433 adding: backend as a client (events: 0)
2008-09-22 13:40:40.163 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1012_20080918202400.mpg'
2008-09-22 13:40:40.165 MainServer: Failed to make preview image.
2008-09-22 13:40:40.238 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/2073_20080914212700.mpg'
2008-09-22 13:40:40.239 MainServer: Failed to make preview image.
2008-09-22 13:40:40.267 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1003_20080914202900.mpg'
2008-09-22 13:40:40.269 MainServer: Failed to make preview image.
2008-09-22 13:40:40.279 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/2073_20080913155200.mpg'
2008-09-22 13:40:40.279 MainServer: Failed to make preview image.
2008-09-22 13:40:40.297 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1012_20080911212400.mpg'
2008-09-22 13:40:40.309 MainServer: Failed to make preview image.
2008-09-22 13:40:40.325 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1007_20080911145400.mpg'
2008-09-22 13:40:40.326 MainServer: Failed to make preview image.
2008-09-22 13:40:40.334 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/2073_20080911112700.mpg'
2008-09-22 13:40:40.335 MainServer: Failed to make preview image.
2008-09-22 13:40:40.344 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1007_20080910222400.mpg'
2008-09-22 13:40:40.345 MainServer: Failed to make preview image.
2008-09-22 13:40:40.353 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1002_20080910195400.mpg'
2008-09-22 13:40:40.354 MainServer: Failed to make preview image.
2008-09-22 13:40:40.364 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1007_20080910153700.mpg'
2008-09-22 13:40:40.365 MainServer: Failed to make preview image.
2008-09-22 13:40:40.378 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1070_20080910124400.mpg'
2008-09-22 13:40:40.387 MainServer: Failed to make preview image.
2008-09-22 13:40:40.398 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/2072_20080909225400.mpg'
2008-09-22 13:40:40.400 MainServer: Failed to make preview image.
2008-09-22 13:40:40.430 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1003_20080906192700.mpg'
2008-09-22 13:40:40.446 MainServer: Failed to make preview image.
2008-09-22 13:40:40.494 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1007_20080827212400.mpg'
2008-09-22 13:40:40.495 MainServer: Failed to make preview image.
2008-09-22 13:40:40.547 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1021_20080815205200.mpg'
2008-09-22 13:40:40.548 MainServer: Failed to make preview image.
2008-09-22 13:40:40.600 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1003_20080721215700.mpg'
2008-09-22 13:40:40.602 MainServer: Failed to make preview image.
2008-09-22 13:40:40.631 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1021_20080716202700.mpg'
2008-09-22 13:40:40.632 MainServer: Failed to make preview image.
2008-09-22 13:40:40.643 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1003_20080710203000.mpg'
2008-09-22 13:40:40.644 MainServer: Failed to make preview image.
2008-09-22 13:40:40.651 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/1021_20080709202700.mpg'
2008-09-22 13:40:40.652 MainServer: Failed to make preview image.
2008-09-22 13:40:40.781 Scheduled 145 items in 2.1 = 0.00 match + 2.07 place
2008-09-22 13:40:40.790 scheduler: Scheduled items: Scheduled 145 items in 2.1 = 0.00 match + 2.07 place
2008-09-22 13:40:44.881 Reschedule requested for id 0.
2008-09-22 13:40:46.826 Scheduled 145 items in 1.9 = 0.01 match + 1.93 place
2008-09-22 13:40:46.833 scheduler: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.93 place
2008-09-22 13:40:51.016 Reschedule requested for id 0.
2008-09-22 13:40:52.961 Scheduled 145 items in 1.9 = 0.01 match + 1.93 place
2008-09-22 13:40:57.135 Reschedule requested for id 0.
2008-09-22 13:40:59.048 Scheduled 145 items in 1.9 = 0.01 match + 1.90 place
2008-09-22 13:40:59.055 scheduler: Last message repeated 1 times: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.93 place
2008-09-22 13:40:59.061 scheduler: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.90 place
2008-09-22 13:41:03.255 Reschedule requested for id 0.
2008-09-22 13:41:05.195 Scheduled 145 items in 1.9 = 0.01 match + 1.92 place
2008-09-22 13:41:05.678 MainServer::HandleAnnounce Monitor
2008-09-22 13:41:06.308 scheduler: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.92 place
2008-09-22 13:41:06.717 adding: backend as a client (events: 0)
2008-09-22 13:41:07.290 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/2073_20080911112700.mpg. File doesn't exist.  Database metadata will not be removed.
2008-09-22 13:41:07.297 mythbackend: Delete Recording: File /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend/2073_20080911112700.mpg does not exist for chanid 2073 at Thu Sep 11 11:27:00 2008 when trying to delete recording.
2008-09-22 13:41:09.380 Reschedule requested for id 0.
2008-09-22 13:41:11.330 Scheduled 145 items in 1.9 = 0.01 match + 1.93 place
2008-09-22 13:41:11.337 scheduler: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.93 place
2008-09-22 13:41:15.496 Reschedule requested for id 0.
2008-09-22 13:41:17.433 Scheduled 145 items in 1.9 = 0.01 match + 1.92 place
2008-09-22 13:41:17.441 scheduler: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.92 place
2008-09-22 13:41:21.713 Reschedule requested for id 0.
2008-09-22 13:41:23.638 Scheduled 145 items in 1.9 = 0.01 match + 1.91 place
2008-09-22 13:41:23.647 scheduler: Scheduled items: Scheduled 145 items in 1.9 = 0.01 match + 1.91 place
2008-09-22 13:44:03.597 mythbackend: Running housekeeping thread
2008-09-22 13:44:11.845 MainServer::HandleAnnounce Monitor
2008-09-22 13:44:11.846 adding: mythkids as a client (events: 0)
2008-09-22 13:44:11.848 MainServer::HandleAnnounce Monitor
2008-09-22 13:44:11.849 adding: mythkids as a client (events: 1)
2008-09-22 13:44:17.117 MainServer::HandleAnnounce Playback
2008-09-22 13:44:17.283 adding: mythkids as a client (events: 0)
2008-09-22 13:44:17.285 MainServer::HandleAnnounce FileTransfer
2008-09-22 13:44:17.286 adding: mythkids as a remote file transfer
2008-09-22 13:44:24.053 MainServer::HandleAnnounce Playback
2008-09-22 13:44:24.055 adding: mythkids as a client (events: 0)

I will attempt to attach an entire log for you all to look at.

I am gutted, I went to watch the second episode of the new season of Battlestar Gallactica, and it was gone. I don't mind so much when the wifes Make Me a Supermodel disappears, but I have my limits.

Any help would be greatly appreciated.

---

### Post by stevanbt on 2008-09-22
Hi,
Have you got enough space left on your hard drive?  If not you may find that recordings are being autoexpired.

Thanks, Steve.

---

### Post by budge31 on 2008-09-22
> **stevanbt said:**
> Hi,
Have you got enough space left on your hard drive?  If not you may find that recordings are being autoexpired.

Thanks, Steve.


Hi Steve,

Yea I have actually got 1.7 TB and am currently using 640gb.

---

### Post by ian dobson on 2008-09-22
Hi,

I've written a small perl script that checks the Database configuration against the file system, maybe it might be of use to you.

You can grab the script here :- [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)

Just rename it to CheckMythDB.pl and set it to executable then run it with ./CheckMythDB.pl -a

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-22
> **ian dobson said:**
> Hi,

I've written a small perl script that checks the Database configuration against the file system, maybe it might be of use to you.

You can grab the script here :- [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)

Just rename it to CheckMythDB.pl and set it to executable then run it with ./CheckMythDB.pl -a

Regards
Ian Dobson

Nice One, I will give it a try today.

---

### Post by budge31 on 2008-09-22
Ok I gave your CheckMythDB.pl a run and it provided this output:

 perl CheckMythDB.pl -u mythtv -p lapwryhz -a -v
[OK].Found 1 video sources
[OK].Videosource (1) Shepherd has a EPG source defined (tv_grab_au)
[OK].Found 9 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].Cardinput (11) Start channel (20) valid
[OK].Cardinput (12) Start channel (2) valid
[OK].Cardinput (13) Start channel (20) valid
[OK].Cardinput (14) Start channel (1073) valid
[OK].Cardinput (16) Start channel (1072) valid
[OK].Cardinput (18) Start channel (10) valid
[OK].Cardinput (19) Start channel (21) valid
[OK].Cardinput (20) Start channel (1073) valid
[OK].Cardinput (22) Start channel (20) valid
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 13 channels defined
[OK].cardinput 18 type DVB exists as device in /dev
[OK].cardinput 19 type DVB exists as device in /dev
[OK].cardinput 20 type DVB exists as device in /dev
[OK].cardinput 21 type DVB exists as device in /dev
[OK].cardinput 23 type DVB exists as device in /dev
[OK].cardinput 25 type DVB exists as device in /dev
[OK].cardinput 26 type DVB exists as device in /dev
[OK].cardinput 27 type DVB exists as device in /dev
[OK].cardinput 29 type DVB exists as device in /dev
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].6 dtv_multiplex entries do not have a valid channel
[OK].Channel ABC 1 has 695 programs in EPG and data available for 10.0260 days
[OK].Channel SBS has 482 programs in EPG and data available for 6.6753 days
[OK].Channel 7 Digital has 364 programs in EPG and data available for 6.6580 days
[OK].Channel TEN Digital has 476 programs in EPG and data available for 6.6371 days
[OK].Channel TEN HD has 430 programs in EPG and data available for 6.6371 days
[OK].Channel ABC HDTV has 687 programs in EPG and data available for 6.6510 days
[OK].Channel ABC2 has 555 programs in EPG and data available for 6.8663 days
[!!].Channel ABC3 has 0 programs in EPG.No EPG data
[OK].Channel SBS HD has 482 programs in EPG and data available for 6.6753 days
[OK].Channel SBS NEWS has 517 programs in EPG and data available for 6.7969 days
[OK].Channel 7 HD Digital has 374 programs in EPG and data available for 9.9496 days
[OK].Channel Nine Digital has 418 programs in EPG and data available for 6.6580 days
[OK].Channel Nine Digital HD has 418 programs in EPG and data available for 6.6580 days
[OK].All EPG entries have a valid channel
[!!].No storage groups found for host ''
[OK].Checking 205 recordings found in database
[!!].No storage groups defined, cannot run FS check
Took 49 SQL queries

As you can see it said I have > No storage groups found for host '' and  No storage groups defined, cannot run FS check. 

I obviously have strorage groups as the system is recording, and most of the recordings are available. 
One problem I have always had with storage groups is the inability to remove a storage directory from a storage group. For example, when I  first set up Storage Groups I decided set a Backup Storage Directory for a test to see how it worked. It worked the way I expected but when  I went to remove it I couldn't. I would delete the path, but it would ste the path to "/". Eventually I just had the same path in the main Storage Group and the Backup Storage group. Could this be pointing to a problem in the Database?

---

### Post by budge31 on 2008-09-22
Ok I think its fixed. After running CheckMythDB.pl, I used Webmin to open mythconverge. I found my way to the storagegroup table and deleted the directory names under DB Backups. I went into mythbackend setup to see if they were completely removed, then when I exited the setup it restarted the mythbackend service. 
Unfortunately, the one recording that was running when mythbackend was restarted, happened to be the only one that was set to record to DB Backups. It couldn't find the path so created a zero length file. The recording wouldn't delete from the frontend so I ran: mysqlcheck -r -u mythtv -********* mythconverg. which fixed it.

I have been monitoring the log from the backend, and all of the error have disappeared. I watch it for a couple of days and hopefully call it solved. Cheers Ian.

---

### Post by ian dobson on 2008-09-22
Hi,

For some reason the script didn't find you host name.  Any chance that you can dump your mysql.txt file?

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-23
> **ian dobson said:**
> Hi,

For some reason the script didn't find you host name.  Any chance that you can dump your mysql.txt file?

Regards
Ian Dobson

Sure, here you go.

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=*******

---

### Post by budge31 on 2008-09-23
Ok, I missed the "-h" switch, so I added it with the hostname and got this result.

perl CheckMythDB.pl -u mythtv -p ******* -h backend
[OK].Found 1 video sources
[OK].Videosource (1) Shepherd has a EPG source defined (tv_grab_au)
[OK].Found 9 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 13 channels defined
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].6 dtv_multiplex entries do not have a valid channel
[OK].All EPG entries have a valid channel
[OK].Found 5 storage groups for 'backend'
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings3/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings2/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup2/)
[!!].Storage group 'DB Backups' is used in the recorded database but it's not defined
Took 26 SQL queries

---

### Post by ian dobson on 2008-09-23
Hi,

If you call the script with just the -a option it should read the mysql data from the mysql.txt file and run all checks on the database.

I'll have a look at the script as to why it didn't complain that the hostname was not defined.

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-24
Well, I managed to get your script to work, and found out there are more recordings going missing. Here is the full output:

> 
budge@backend:~$ perl CheckMythDB.pl -a
[--].No command line options defined trying mysql.txt
[--].Try CheckMythDB.pl -H for help
[--] Using HostName 'backend', DatabaseHost '192.168.0.7', SQLUserName 'mythtv', SQLPassword 'lapwryhz'
[OK].Found 1 video sources
[OK].Videosource (1) Shepherd has a EPG source defined (tv_grab_au)
[OK].Found 9 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 25 channels defined
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].6 dtv_multiplex entries do not have a valid channel
[!!].Channel ABC3 has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 5 storage groups for 'backend'
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings2/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings3/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup2/)
[!!].Storage group 'DB Backups' is used in the recorded database but it's not defined
[!!].Storage group 'LiveTV' is used in the recorded database but it's not defined
[--].Checking files in storage group 'Default'
[--].File '1012_20080924123000.mpg' exits in the database but it's in storage group 'LiveTV' rather than 'Default'
[!!].File '1020_20080702220000.mpg' storage group 'Default' does not appear to exist in database
[!!].Recording Judge Judy 2008-09-04 14:54:00 (1010_20080904145400.mpg) does not appear in the file system (Default)
[!!].Recording Sir Alan Sugar: The Apprentice 2008-09-03 22:24:00 (1007_20080903222400.mpg) does not appear in the file system (Default)
[!!].Recording Seinfeld 2008-09-07 23:22:00 (2072_20080907232200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Seinfeld 2008-08-31 23:22:00 (2072_20080831232200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Secret Diary of a Call Girl 2008-09-23 22:24:00 (2072_20080923222400.mpg) does not appear in the file system (Default)
[!!].Recording Skins 2008-08-04 22:02:00 (1003_20080804220200.mpg) does not appear in the file system (Default)
[!!].Recording Monster Garage 2008-09-24 14:54:00 (1012_20080924145400.mpg) does not appear in the file system (Default)
[!!].Recording Hi-5 2008-09-05 15:27:00 (2072_20080905152700.mpg) does not appear in the file system (Default)
[!!].Recording Hi-5 2008-09-04 15:27:00 (2072_20080904152700.mpg) does not appear in the file system (Default)
[!!].Recording The Gil Mayo Mysteries 2008-07-10 20:38:00 (1020_20080710203800.mpg) does not appear in the file system (Default)
[!!].Recording Dora the Explorer 2008-09-21 06:54:00 (2072_20080921065400.mpg) does not appear in the file system (Default)
[!!].Recording Masterchef Goes Large 2008-09-16 14:54:00 (1007_20080916145400.mpg) does not appear in the file system (Default)
[!!].Recording Judge Judy 2008-09-02 14:54:00 (1010_20080902145400.mpg) does not appear in the file system (Default)
[!!].Recording Kokoda 2008-08-23 21:22:00 (2073_20080823212200.mpg) does not appear in the file system (Default)
[!!].Recording Shaun the Sheep 2008-09-13 11:32:00 (1021_20080913113200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Seinfeld 2008-09-05 23:17:00 (2073_20080905231700.mpg) does not appear in the file system (DB Backups)
[!!].Recording Mythbusters 2008-08-07 22:54:00 (1070_20080807225400.mpg) does not appear in the file system (Default)
[!!].Recording Motorway Patrol 2008-08-22 19:27:00 (2072_20080822192700.mpg) does not appear in the file system (Default)
[!!].Recording Speed 2008-07-19 21:44:00 (1070_20080719214400.mpg) does not appear in the file system (Default)
[!!].Recording Big Love 2008-07-19 20:30:00 (1003_20080719203000.mpg) does not appear in the file system (Default)
[!!].Recording Fast Ed's Fast Food 2008-09-05 12:44:00 (1070_20080905124400.mpg) does not appear in the file system (Default)
[!!].Recording Spiral 2008-07-31 20:30:00 (1003_20080731203000.mpg) does not appear in the file system (Default)
[!!].Recording New Police Story 2008-08-02 21:54:00 (1003_20080802215400.mpg) does not appear in the file system (Default)
[!!].Recording Very Small Business 2008-09-03 21:24:00 (1020_20080903212400.mpg) does not appear in the file system (Default)
[!!].Recording Torchwood 2008-09-08 22:22:00 (1012_20080908222200.mpg) does not appear in the file system (Default)
[!!].Recording James May's 20th Century 2008-09-21 20:29:00 (1003_20080921202900.mpg) does not appear in the file system (Default)
[!!].Recording Spiral 2008-08-07 20:30:00 (1003_20080807203000.mpg) does not appear in the file system (Default)
[!!].Recording Kitchen Nightmares 2008-09-08 20:22:00 (2073_20080908202200.mpg) does not appear in the file system (Default)
[!!].Recording Seinfeld 2008-09-12 23:37:00 (2073_20080912233700.mpg) does not appear in the file system (DB Backups)
[!!].Recording Judge Judy 2008-09-05 14:55:00 (1010_20080905145500.mpg) does not appear in the file system (Default)
[!!].Recording Shipwrecked 2008-09-01 23:54:00 (2072_20080901235400.mpg) does not appear in the file system (Default)
[!!].Recording Torchwood 2008-09-15 22:22:00 (1012_20080915222200.mpg) does not appear in the file system (Default)
[!!].Recording In The Night Garden 2008-09-23 09:00:00 (1020_20080923090000.mpg) does not appear in the file system (Default)
[!!].Recording At the Movies 2008-08-27 21:57:00 (1020_20080827215700.mpg) does not appear in the file system (Default)
[!!].Recording Big Love 2008-07-26 20:30:00 (1003_20080726203000.mpg) does not appear in the file system (Default)
[!!].Recording The Gil Mayo Mysteries 2008-07-24 20:35:00 (1020_20080724203500.mpg) does not appear in the file system (Default)
[!!].Recording Seinfeld 2008-08-24 23:22:00 (2073_20080824232200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Motorway Patrol 2008-07-25 19:27:00 (2072_20080725192700.mpg) does not appear in the file system (Default)
[!!].Recording The Mighty Boosh 2008-09-15 20:49:00 (1003_20080915204900.mpg) does not appear in the file system (Default)
[!!].Recording Brat Camp: Mums And Daughters 2008-07-30 21:14:00 (1021_20080730211400.mpg) does not appear in the file system (Default)
[!!].Recording Masterchef Goes Large 2008-09-12 14:54:00 (1007_20080912145400.mpg) does not appear in the file system (Default)
[!!].Recording Crash Investigation Unit 2008-09-03 19:24:00 (1070_20080903192400.mpg) does not appear in the file system (Default)
[!!].Recording Underbelly 2008-09-16 20:27:00 (2073_20080916202700.mpg) does not appear in the file system (Default)
[!!].Recording Shaun the Sheep 2008-09-20 11:32:00 (1021_20080920113200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Jakers!: The Adventures of Piggley Winks 2008-09-20 12:12:00 (1021_20080920121200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Masterchef Goes Large 2008-09-15 14:54:00 (1007_20080915145400.mpg) does not appear in the file system (Default)
[!!].Recording Crash Investigation Unit 2008-09-17 19:24:00 (1070_20080917192400.mpg) does not appear in the file system (Default)
[!!].Recording Underbelly 2008-09-14 20:27:00 (2073_20080914202700.mpg) does not appear in the file system (Default)
[!!].Recording The Mighty Boosh 2008-09-22 20:49:00 (1003_20080922204900.mpg) does not appear in the file system (Default)
[!!].Recording ABC Kids 2008-09-23 06:57:00 (1002_20080923065700.mpg) does not appear in the file system (DB Backups)
[!!].Recording Shipwrecked 2008-09-16 00:04:00 (2072_20080916000400.mpg) does not appear in the file system (Default)
[!!].Recording Masterchef Goes Large 2008-09-17 14:54:00 (1007_20080917145400.mpg) does not appear in the file system (Default)
[!!].Recording Very Small Business 2008-09-17 21:27:00 (1020_20080917212700.mpg) does not appear in the file system (Default)
[!!].Recording Kitchen Nightmares 2008-09-17 21:55:00 (2073_20080917215500.mpg) does not appear in the file system (Default)
[!!].Recording Sir Alan Sugar: The Apprentice 2008-09-17 22:24:00 (1007_20080917222400.mpg) does not appear in the file system (Default)
[!!].Recording Masterchef Goes Large 2008-09-18 14:54:00 (1007_20080918145400.mpg) does not appear in the file system (Default)
[!!].Recording Friends 2008-09-19 18:54:00 (1012_20080919185400.mpg) does not appear in the file system (Default)
[!!].Recording Father Ted 2008-09-19 19:56:00 (1021_20080919195600.mpg) does not appear in the file system (Default)
[!!].Recording The Girl Next Door 2008-09-19 21:34:00 (2073_20080919213400.mpg) does not appear in the file system (Default)
[!!].Recording Make Me a Supermodel 2008-09-23 22:24:00 (1007_20080923222400.mpg) does not appear in the file system (Default)
[!!].Recording Seinfeld 2008-09-19 23:37:00 (2072_20080919233700.mpg) does not appear in the file system (DB Backups)
[!!].Recording Good Game 2008-09-20 00:02:00 (1020_20080920000200.mpg) does not appear in the file system (Default)
[!!].Recording My Friends Tigger and Pooh 2008-09-20 06:24:00 (1070_20080920062400.mpg) does not appear in the file system (Default)
[!!].Recording Secret Diary of a Call Girl 2008-09-23 22:54:00 (2072_20080923225400.mpg) does not appear in the file system (Default)
[!!].Recording Fresh Cooking with the Australian Women's Weekly 2008-09-23 11:30:00 (2073_20080923113000.mpg) does not appear in the file system (Default)
[!!].Recording Kenneth Copeland 2008-09-24 12:30:00 (1012_20080924123000.mpg) does not appear in the file system (LiveTV)
[!!].Recording Fringe 2008-09-24 20:25:00 (2073_20080924202500.mpg) does not appear in the file system (Default)
[!!].Recording Pocoyo 2008-09-25 10:47:00 (1021_20080925104700.mpg) does not appear in the file system (Default)
[OK].Checking 195 recordings found in database
[--].Recording 'Anthony Zimmer' 2008-06-01 21:32:00 Mythcommflag not run
[--].Recording 'The Human Stain' 2008-07-13 00:27:00 Mythcommflag not run
[--].Recording 'Hi-5' 2008-09-05 15:27:00 Mythcommflag not run
[--].Recording 'Underbelly' 2008-09-14 20:27:00 Mythcommflag not run
[--].Recording 'The Girl Next Door' 2008-09-19 21:34:00 Mythcommflag not run
[--].Recording 'Kenneth Copeland' 2008-09-24 12:30:00 appears to be a 'LiveTV' recording (no commflag)
Took 680 SQL queries


This is getting frustrating.

Edit: I just noticed that "[!!].Recording Pocoyo 2008-09-25 10:47:00 (1021_20080925104700.mpg) does not appear in the file system (Default)" is actually there and watchable.

---

### Post by budge31 on 2008-09-24
Well, in what has to be one of the dumbest things I have done in a while, I went through in the frontend and deleted all the missing recordings, only to notice when I was finished that on the last reboot all of my HDDs had rearranged themselves and been mounted in different directories. My DVDs storage had become storage directories, and vice-versa. So when the Database went looking for recordings, they were-not there. So now I have cleared the Database of the metadata, the recordings are probably there. Or not. Who knows.:(:(:(

So now I still have the original issue, or I never had one, or not](*,)](*,)](*,)

---

### Post by ian dobson on 2008-09-26
Hi,

I see you have multiple recording directories in the storage group default. I think I need to have a look at this bit of code, as I'm not sure if it works 100%.

Maybe I can get my test box up and running over the weekend and start debugging this code.

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-26
Hi Ian, 
It seems to be having problems with the multiple storage directories, epecially since my HDDs reshuffled themselves. Is seems to be reporting all new recordings as being missing:


> perl CheckMythDB.pl -a
[--].No command line options defined trying mysql.txt
[--].Try CheckMythDB.pl -H for help
[--] Using HostName 'backend', DatabaseHost '192.168.0.7', SQLUserName 'mythtv',                                                                                                  SQLPassword 'lapwryhz'
[OK].Found 1 video sources
[OK].Videosource (1) Shepherd has a EPG source defined (tv_grab_au)
[OK].Found 9 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 25 channels defined
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].6 dtv_multiplex entries do not have a valid channel
[!!].Channel ABC3 has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 5 storage groups for 'backend'
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordin                                                                                                 gs2/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordin                                                                                                 gs/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordin                                                                                                 gs3/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordin                                                                                                 gsbackup/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordin                                                                                                 gsbackup2/)
[!!].Storage group 'DB Backups' is used in the recorded database but it's not de                                                                                                 fined
[--].Checking files in storage group 'Default'
[!!].File '1020_20080702220000.mpg' storage group 'Default' does not appear to e                                                                                                 xist in database
[!!].Recording Judge Judy 2008-09-04 14:54:00 (1010_20080904145400.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording Make Me a Supermodel 2008-09-25 19:24:00 (1070_20080925192400.mpg                                                                                                 ) does not appear in the file system (Default)
[!!].Recording Secret Diary of a Call Girl 2008-09-23 22:24:00 (2072_20080923222                                                                                                 400.mpg) does not appear in the file system (Default)
[!!].Recording Skins 2008-08-04 22:02:00 (1003_20080804220200.mpg) does not appe                                                                                                 ar in the file system (Default)
[!!].Recording Monster Garage 2008-09-24 14:54:00 (1012_20080924145400.mpg) does                                                                                                  not appear in the file system (Default)
[!!].Recording Hi-5 2008-09-05 15:27:00 (2072_20080905152700.mpg) does not appea                                                                                                 r in the file system (Default)
[!!].Recording Hi-5 2008-09-04 15:27:00 (2072_20080904152700.mpg) does not appea                                                                                                 r in the file system (Default)
[!!].Recording The Gil Mayo Mysteries 2008-07-10 20:38:00 (1020_20080710203800.m                                                                                                 pg) does not appear in the file system (Default)
[!!].Recording Dora the Explorer 2008-09-21 06:54:00 (2072_20080921065400.mpg) d                                                                                                 oes not appear in the file system (Default)
[!!].Recording Masterchef Goes Large 2008-09-16 14:54:00 (1007_20080916145400.mp                                                                                                 g) does not appear in the file system (Default)
[!!].Recording Judge Judy 2008-09-02 14:54:00 (1010_20080902145400.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording Kokoda 2008-08-23 21:22:00 (2073_20080823212200.mpg) does not app                                                                                                 ear in the file system (Default)
[!!].Recording Play School 2008-09-26 15:02:00 (1020_20080926150200.mpg) does no                                                                                                 t appear in the file system (Default)
[!!].Recording Monster Garage 2008-09-26 14:56:00 (1012_20080926145600.mpg) does                                                                                                  not appear in the file system (Default)
[!!].Recording Motorway Patrol 2008-08-22 19:27:00 (2072_20080822192700.mpg) doe                                                                                                 s not appear in the file system (Default)
[!!].Recording Speed 2008-07-19 21:44:00 (1070_20080719214400.mpg) does not appe                                                                                                 ar in the file system (Default)
[!!].Recording Just Married 2008-09-25 11:54:00 (1007_20080925115400.mpg) does n                                                                                                 ot appear in the file system (Default)
[!!].Recording Spiral 2008-07-31 20:30:00 (1003_20080731203000.mpg) does not app                                                                                                 ear in the file system (Default)
[!!].Recording New Police Story 2008-08-02 21:54:00 (1003_20080802215400.mpg) do                                                                                                 es not appear in the file system (Default)
[!!].Recording Torchwood 2008-09-08 22:22:00 (1012_20080908222200.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording James May's 20th Century 2008-09-21 20:29:00 (1003_20080921202900                                                                                                 .mpg) does not appear in the file system (Default)
[!!].Recording Spiral 2008-08-07 20:30:00 (1003_20080807203000.mpg) does not app                                                                                                 ear in the file system (Default)
[!!].Recording Kitchen Nightmares 2008-09-08 20:22:00 (2073_20080908202200.mpg)                                                                                                  does not appear in the file system (Default)
[!!].Recording Judge Judy 2008-09-05 14:55:00 (1010_20080905145500.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording Shipwrecked 2008-09-01 23:54:00 (2072_20080901235400.mpg) does no                                                                                                 t appear in the file system (Default)
[!!].Recording In The Night Garden 2008-09-23 09:00:00 (1020_20080923090000.mpg)                                                                                                  does not appear in the file system (Default)
[!!].Recording At the Movies 2008-08-27 21:57:00 (1020_20080827215700.mpg) does                                                                                                  not appear in the file system (Default)
[!!].Recording Big Love 2008-07-26 20:30:00 (1003_20080726203000.mpg) does not a                                                                                                 ppear in the file system (Default)
[!!].Recording The Gil Mayo Mysteries 2008-07-24 20:35:00 (1020_20080724203500.m                                                                                                 pg) does not appear in the file system (Default)
[!!].Recording Seinfeld 2008-08-24 23:22:00 (2073_20080824232200.mpg) does not a                                                                                                 ppear in the file system (DB Backups)
[!!].Recording Motorway Patrol 2008-07-25 19:27:00 (2072_20080725192700.mpg) doe                                                                                                 s not appear in the file system (Default)
[!!].Recording The Mighty Boosh 2008-09-15 20:49:00 (1003_20080915204900.mpg) do                                                                                                 es not appear in the file system (Default)
[!!].Recording Underbelly 2008-09-16 20:27:00 (2073_20080916202700.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording Shaun the Sheep 2008-09-20 11:32:00 (1021_20080920113200.mpg) doe                                                                                                 s not appear in the file system (DB Backups)
[!!].Recording Jakers!: The Adventures of Piggley Winks 2008-09-20 12:12:00 (102                                                                                                 1_20080920121200.mpg) does not appear in the file system (DB Backups)
[!!].Recording Masterchef Goes Large 2008-09-15 14:54:00 (1007_20080915145400.mp                                                                                                 g) does not appear in the file system (Default)
[!!].Recording Crash Investigation Unit 2008-09-17 19:24:00 (1070_20080917192400                                                                                                 .mpg) does not appear in the file system (Default)
[!!].Recording Underbelly 2008-09-14 20:27:00 (2073_20080914202700.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording The Mighty Boosh 2008-09-22 20:49:00 (1003_20080922204900.mpg) do                                                                                                 es not appear in the file system (Default)
[!!].Recording Shipwrecked 2008-09-16 00:04:00 (2072_20080916000400.mpg) does no                                                                                                 t appear in the file system (Default)
[!!].Recording Masterchef Goes Large 2008-09-17 14:54:00 (1007_20080917145400.mp                                                                                                 g) does not appear in the file system (Default)
[!!].Recording Very Small Business 2008-09-17 21:27:00 (1020_20080917212700.mpg)                                                                                                  does not appear in the file system (Default)
[!!].Recording Kitchen Nightmares 2008-09-17 21:55:00 (2073_20080917215500.mpg)                                                                                                  does not appear in the file system (Default)
[!!].Recording Sir Alan Sugar: The Apprentice 2008-09-17 22:24:00 (1007_20080917                                                                                                 222400.mpg) does not appear in the file system (Default)
[!!].Recording Make Me a Supermodel 2008-09-25 23:24:00 (1070_20080925232400.mpg                                                                                                 ) does not appear in the file system (Default)
[!!].Recording Growing Up Creepie 2008-09-26 06:31:00 (1020_20080926063100.mpg)                                                                                                  does not appear in the file system (Default)
[!!].Recording Friends 2008-09-19 18:54:00 (1012_20080919185400.mpg) does not ap                                                                                                 pear in the file system (Default)
[!!].Recording Father Ted 2008-09-19 19:56:00 (1021_20080919195600.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording The Girl Next Door 2008-09-19 21:34:00 (2073_20080919213400.mpg)                                                                                                  does not appear in the file system (Default)
[!!].Recording Make Me a Supermodel 2008-09-23 22:24:00 (1007_20080923222400.mpg                                                                                                 ) does not appear in the file system (Default)
[!!].Recording Seinfeld 2008-09-19 23:37:00 (2072_20080919233700.mpg) does not a                                                                                                 ppear in the file system (DB Backups)
[!!].Recording Good Game 2008-09-20 00:02:00 (1020_20080920000200.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording My Friends Tigger and Pooh 2008-09-20 06:24:00 (1070_200809200624                                                                                                 00.mpg) does not appear in the file system (Default)
[!!].Recording Secret Diary of a Call Girl 2008-09-23 22:54:00 (2072_20080923225                                                                                                 400.mpg) does not appear in the file system (Default)
[!!].Recording Fringe 2008-09-24 20:25:00 (2073_20080924202500.mpg) does not app                                                                                                 ear in the file system (Default)
[!!].Recording Pocoyo 2008-09-25 10:47:00 (1021_20080925104700.mpg) does not app                                                                                                 ear in the file system (Default)
[!!].Recording Play School 2008-09-25 15:02:00 (1020_20080925150200.mpg) does no                                                                                                 t appear in the file system (Default)
[!!].Recording Lazy Lucy 2008-09-26 11:53:00 (1021_20080926115300.mpg) does not                                                                                                  appear in the file system (Default)
[!!].Recording Postman Pat 2008-09-26 11:35:00 (1021_20080926113500.mpg) does no                                                                                                 t appear in the file system (Default)
[!!].Recording The X-Files 2008-09-25 21:26:00 (1012_20080925212600.mpg) does no                                                                                                 t appear in the file system (Default)
[!!].Recording The Large Family 2008-09-26 07:57:00 (1020_20080926075700.mpg) do                                                                                                 es not appear in the file system (Default)
[!!].Recording Fifi and the Flowertots 2008-09-26 08:08:00 (1020_20080926080800.                                                                                                 mpg) does not appear in the file system (Default)
[!!].Recording Dorothy the Dinosaur 2008-09-26 08:21:00 (1020_20080926082100.mpg                                                                                                 ) does not appear in the file system (Default)
[!!].Recording Sesame Street 2008-09-26 08:25:00 (1020_20080926082500.mpg) does                                                                                                  not appear in the file system (Default)
[!!].Recording Louie 2008-09-26 08:51:00 (1020_20080926085100.mpg) does not appe                                                                                                 ar in the file system (Default)
[OK].Checking 202 recordings found in database
[--].Recording 'Anthony Zimmer' 2008-06-01 21:32:00 Mythcommflag not run
[--].Recording 'The Human Stain' 2008-07-13 00:27:00 Mythcommflag not run
[--].Recording 'Hi-5' 2008-09-05 15:27:00 Mythcommflag not run
[--].Recording 'The Girl Next Door' 2008-09-19 21:34:00 Mythcommflag not run
Took 726 SQL queries


Cheers

Rob

---

### Post by ian dobson on 2008-09-26
Hi,

I don't actually use multiple storage directories. How do you set that up? In the storage group settings dir_one:dir_two:dir_three?

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-26
> **ian dobson said:**
> Hi,

I don't actually use multiple storage directories. How do you set that up? In the storage group settings dir_one:dir_two:dir_three?

Regards
Ian Dobson

Thats pretty much it. You can also have the same path in multiple Storage Groups.

---

### Post by ian dobson on 2008-09-26
Hi,

How have you setup the storage groups on your system exactly. It looks as if you have 5 groups each called "Default".

I've got a feeling that that's not quite right/what mythtv expects. Reading the documentation/code it looks as if myth expects:-
Default=>Directory1
Default1=>Directory2
Default2=>Directory3

or 
Default=>Directory1:directory2:directory3

My script understands the first version but not the second at the moment. I'll see what I can do about it this weekend.

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-26
I have the second :
Default=>Directory1:directory2:directory3

So that would be the issue.

---

### Post by ian dobson on 2008-09-27
Hi budge31,

My script doesn't understand the dir:dir:dir syntax at the moment. Give me afew hours to work on it.

Most of the examples for multiple directories in a storage group seem to use multiple seperate groups with the same name so I'll implement that as well.

Note I just tried the :dir:dir syntax and got this error

2008-09-27 06:57:22.464 TFW, Error: Opening file '/data/mythtv/recordings:/data/mythtv/recordings1/2009_20080927065700.mpg'.
                        eno: No such file or directory (2)

Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-27
Hi budge31,

I've just uploaded a new version of the script that should handle storage groups alot better. It now suports multiple groups with the same names and the dir:dir:dir syntax.

_**Can someone please confirm that the dir:dir:dir syntax is correct/valid for storage groups as per my last post my backend produces errors/doesn't record any programs if I use the ":" syntax.**_

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-27
Sorry, I think I mislead you. It sounds like you are adding the directories in the same way you would in the Videos section ie. /dir1:/dir2:/dir3.

The way I believe it is supposed to be done is you add /dir1,save out, then it gives you the option to add /dir2 and so on.

I just ran the script and got

> perl CheckMythDB.pl -a
[--].No command line options defined trying mysql.txt
[--].Try CheckMythDB.pl -H for help
[--] Using HostName 'backend', DatabaseHost '192.168.0.7', SQLUserName 'mythtv', SQLPassword 'lapwryhz'
[--].Checking configuration for host 'backend'
[OK].Found 1 video sources
[OK].Videosource (1) Shepherd has a EPG source defined (tv_grab_au)
[OK].Found 9 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 25 channels defined
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].6 dtv_multiplex entries do not have a valid channel
[!!].Channel ABC3 has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 5 storage groups for 'backend'
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings2/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings3/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup2/)
[!!].Storage group 'DB Backups' is used in the recorded database but it's not defined
[--].Checking files in storage group 'Default'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordings2/'
[!!].File '1021_20080920113200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1021_20080920121200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1021_20080927113200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '2072_20080919233700.mpg' storage group 'Default' does not appear to exist in database
[!!].File '2073_20080824232200.mpg' storage group 'Default' does not appear to exist in database
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordings/'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordings3/'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordingsbackup/'
[!!].File '1003_20080719203000.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1007_20080903222400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1007_20080912145400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1007_20080918145400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1012_20080915222200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1020_20080903212400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1021_20080730211400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1021_20080913113200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1070_20080807225400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '1070_20080903192400.mpg' storage group 'Default' does not appear to exist in database
[!!].File '2072_20080831232200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '2072_20080907232200.mpg' storage group 'Default' does not appear to exist in database
[!!].File '2073_20080905231700.mpg' storage group 'Default' does not appear to exist in database
[!!].File '2073_20080912233700.mpg' storage group 'Default' does not appear to exist in database
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordingsbackup2/'
[!!].File '1020_20080702220000.mpg' storage group 'Default' does not appear to exist in database
[!!].Recording Seinfeld, 2008-08-24 23:22:00 , storage group (DB Backups) does not appear in the fs
[!!].Recording Shaun the Sheep, 2008-09-20 11:32:00 , storage group (DB Backups) does not appear in the fs
[!!].Recording Jakers!: The Adventures of Piggley Winks, 2008-09-20 12:12:00 , storage group (DB Backups) does not appear in the fs
[!!].Recording Seinfeld, 2008-09-19 23:37:00 , storage group (DB Backups) does not appear in the fs
[!!].Recording Shaun the Sheep, 2008-09-27 11:32:00 , storage group (DB Backups) does not appear in the fs
[OK].Checking 205 recordings found in database
[--].Recording 'Anthony Zimmer' 2008-06-01 21:32:00 Mythcommflag not run
[--].Recording 'The Human Stain' 2008-07-13 00:27:00 Mythcommflag not run
[--].Recording 'Hi-5' 2008-09-05 15:27:00 Mythcommflag not run
[--].Recording 'The X-Files' 2008-09-18 21:24:00 Mythcommflag not run
[--].Recording 'The Girl Next Door' 2008-09-19 21:34:00 Mythcommflag not run
[--].Recording '3-Iron' 2008-09-25 21:59:00 Mythcommflag not run
Took 833 SQL queries


It looks like all the recordings that went missing when my directorys got reshuffled are still on the HDDs. I am just going to work through the list and see what I can recover.

---

### Post by ian dobson on 2008-09-27
Hi,

OK, I understand that now.

The output looks alot better now. I'll have another look at the storage code again but it's almost there.

Thanks again for helping me debug the storage groups code.

Regards
Ian Dobson

---

### Post by budge31 on 2008-09-27
Absolutely my pleasure, I think you have helped fix my issues, so I can't thank you enough. I just went through and cleaned up my HDDs of the screwed up recordings. Now I am getting:

>  perl CheckMythDB.pl -a
[--].No command line options defined trying mysql.txt
[--].Try CheckMythDB.pl -H for help
[--] Using HostName 'backend', DatabaseHost '192.168.0.7', SQLUserName 'mythtv', SQLPassword 'lapwryhz'
[--].Checking configuration for host 'backend'
[OK].Found 1 video sources
[OK].Videosource (1) Shepherd has a EPG source defined (tv_grab_au)
[OK].Found 9 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 25 channels defined
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].6 dtv_multiplex entries do not have a valid channel
[!!].Channel ABC3 has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 5 storage groups for 'backend'
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings2/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordings3/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup/)
[OK].Storage group 'Default' exists in file system at (/home/budge/myth/recordingsbackup2/)
[--].Checking files in storage group 'Default'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordings2/'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordings/'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordings3/'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordingsbackup/'
[--].Checking files in storage group 'Default' directory '/home/budge/myth/recordingsbackup2/'
[OK].Checking 202 recordings found in database
[--].Recording 'Anthony Zimmer' 2008-06-01 21:32:00 Mythcommflag not run
[--].Recording 'The Human Stain' 2008-07-13 00:27:00 Mythcommflag not run
[--].Recording 'Hi-5' 2008-09-05 15:27:00 Mythcommflag not run
[--].Recording 'The X-Files' 2008-09-18 21:24:00 Mythcommflag not run
[--].Recording 'The Girl Next Door' 2008-09-19 21:34:00 Mythcommflag not run
[--].Recording '3-Iron' 2008-09-25 21:59:00 Mythcommflag not run
Took 802 SQL queries

The "Mythcommflag not run" are transcoded files, so I am not worried about them.
All I need to do is keep an eye an the recorded files using your script and I should be able to work out if I am still losing recordings. Personally, I think my Storage Paths and Storage Groups got screwy but we will see,

Thanks Ian

Cheers 

Rob

---

### Post by ian dobson on 2008-09-27
Hi,

I've now finished the storage groups<->FS/Seeklists code. It should now abit easier for you to find which files/recordings are missing by including the file name in the error message.

Regards
Ian Dobson

---

### Post by DemonBob on 2008-09-27
In your fstab make sure your HDD are being mounted by thier UUID and not just /dev/sdx. I've had HDD move around on me before and it was because i was placing them in fstab the old traditional way of /dev/sda1 /media/disk and so on. I switched it to UUID and never had any confusion again.

---

### Post by budge31 on 2008-09-27
Thanks DemonBob, I will give it a go.

---

### Post by budge31 on 2008-09-27
> **ian dobson said:**
> Hi,

I've now finished the storage groups<->FS/Seeklists code. It should now abit easier for you to find which files/recordings are missing by including the file name in the error message.

Regards
Ian Dobson

Thanks, that works perfectly.

---

