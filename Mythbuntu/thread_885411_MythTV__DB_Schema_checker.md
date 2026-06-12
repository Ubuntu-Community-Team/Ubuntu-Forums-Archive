---
title: "MythTV  DB Schema checker"
date: 2008-08-10
forum: Mythbuntu
---

### Post by ian dobson on 2008-08-10
Hi All,

Is there such a thing as a mythtv database checker. I don't mean just checking the database Structure in Mysql. Rather something like:-

1) Check what video inputs are defined against the channels defined.
2) Check the multiplex data against the channels (for DVB)
3) Check the recordings in the DB against what's actually stored on the filesystem.

In my wandering through the Mysql database using phpmyadmin I've found several "errors" (channels in the multiplex database that belong to deleted channels) as well as entries in the recordseek table that belong to deleted recordings.

ps. If one doesn't exist I'll throw on my programmers hat and have a go at writing something, once I've decoded the DB schema MythTV uses.

Regards
Ian Dobson

---

### Post by laga on 2008-08-10
> 
channels in the multiplex database that belong to deleted channels


I'm not sure if that's an "error". AFAIK, dtv_multiplex is used to store the transponders and you don't necessarily want to delete those if you delete all channels on that transponder.

---

### Post by ian dobson on 2008-08-10
Hi laga,

Is there documentation for the DB schema? I've had a look on the MythTV.org site and I've not really found anything.

Regards
Ian Dobson

---

### Post by nickrout on 2008-08-10
[http://www.cuymedia.net/mythtv-trunk/group__db__schema.html](http://www.cuymedia.net/mythtv-trunk/group__db__schema.html)

---

### Post by ian dobson on 2008-08-10
Hi nickrout,

I've see that already, it's a shame that doesn't cover all tables.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-08-11
Hi,

I've started working on the code and already have:-

1) Check how many video inputs are defined.
2) Check that there is atleast one channel defined for each video input.
3) Check that each channel is attached to a video input.
4) Check that each video input has a valid default channel

I still need to work on:-
1) Check each recorded program exists on file system
2) Check each recorded program exists in the recordedseek file
3) Check storage groups/premissions
4) DVD multiplex database
Anything else I can think of :)

Regards
Ian Dobson

---

### Post by nickrout on 2008-08-11
> **ian dobson said:**
> Hi,

I've started working on the code and already have:-


1) Check each recorded program exists on file system
2) Check each recorded program exists in the recordedseek file


Regards
Ian Dobson

Those are already covered by myth.rebuilddatabase as far as I know.

---

### Post by ian dobson on 2008-08-14
Hi,

Done abit more on the code. At the moment the results look like this:-

```

OK...Found 2 video sources
OK...Videosource (1) analog has a EPG source defined (tv_grab_ch_search)
OK...Videosource (2) digital has a EPG source defined (eitonly)
OK...Found 2 card inputs for Videoinput 1
OK...Found 4 card inputs for Videoinput 2
OK...All InputCards are linked to a videosource
OK...Videosource 1 has 10 channels defined
OK...Videosource 2 has 35 channels defined
OK...All channels have a valid videosource
Checking ANIXE HD   has 224 programs in EPG    EPG available for 3.2755 days
Checking SF 1   has 458 programs in EPG    EPG available for 5.0880 days
Checking SF zwei   has 316 programs in EPG    EPG available for 3.9421 days
Checking SF info   has 255 programs in EPG    EPG available for 5.9942 days
Checking HD suisse   has 133 programs in EPG    EPG available for 4.0255 days
Checking BBC HD   has 102 programs in EPG    EPG available for 0.0706 days
Checking BBC 1 London   has 168 programs in EPG    EPG available for 0.0567 days
Checking BBC 2 England   has 297 programs in EPG    EPG available for 0.0567 days
Checking BBC NEWS 24   has 262 programs in EPG    EPG available for 0.0359 days
Checking CBBC Channel / BBC 3   has 131 programs in EPG    EPG available for 0.0359 days
Checking CBeebies / BBC 4   has 92 programs in EPG    EPG available for 0.1192 days
Checking ARTE   has 294 programs in EPG    EPG available for 0.0046 days
Checking ARD   has 429 programs in EPG    EPG available for 6.5567 days
OK...All EPG eintries have a valid channel
OK...Found 269 recordings
Warning...Recording 1001 2008-01-07 05:30:00 does not appear to have a seeklist (has Mythcommflag been run?)
 OK...file exists in file system
Warning...Recording 1001 2007-12-31 05:30:00 does not appear to have a seeklist (has Mythcommflag been run?)
 OK...file exists in file system
Warning...Recording 1001 2008-01-01 05:30:00 does not appear to have a seeklist (has Mythcommflag been run?)
 OK...file exists in file system

```

I need to improve the output abit/add afew more tests.

Regards
Ian Dobson

---

### Post by nickrout on 2008-08-14
If you'd like another tester, let me know where to find your script.

---

### Post by DemonBob on 2008-08-14
> **nickrout said:**
> If you'd like another tester, let me know where to find your script.


I second this. 

Post up a link and i'll give it a test also.

---

### Post by ian dobson on 2008-08-15
Hi,

OK you can grab the code here:- [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)

Just download it to you HD, rename to CheckMythDB.pl and set the execute bit.

I've disabled the file system exists check at the moment as it's hardwired to use the mount point on my server. if I get the chance at the weekend I'll have a go at getting i working with storage groups. To run the script:-

CheckMythDB.pl -u UserName -p Password [optional -h Hostname, localhost is not defined]

It produces alot of output so it might be a good idea to run with "| more".

Regards
Ian Dobson

---

### Post by nickrout on 2008-08-15
Cool, works here fine.

May I suggest getting user and password by sourcing ~/.mythtv/mysql.txt ?

typo on line 136 (misspelled 'entries')

You probably should specify which version of the GPL and include a proper copyright notice.

Thanks for your efforts.

---

### Post by laga on 2008-08-15
Have you looked at the Perl Bindings for MYthTV? They can probably help you with storage groups and the mysql.txt bits.

---

### Post by ian dobson on 2008-08-15
Hi,

I actually don't like the perl bindings much, the reason I'm writing this tool is because another script that I wrote (which uses the perl bindings/mysql.txt) started blowing up in my face for no apparent reason. In the end the reason was that I manually edited the SQL DB and made a small error that MythTV seemed to ignore but the perl routines killed.

I'll fix the spelling of entries (What do you expect from an English programmer living in Switzerland programming at 5am before the coffee machine has warmed up).

GPL/copyright will be fixed up one day, at the moment it's just a hack to see if it'll work.

I'd like to avoid using the mysql.txt config file if I can. If the operator needs to run this script then it could be that something is really badly wrong and I'd rather not trust the info in some file.

Could someone please dump the output from the script for any errors (in the Schema that they find). I'll be playing with my test box at the weekend and hopefully I can create enough schema errors to really test the code that I have at the moment.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-08-15
Hi,

Added the Recorded <-> File check including StorageGroup support.
Also added 2 new command line options:-

-f Check files in FS
-r Check Recorded against FS/Storage Groups

Also added abit of colour for people who like that sort of thing.

I'll work on the code this weekend when I get the chance, I still need to add the GPL comments/disclaimer and tidy up the code abit.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-08-16
Hi all,

updated the code again.
Fixed afew typo's, cleaned up the storage groups code, added a verbose option and added code to read mysql.txt when no commandline options are defined.

All I need to do now is write the dtv_multiplex check. At the momemnt I can't get the SQL query to work correctly.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-08-16
Hi,

Anyone know why this query:-
```

SELECT * 
FROM dtv_multiplex 
WHERE mplexid IN (
SELECT mplexid
FROM channel
)

```

Produces the list of mplexid id's used but:-

```

SELECT * 
FROM dtv_multiplex
WHERE mplexid NOT 
IN (
SELECT mplexid
FROM channel
)

```
Does not produce a list of unused/invalid multiplex id's. I can't see why that shouldn't work.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-08-17
Hi,

Can anyone answer my question? 

The code is now up to scratch apart from the dtv_multiplex problem, but looks as if I'll need to look abit more at it.

The output with all command line options looks like:-

```

[OK].Found 2 video sources
[OK].Videosource (1) analog has a EPG source defined (tv_grab_ch_search)
[OK].Videosource (2) digital has a EPG source defined (eitonly)
[OK].Found 2 card inputs for Videoinput 1
[OK].Found 4 card inputs for Videoinput 2
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 10 channels defined
[OK].Videosource 2 has 35 channels defined
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[OK].All EPG eintries have a valid channel
[OK].Found 2 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system
[OK].Storage group 'DB Backups' exists in file system
[OK].Storage group 'Default' is used in the recorded database
[!!].Storage group 'LiveTV' is used in the recorded database and is not defined
[OK].Channel BBC 2 England has 325 programs in EPG  and data available for 0.0833 days
[OK].Channel BBC NEWS 24 has 297 programs in EPG  and data available for 0.0312 days
[!!].Channel CBBC Channel / BBC 3 has 143 programs in EPG  No EPG data or last program in the past
[--].Checking files in storage group 'Default'
[OK].File 1001_20071231053000.nuv storage group 'Default' exists in database
[--].File 32432_20080817140430.mpg exits in the database but it's in storage group 'LiveTV'
[OK].Checking 279 recordings found in database
[!!].Recording Star Trek - Raumschiff Voyager 2008-01-07 05:30:00 does not appear to have a seeklist
[!!].Recording Doctor Who 2008-06-28 19:55:00 does not appear to have any markup entries (Mythcommflag run?)
[--].Recording Star Trek - Raumschiff Voyager 2008-03-28 05:29:00 Mythcommflag ran but no commercials found
[!!].Recording Alien vs. Predator 2008-03-27 00:29:00 does not appear to have a seeklist
[OK].Recording Alien vs. Predator 2008-03-27 00:29:00 has 7 markup entries
[OK].Recording Earth: Final Conflict 2008-08-04 18:14:00 has 9453 seek entries
[OK].Recording Earth: Final Conflict 2008-08-04 18:14:00 has 11 markup entries

```

Hopefully this might be helpful for someone. I'd love to get some feedback what errors my script finds on other systems and more importantly what errors it doesn't find.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-08-29
Hi,

Had a chance to update the script abit. I've added a multiplex -> channel check and a cardinput -> device check.

Also added the ability to read the MythTV information from the mysql.txt file and display it. The output looks as follows:-

```
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--] Using HostName 'alpha2', DatabaseHost '192.168.0.2', SQLUserName 'mythtv', SQLPassword 'xXxXxXxX'
[OK].Found 2 video sources
[OK].Videosource (1) analog has a EPG source defined (tv_grab_ch_search)
[OK].Videosource (2) digital has a EPG source defined (eitonly)
[OK].Found 2 card inputs for Videoinput 1
[OK].Found 4 card inputs for Videoinput 2
[--].Checking start channel for each cardinput
[OK].Cardinput (1) Start channel (18) valid
[OK].Cardinput (2) Start channel (18) valid
[OK].Cardinput (3) Start channel (33003) valid
[OK].Cardinput (4) Start channel (33003) valid
[OK].Cardinput (5) Start channel (30431) valid
[OK].Cardinput (6) Start channel (30431) valid
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 10 channels defined
[OK].Videosource 2 has 40 channels defined
[OK].cardinput 1 type MPEG exists as device in /dev
[OK].cardinput 2 type MPEG exists as device in /dev
[OK].cardinput 3 type DVB exists as device in /dev
[OK].cardinput 4 type DVB exists as device in /dev
[OK].cardinput 5 type DVB exists as device in /dev
[OK].cardinput 6 type DVB exists as device in /dev
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].8 dtv_multiplex entries do not have a valid channel
[!!].487 EPG entries do not have a valid channel
[OK].Found 2 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system
[OK].Storage group 'DB Backups' exists in file system
[OK].Storage group 'Default' is used in the recorded database and is defined
```

If people could try the script out and provide me with any bugs/problems that they find. At the moment I only know how to check DVB/MPEG cards in the cardinput/devices. If people could provide a dump of the lines :-

sorry I don't know how to check cardinput XxX type XxX device XxX

it would help me alot.
Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-01
Hi,

Spent the last few days wotking with a user on the MythTV dev list and have added afew new checks/fixed afew bugs.

You can download the code from :- [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)

Regards
Ian Dobson

---

### Post by ian dobson on 2008-10-03
Hi All,

I'm now happy with the code. I've finally got the storage groups code working correctly. The script can now handle a storage group that has multiple directories defined.

Regards
Ian Dobson

---

### Post by 4dognight on 2008-10-17
I have a few feature requests for the DB checker.

When it checks the encoders. can it check the remote encoders too. It shows remote encoders as unkown, since they are not in /dev locally.

Same for the recordings checks. Can it also check when the recordings are on remote servers. 

This DB checker is a great idea. Good work. I think it could be expanded to all the other tables too, as there is no Foreign key relationships enforced in the DB. The problem is knowing the relationships. Some are obvious but others not so.

---

### Post by ian dobson on 2008-10-17
Hi,

I though that encoders are specific to one host, based on the hostname in the "capturecard" table. The problem checking remote encoders is that the script doesn't have access to the /dev directory on the remote system.

I'll change the code so that it only looks at the local encoders.

The code checks storage groups but files on a remote system could be hard as the script doesn't necessarly know where to look.

The biggest problem is that there isn't any documentation for the database structure so I can only find the relationships through trial and error.

Another problem I have is that I only have a simple single Backend/single Frontend setup and no posibility to test the code on a complex multi-backend system.

Regards
Ian Dobson

edit: I've just updated the script so that it only looks at local encoders.

---

### Post by Scorpuk on 2008-10-30
Tag - for trialing at the weekend!


I know my database has entries that do not exist in the file storage, so this looks like something I could use to sort that out. :-)


Will backup the database before I use it. :-)

---

### Post by ian dobson on 2008-10-30
Hi,

The script won't actually delete any misstion recordings, it'll just let you know which ones are missing.



Regards
Ian Dobson

---

### Post by nickrout on 2008-10-30
> **Scorpuk said:**
> Tag - for trialing at the weekend!


I know my database has entries that do not exist in the file storage, so this looks like something I could use to sort that out. :-)


Will backup the database before I use it. :-)

what about the tool that mythtv already provides? myth.rebuilddatabase

---

### Post by ian dobson on 2010-04-17
Hi,

I've updated the script, it now understands freebox decoders (channel info fom m3u files/external IP recorders). I've also cleaned up the code abit.

If I get the time I'll add a code to the file/recordings check code to check the size of the thumbnails created, I had a problem on my backend a while back that some png thumbnails where created as 0byte files. This took me sometime to find.

I'll upload a new version in the next few hours. I've not tested the code on MythTV .23 but when I upgrade my backend I'll update the code again. But I don't think anything has changed between .22 and .23 that would affect my script.

```

./CheckMythDB.pl -a
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Found configuration file /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /root/.mythtv/mysql.txt
[--].Found configuration file /root/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'alpha2', DatabaseHost 'localhost', SQLUserName 'mythtv', SQLPassword 'XXXX'
[--].Checking configuration for host 'alpha2'
[OK].Found 2 video sources
[OK].Videosource (2) 'digital' has a EPG source defined (tv_grab_ch_search)
[OK].Videosource (3) 'itgate' has a EPG source defined (/bin/true)
[OK].Found 4 card inputs for Videoinput 2
[OK].Found 2 card inputs for Videoinput 3
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 2 has 60 visible and 73 invisible channels defined
[OK].Videosource 3 has 12 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 4 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 5 type FREEBOX got 985 bytes from web page (M3U) file
[--].cardinput 5 has 11 Channels defined for in m3u file
[OK].cardinput 6 type FREEBOX got 985 bytes from web page (M3U) file
[--].cardinput 6 has 11 Channels defined for in m3u file
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[!!].1 channel entries do not have a valid dtv_multiplex
[!!].Channel 'SHOW TURK' does not have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[OK].All EPG entries have a valid channel
[OK].Found 3 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system at (/data/mythtv/recordings/)
[OK].Storage group 'DB Backups' exists in file system at (/data/mythtv/backup/)
[OK].Storage group 'LiveTV' exists in file system at (/data/mythtv/liveTV/)
[--].Checking files in storage group 'LiveTV'
[--].Checking files in storage group 'Default'
[--].Checking files in storage group 'DB Backups'
[OK].Checking 877 recordings in database (file system)
[OK].Checking 877 recordings found in database (seek,commflag etc)
Took 3211 SQL queries

```

EDIT: Maybe I spoke too soon it looks as if 0.23 is slowly going over to use an xml file (mythtv/config.xml) for the user/password/default server info. The change isn't 100% but mythtv is moving away from using mysql.txt for the default user info (see [https://bugs.launchpad.net/mythbuntu/+bug/484776](https://bugs.launchpad.net/mythbuntu/+bug/484776))

Regards
Ian Dobson

---

### Post by ian dobson on 2010-04-18
Hi All,

OK I've added a thumbnail check to the code. I may have found a bug in the simple storage group code (Storage group with only one directory defined), when I get access to a friends MythTV system I'll have a look at it.

```

[OK].Found 2 video sources
[OK].Videosource (2) 'digital' has a EPG source defined (tv_grab_ch_search)
[OK].Videosource (3) 'itgate' has a EPG source defined (/bin/true)
[OK].Found 4 card inputs for Videoinput 2
[OK].Found 2 card inputs for Videoinput 3
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 2 has 60 visible and 73 invisible channels defined
[OK].Videosource 3 has 12 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 4 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 5 type FREEBOX got 985 bytes from web page (M3U) file
[--].cardinput 5 has 11 Channels defined for in m3u file
[OK].cardinput 6 type FREEBOX got 985 bytes from web page (M3U) file
[--].cardinput 6 has 11 Channels defined for in m3u file
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[!!].1 channel entries do not have a valid dtv_multiplex
[!!].Channel 'SHOW TURK' does not have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[!!].Channel kabel eins has 41 programs in EPG.No EPG data or last program in the past
[!!].Channel DAS VIERTE has 51 programs in EPG.No EPG data or last program in the past
[OK].All EPG entries have a valid channel
[OK].Found 3 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system at (/data/mythtv/recordings/)
[OK].Storage group 'DB Backups' exists in file system at (/data/mythtv/backup/)
[OK].Storage group 'LiveTV' exists in file system at (/data/mythtv/liveTV/)
[--].Checking files in storage group 'LiveTV'
[--].Checking files in storage group 'Default'
[--].Checking files in storage group 'DB Backups'
[OK].Checking 885 recordings in database (file system)
[!!].Recording Judge Dredd, storage group (Default), File (1_20090620224900.mpg) does not have a thumbnail pic
[!!].Recording A.I. Künstliche Intelligenz, storage group (Default), File (1_20090726234900.mpg) does not have a thumbnail pic
[!!].Recording  32438_20090906015400.mpg, thumbnail (32438_20090906015400.mpg.100x56.png) too small (<100bytes)
[!!].Recording  32438_20090906015400.mpg, thumbnail (32438_20090906015400.mpg.64.100x75.png) too small (<100bytes)
[!!].Recording  32438_20090906015400.mpg, thumbnail (32438_20090906015400.mpg.64.png) too small (<100bytes)
[!!].Recording  32438_20090906015400.mpg, thumbnail (32438_20090906015400.mpg.png) too small (<100bytes)
[!!].Recording Arachnid, storage group (Default), File (1_20091108034400.mpg) does not have a thumbnail pic
[OK].Checking 885 recordings found in database (seek,commflag etc)
Took 3235 SQL queries

```

I'll upload a new version in afew hours, I still want to do afew tests.

EDIT: OK storage groupproblem solved, the code always used the complex storage group (/directory1:/directory2) even though I had seperate code for simple storage groups.

EDIT: New version uploaded. Link [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)


Regards
Ian Dobson

---

### Post by ian dobson on 2010-04-18
OK,

Uploaded a new version, the thumbnail check code is abit more inteligent and abit quicker. It also checks the owner of the thumbs.

The code also checks the channels listed for a FREEBOX encoder against the channel table and channel table against m3u file.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-04-21
Hi,

OK, hacked afew more tests for FREEBOX tuners.

```

[OK].Found 2 video sources
[OK].Videosource 2 'digital' has a EPG source defined (tv_grab_ch_search)
[OK].Videosource 3 'itgate' has a EPG source defined (/bin/true)
[OK].Videoinput 2 has 4 card inputs defined
[OK].Videoinput 3 has 2 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[--].Cardinput (5) has a channel change script defined '/data/bin/itgate-changea.sh'
[OK].Channel change script '/data/bin/itgate-changea.sh' the permissions 0777 (rwx rwx rwx) owner (mythtv) group (mythtv)
[--].Cardinput (6) has a channel change script defined '/data/bin/itgate-changeb.sh'
[OK].Channel change script '/data/bin/itgate-changeb.sh' the permissions 0777 (rwx rwx rwx) owner (mythtv) group (mythtv)
[OK].All InputCards are linked to a videosource
[OK].Videosource 2 has 60 visible and 73 invisible channels defined
[OK].Videosource 3 has 12 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 4 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 5 type FREEBOX got 1065 bytes from web page (M3U) file 'http://localhost/itgate1.m3u'
[--].cardinput 5 has 12 Channels defined for in m3u file
[OK].cardinput 6 type FREEBOX got 1065 bytes from web page (M3U) file 'http://localhost/itgate2.m3u'
[--].cardinput 6 has 12 Channels defined for in m3u file
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[!!].1 channel entries do not have a valid dtv_multiplex
[!!].Channel 'SHOW TURK' does not have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[OK].All EPG entries have a valid channel
[OK].Found 3 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system at (/data/mythtv/recordings/)
[OK].Storage group 'DB Backups' exists in file system at (/data/mythtv/backup/)
[OK].Storage group 'LiveTV' exists in file system at (/data/mythtv/liveTV/)
[--].Checking files in storage group 'LiveTV'
[--].Checking files in storage group 'Default'
[--].Checking files in storage group 'DB Backups'
[OK].Checking 878 recordings in database (file system)
[OK].Checking 878 recordings found in database (seek,commflag etc)

```

If anyone has a 0.23 Mythtv system and want's to test the script I'll be more than happy :)

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-04-21
I have a 0.23 machine, what does this script do exactly?

---

### Post by ian dobson on 2010-04-21
Hi,

The script checks the database structure checking that the dependances between Videosource/Card input/Channels/Recordings/Thumbnails are correct.

For example the script displays an error 
1) when you have a channel thats not linked to a video source
2) When you have a external channel change script defined in the DB but the script doesn't exist/isn't executible
3) When you have recordings in the DB but the recording doesn't exist in the file system
4) When there is a DVB Channel that doesn't have a valid DTV_multiplex entry.

plus alot more. The script doesn't change anything it just executes sql queries comparing the results recieved to what is expected/listed in other tables.

I actually started writing this script to try a fix a totally screwed up database, caused by disk corruption from a dieing harddisk.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-04-24
Hi tgm4883,

Have you tried the script?

I've uploaded a new version of the script (I found an error in the option selection code/added a thumbnail check against recodings).

The first time I ran the new "thumbnail check against recordings" it found about 300 png files that mythtv didn't delete when it deleted the recording.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-04-24
I've run the script, here is the output from my machine. Note, I ran this on my frontend. 
```
thomas@poseidon:~/Downloads$ ./CheckMythDB.pl 
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /home/thomas/.mythtv/mysql.txt
[--].Found configuration file /home/thomas/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'poseidon', DatabaseHost '192.168.0.10', SQLUserName 'SCRUBBED', SQLPassword 'SCRUBBED'
(SCRUBBED, SCRUBBED, poseidon,0,0,0,192.168.0.10,0)
[--].Checking configuration for host 'poseidon'
[OK].Found 2 video sources
[OK].Videosource 1 'Portland OTA' has a EPG source defined (schedulesdirect1)
[OK].Videosource 2 'WB Cable' has a EPG source defined (schedulesdirect1)
[OK].Videoinput 1 has 3 card inputs defined
[!!].Videoinput 2 does not have any card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 6 visible and 0 invisible channels defined
[!!].Videosource 2 does not appear to have any channels defined
[--].cardinput 1 type DVB is not local to host 'poseidon'
[--].cardinput 2 type DVB is not local to host 'poseidon'
[--].cardinput 4 type DVB is not local to host 'poseidon'
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].3 dtv_multiplex entries do not have a valid channel
[!!].No storage groups found for host 'poseidon'
Took 20 SQL queries

```


And again from my backend


```
thomas@ares:~$ ./CheckMythDB.pl 
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /home/thomas/.mythtv/mysql.txt
[--].Found configuration file /home/thomas/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'ares', DatabaseHost 'ares', SQLUserName 'SCRUBBED', SQLPassword 'SCRUBBED'
(SCRUBBED, SCRUBBED, ares,0,0,0,ares,0)
[--].Checking configuration for host 'ares'
[OK].Found 2 video sources
[OK].Videosource 1 'Portland OTA' has a EPG source defined (schedulesdirect1)
[OK].Videosource 2 'WB Cable' has a EPG source defined (schedulesdirect1)
[OK].Videoinput 1 has 3 card inputs defined
[!!].Videoinput 2 does not have any card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 6 visible and 0 invisible channels defined
[!!].Videosource 2 does not appear to have any channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 4 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].3 dtv_multiplex entries do not have a valid channel
[OK].Found 8 storage groups for 'ares'
[OK].Storage group 'Default' exists in file system at (/srv/mythtv/ares1500/recordings/)
[OK].Storage group 'Videos' exists in file system at (/var/lib/mythtv/videos/)
[OK].Storage group 'Trailers' exists in file system at (/var/lib/mythtv/trailers/)
[OK].Storage group 'Coverart' exists in file system at (/var/lib/mythtv/coverart/)
[OK].Storage group 'Fanart' exists in file system at (/var/lib/mythtv/fanart/)
[OK].Storage group 'Screenshots' exists in file system at (/var/lib/mythtv/screenshots/)
[OK].Storage group 'Banners' exists in file system at (/var/lib/mythtv/banners/)
[OK].Storage group 'DB Backups' exists in file system at (/var/lib/mythtv/db_backups/)
[!!].Storage group 'LiveTV' is used in the recorded database but it's not defined
Took 24 SQL queries
thomas@ares:~$ 

```

---

### Post by ian dobson on 2010-04-24
Hi,

The script should be run on one backend.

It looks as if you don't have any channels defined for 'WB Cable' is this video source on a slave backend?
It also looks as if you have LiveTV recordings but the LiveTV storage group is not defined.

If you run the script with the -a option it'll check all options.

Any entry marked with [!!] is what I think is an error.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-09-18
Hi,

OK, I've added afew new functions to the code (iptv recorder checking, thumbs checking, fixed afew bugs).

```

[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /root/.mythtv/mysql.txt
[--].Found configuration file /root/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'alpha2', DatabaseHost 'localhost', SQLUserName 'mythtv', SQLPassword 'DELETED'
[--].Checking configuration for host 'alpha2'
[OK].Found 2 video sources
[OK].Videosource 2 'digital' has a EPG source defined (tv_grab_ch_search)
[OK].Videosource 3 'itgate' has a EPG source defined (/bin/true)
[OK].Videoinput 2 has 4 card inputs defined
[OK].Videoinput 3 has 2 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[--].Cardinput (5) has a channel change script defined '/data/bin/itgate-changea.sh'
[OK].Channel change script '/data/bin/itgate-changea.sh' the permissions 0755 (rwx r-x r-x) owner (mythtv) group (video)
[--].Cardinput (6) has a channel change script defined '/data/bin/itgate-changeb.sh'
[OK].Channel change script '/data/bin/itgate-changeb.sh' the permissions 0755 (rwx r-x r-x) owner (mythtv) group (video)
[OK].All InputCards are linked to a videosource
[OK].Videosource 2 has 56 visible and 75 invisible channels defined
[OK].Videosource 3 has 16 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device (/dev/dvb/adapter0/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device (/dev/dvb/adapter0/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device (/dev/dvb/adapter1/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 4 type DVB exists as device (/dev/dvb/adapter1/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 5 type FREEBOX got 1412 bytes from web page (M3U) file 'http://localhost/itgate1.m3u'
[OK].cardinput 5 has 16 Channels defined in m3u file
[OK].cardinput 6 type FREEBOX got 1413 bytes from web page (M3U) file 'http://localhost/itgate2.m3u'
[OK].cardinput 6 has 16 Channels defined in m3u file
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[OK].All EPG entries have a valid channel
[OK].Found 3 storage groups for 'alpha2'
[OK].Storage group 'Default' exists in file system at (/data/mythtv/recordings/)
[OK].Storage group 'DB Backups' exists in file system at (/data/mythtv/backup/)
[OK].Storage group 'LiveTV' exists in file system at (/data/mythtv/liveTV/)
[--].Checking files in storage group 'LiveTV'
[--].Checking thumbnails in storage group 'LiveTV' against recordings
[--].Checking files in storage group 'Default'
[--].Checking thumbnails in storage group 'Default' against recordings
[--].Checking files in storage group 'DB Backups'
[--].Checking thumbnails in storage group 'DB Backups' against recordings
[--].Checking 1349 recordings in database (file system)
[OK].Checking 1349 recordings found in database (seek,commflag etc)
Took 4444 SQL queries
```

Regards
Ian Dobson

---

