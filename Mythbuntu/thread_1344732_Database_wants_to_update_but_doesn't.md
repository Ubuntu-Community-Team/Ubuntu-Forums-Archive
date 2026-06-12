---
title: "Database wants to update but doesn't"
date: 2009-12-03
forum: Mythbuntu
---

### Post by williammanda on 2009-12-03
I started viewing a recording and within a few minutes it freezes. I'm forced to reboot the computer. When I start mythtv, I get a screen that tells me that I need to update the database and to run mythtv-setup or mythbackend. I run backend setup and this is the message:

Warning: MythTV wants to upgrade your database, for the TV schema, from to 1244.
MythTV was unable to backup your database.

Then I select update and it finishes. I try to start mythtv and I get the same error again. Which means I'm going in circles, being forced to update the database, which it doesn't. I running the latest ver .22 repo.

---

### Post by kja999 on 2009-12-03
It might be worth doing your own database backup and running a repair as prep for anything else ..

backup:
mysqldump -u<yourdatabase user> -p<userpassword> --all-databases > /home/<you>/mybackup.sql

repair:
mysqlcheck -ao --auto-repair -u<yourdatabase user> -p<userpassword> mythconverg

This might fix it or not, but worth doing anyway as myth is struggling with something in your databaseto aply the update

---

### Post by williammanda on 2009-12-03
> **kja999 said:**
> 
repair:
mysqlcheck -ao --auto-repair -u<yourdatabase user> -p<userpassword> mythconverg


I get this error when running this command:

william@C2Q:~$ mysqlcheck -ao --auto-repair -u mythtv -p mythtv mythconvergEnter password: 
mysqlcheck: Got error: 1045: Access denied for user 'mythtv'@'localhost' (using password: YES) when trying to connect

I tried mythtv as the password as well as mine.

---

### Post by OffAxis on 2009-12-03
you can find your name and password in 
**/home/<your user name>/.mythtv/mysql.txt**

anyone with enough privileges can run that command (so you could run it as user 'root' if you know that password).

And do one of two things:

1. Eliminate the space between the -p and your password (so it'd be -pmythtv in your example)
2. Eliminate the password on that line completely (so the tail end would be ... -p mythconverg). It'll prompt for a password after.

---

### Post by williammanda on 2009-12-03
I used the mythtv information but it still asks for a password after. I have tried the mythtv password and my own but I still get an error.


william@C2Q:~$ mysqlcheck -ao --auto-repair -u mythtv -p b5HP7El9 mythconverg
Enter password: 
mysqlcheck: Got error: 1045: Access denied for user 'mythtv'@'localhost' (using password: YES) when trying to connect

---

### Post by williammanda on 2009-12-03
> **OffAxis said:**
> you can find your name and password in 
**/home/<your user name>/.mythtv/mysql.txt**

anyone with enough privileges can run that command (so you could run it as user 'root' if you know that password).

And do one of two things:

1. Eliminate the space between the -p and your password (so it'd be -pmythtv in your example)
2. Eliminate the password on that line completely (so the tail end would be ... -p mythconverg). It'll prompt for a password after.

Sorry I missed you update. I removed the space between -p and password and it did this:

```
william@C2Q:~$ mysqlcheck -ao --auto-repair -u mythtv -pb5HP7El9 mythconverg
mythconverg.archiveitems
Error    : Incorrect file format 'archiveitems'
error    : Corrupt
mythconverg.callsignnetworkmap
Error    : Incorrect file format 'callsignnetworkmap'
error    : Corrupt
mythconverg.capturecard
Error    : Incorrect file format 'capturecard'
error    : Corrupt
mythconverg.cardinput
Error    : Incorrect file format 'cardinput'
error    : Corrupt
mythconverg.channel
Error    : Incorrect file format 'channel'
error    : Corrupt
mythconverg.channelgroup
Error    : Incorrect file format 'channelgroup'
error    : Corrupt
mythconverg.channelgroupnames
Error    : Incorrect file format 'channelgroupnames'
error    : Corrupt
mythconverg.channelscan
Error    : Incorrect file format 'channelscan'
error    : Corrupt
mythconverg.channelscan_channel
Error    : Incorrect file format 'channelscan_channel'
error    : Corrupt
mythconverg.channelscan_dtv_multiplex
Error    : Incorrect file format 'channelscan_dtv_multiplex'
error    : Corrupt
mythconverg.codecparams
Error    : Incorrect file format 'codecparams'
error    : Corrupt
mythconverg.credits
Error    : Incorrect file format 'credits'
error    : Corrupt
mythconverg.customexample
Error    : Incorrect file format 'customexample'
error    : Corrupt
mythconverg.diseqc_config
Error    : Incorrect file format 'diseqc_config'
error    : Corrupt
mythconverg.diseqc_tree
Error    : Incorrect file format 'diseqc_tree'
error    : Corrupt
mythconverg.displayprofilegroups
Error    : Incorrect file format 'displayprofilegroups'
error    : Corrupt
mythconverg.displayprofiles
Error    : Incorrect file format 'displayprofiles'
error    : Corrupt
mythconverg.dtv_multiplex
Error    : Incorrect file format 'dtv_multiplex'
error    : Corrupt
mythconverg.dtv_privatetypes
Error    : Incorrect file format 'dtv_privatetypes'
error    : Corrupt
mythconverg.dvdbookmark
Error    : Incorrect file format 'dvdbookmark'
error    : Corrupt
mythconverg.dvdinput
Error    : Incorrect file format 'dvdinput'
error    : Corrupt
mythconverg.dvdtranscode
Error    : Incorrect file format 'dvdtranscode'
error    : Corrupt
mythconverg.eit_cache
Error    : Incorrect file format 'eit_cache'
error    : Corrupt
mythconverg.filemarkup
Error    : Incorrect file format 'filemarkup'
error    : Corrupt
mythconverg.gallerymetadata
Error    : Incorrect file format 'gallerymetadata'
error    : Corrupt
mythconverg.gamemetadata
Error    : Incorrect file format 'gamemetadata'
error    : Corrupt
mythconverg.gameplayers
Error    : Incorrect file format 'gameplayers'
error    : Corrupt
mythconverg.housekeeping
Error    : Incorrect file format 'housekeeping'
error    : Corrupt
mythconverg.inputgroup
Error    : Incorrect file format 'inputgroup'
error    : Corrupt
mythconverg.inuseprograms
Error    : Incorrect file format 'inuseprograms'
error    : Corrupt
mythconverg.jobqueue
Error    : Incorrect file format 'jobqueue'
error    : Corrupt
mythconverg.jumppoints
Error    : Incorrect file format 'jumppoints'
error    : Corrupt
mythconverg.keybindings
Error    : Incorrect file format 'keybindings'
error    : Corrupt
mythconverg.keyword
Error    : Incorrect file format 'keyword'
error    : Corrupt
mythconverg.movies_movies
Error    : Incorrect file format 'movies_movies'
error    : Corrupt
mythconverg.movies_showtimes
Error    : Incorrect file format 'movies_showtimes'
error    : Corrupt
mythconverg.movies_theaters
Error    : Incorrect file format 'movies_theaters'
error    : Corrupt
mythconverg.music_albumart
Error    : Incorrect file format 'music_albumart'
error    : Corrupt
mythconverg.music_albums
Error    : Incorrect file format 'music_albums'
error    : Corrupt
mythconverg.music_artists
Error    : Incorrect file format 'music_artists'
error    : Corrupt
mythconverg.music_directories
Error    : Incorrect file format 'music_directories'
error    : Corrupt
mythconverg.music_genres
Error    : Incorrect file format 'music_genres'
error    : Corrupt
mythconverg.music_playlists
Error    : Incorrect file format 'music_playlists'
error    : Corrupt
mythconverg.music_smartplaylist_categories
Error    : Incorrect file format 'music_smartplaylist_categories'
error    : Corrupt
mythconverg.music_smartplaylist_items
Error    : Incorrect file format 'music_smartplaylist_items'
error    : Corrupt
mythconverg.music_smartplaylists
Error    : Incorrect file format 'music_smartplaylists'
error    : Corrupt
mythconverg.music_songs
Error    : Incorrect file format 'music_songs'
error    : Corrupt
mythconverg.music_stats
Error    : Incorrect file format 'music_stats'
error    : Corrupt
mythconverg.mythlog
Error    : Incorrect file format 'mythlog'
error    : Corrupt
mythconverg.mythweb_sessions
Error    : Incorrect file format 'mythweb_sessions'
error    : Corrupt
mythconverg.networkiconmap
Error    : Incorrect file format 'networkiconmap'
error    : Corrupt
mythconverg.newssites
Error    : Incorrect file format 'newssites'
error    : Corrupt
mythconverg.oldfind
Error    : Incorrect file format 'oldfind'
error    : Corrupt
mythconverg.oldprogram
Error    : Incorrect file format 'oldprogram'
error    : Corrupt
mythconverg.oldrecorded
Error    : Incorrect file format 'oldrecorded'
error    : Corrupt
mythconverg.people
Error    : Incorrect file format 'people'
error    : Corrupt
mythconverg.phonecallhistory
Error    : Incorrect file format 'phonecallhistory'
error    : Corrupt
mythconverg.phonedirectory
Error    : Incorrect file format 'phonedirectory'
error    : Corrupt
mythconverg.pidcache
Error    : Incorrect file format 'pidcache'
error    : Corrupt
mythconverg.playgroup
Error    : Incorrect file format 'playgroup'
error    : Corrupt
mythconverg.powerpriority
Error    : Incorrect file format 'powerpriority'
error    : Corrupt
mythconverg.profilegroups
Error    : Incorrect file format 'profilegroups'
error    : Corrupt
mythconverg.program
Error    : Incorrect file format 'program'
error    : Corrupt
mythconverg.programgenres
Error    : Incorrect file format 'programgenres'
error    : Corrupt
mythconverg.programrating
Error    : Incorrect file format 'programrating'
error    : Corrupt
mythconverg.recgrouppassword
Error    : Incorrect file format 'recgrouppassword'
error    : Corrupt
mythconverg.record
Error    : Incorrect file format 'record'
error    : Corrupt
mythconverg.record_tmp
Error    : Incorrect file format 'record_tmp'
error    : Corrupt
mythconverg.recorded
Error    : Incorrect file format 'recorded'
error    : Corrupt
mythconverg.recordedcredits
Error    : Incorrect file format 'recordedcredits'
error    : Corrupt
mythconverg.recordedfile
Error    : Incorrect file format 'recordedfile'
error    : Corrupt
mythconverg.recordedmarkup
Error    : Incorrect file format 'recordedmarkup'
error    : Corrupt
mythconverg.recordedprogram
Error    : Incorrect file format 'recordedprogram'
error    : Corrupt
mythconverg.recordedrating
Error    : Incorrect file format 'recordedrating'
error    : Corrupt
mythconverg.recordedseek
Error    : Incorrect file format 'recordedseek'
error    : Corrupt
mythconverg.recordingprofiles
Error    : Incorrect file format 'recordingprofiles'
error    : Corrupt
mythconverg.recordmatch
Error    : Incorrect file format 'recordmatch'
error    : Corrupt
mythconverg.romdb
Error    : Incorrect file format 'romdb'
error    : Corrupt
mythconverg.schemalock
Error    : Incorrect file format 'schemalock'
error    : Corrupt
mythconverg.settings
Error    : Incorrect file format 'settings'
error    : Corrupt
mythconverg.storagegroup
Error    : Incorrect file format 'storagegroup'
error    : Corrupt
mythconverg.tvchain
Error    : Incorrect file format 'tvchain'
error    : Corrupt
mythconverg.tvosdmenu
Error    : Incorrect file format 'tvosdmenu'
error    : Corrupt
mythconverg.upnpmedia
Error    : Incorrect file format 'upnpmedia'
error    : Corrupt
mythconverg.videocast
Error    : Incorrect file format 'videocast'
error    : Corrupt
mythconverg.videocategory
Error    : Incorrect file format 'videocategory'
error    : Corrupt
mythconverg.videocountry
Error    : Incorrect file format 'videocountry'
error    : Corrupt
mythconverg.videogenre
Error    : Incorrect file format 'videogenre'
error    : Corrupt
mythconverg.videometadata
Error    : Incorrect file format 'videometadata'
error    : Corrupt
mythconverg.videometadatacast
Error    : Incorrect file format 'videometadatacast'
error    : Corrupt
mythconverg.videometadatacountry
Error    : Incorrect file format 'videometadatacountry'
error    : Corrupt
mythconverg.videometadatagenre
Error    : Incorrect file format 'videometadatagenre'
error    : Corrupt
mythconverg.videosource
Error    : Incorrect file format 'videosource'
error    : Corrupt
mythconverg.videotypes
Error    : Incorrect file format 'videotypes'
error    : Corrupt
mythconverg.weatherdatalayout
note     : Table does not support optimize, doing recreate + analyze instead
status   : OK
mythconverg.weatherscreens
note     : Table does not support optimize, doing recreate + analyze instead
status   : OK
mythconverg.weathersourcesettings
note     : Table does not support optimize, doing recreate + analyze instead
status   : OK

Repairing tables
mythconverg.archiveitems
Error    : Incorrect file format 'archiveitems'
error    : Corrupt
mythconverg.callsignnetworkmap
Error    : Incorrect file format 'callsignnetworkmap'
error    : Corrupt
mythconverg.capturecard
Error    : Incorrect file format 'capturecard'
error    : Corrupt
mythconverg.cardinput
Error    : Incorrect file format 'cardinput'
error    : Corrupt
mythconverg.channel
Error    : Incorrect file format 'channel'
error    : Corrupt
mythconverg.channelgroup
Error    : Incorrect file format 'channelgroup'
error    : Corrupt
mythconverg.channelgroupnames
Error    : Incorrect file format 'channelgroupnames'
error    : Corrupt
mythconverg.channelscan
Error    : Incorrect file format 'channelscan'
error    : Corrupt
mythconverg.channelscan_channel
Error    : Incorrect file format 'channelscan_channel'
error    : Corrupt
mythconverg.channelscan_dtv_multiplex
Error    : Incorrect file format 'channelscan_dtv_multiplex'
error    : Corrupt
mythconverg.codecparams
Error    : Incorrect file format 'codecparams'
error    : Corrupt
mythconverg.credits
Error    : Incorrect file format 'credits'
error    : Corrupt
mythconverg.customexample
Error    : Incorrect file format 'customexample'
error    : Corrupt
mythconverg.diseqc_config
Error    : Incorrect file format 'diseqc_config'
error    : Corrupt
mythconverg.diseqc_tree
Error    : Incorrect file format 'diseqc_tree'
error    : Corrupt
mythconverg.displayprofilegroups
Error    : Incorrect file format 'displayprofilegroups'
error    : Corrupt
mythconverg.displayprofiles
Error    : Incorrect file format 'displayprofiles'
error    : Corrupt
mythconverg.dtv_multiplex
Error    : Incorrect file format 'dtv_multiplex'
error    : Corrupt
mythconverg.dtv_privatetypes
Error    : Incorrect file format 'dtv_privatetypes'
error    : Corrupt
mythconverg.dvdbookmark
Error    : Incorrect file format 'dvdbookmark'
error    : Corrupt
mythconverg.dvdinput
Error    : Incorrect file format 'dvdinput'
error    : Corrupt
mythconverg.dvdtranscode
Error    : Incorrect file format 'dvdtranscode'
error    : Corrupt
mythconverg.eit_cache
Error    : Incorrect file format 'eit_cache'
error    : Corrupt
mythconverg.filemarkup
Error    : Incorrect file format 'filemarkup'
error    : Corrupt
mythconverg.gallerymetadata
Error    : Incorrect file format 'gallerymetadata'
error    : Corrupt
mythconverg.gamemetadata
Error    : Incorrect file format 'gamemetadata'
error    : Corrupt
mythconverg.gameplayers
Error    : Incorrect file format 'gameplayers'
error    : Corrupt
mythconverg.housekeeping
Error    : Incorrect file format 'housekeeping'
error    : Corrupt
mythconverg.inputgroup
Error    : Incorrect file format 'inputgroup'
error    : Corrupt
mythconverg.inuseprograms
Error    : Incorrect file format 'inuseprograms'
error    : Corrupt
mythconverg.jobqueue
Error    : Incorrect file format 'jobqueue'
error    : Corrupt
mythconverg.jumppoints
Error    : Incorrect file format 'jumppoints'
error    : Corrupt
mythconverg.keybindings
Error    : Incorrect file format 'keybindings'
error    : Corrupt
mythconverg.keyword
Error    : Incorrect file format 'keyword'
error    : Corrupt
mythconverg.movies_movies
Error    : Incorrect file format 'movies_movies'
error    : Corrupt
mythconverg.movies_showtimes
Error    : Incorrect file format 'movies_showtimes'
error    : Corrupt
mythconverg.movies_theaters
Error    : Incorrect file format 'movies_theaters'
error    : Corrupt
mythconverg.music_albumart
Error    : Incorrect file format 'music_albumart'
error    : Corrupt
mythconverg.music_albums
Error    : Incorrect file format 'music_albums'
error    : Corrupt
mythconverg.music_artists
Error    : Incorrect file format 'music_artists'
error    : Corrupt
mythconverg.music_directories
Error    : Incorrect file format 'music_directories'
error    : Corrupt
mythconverg.music_genres
Error    : Incorrect file format 'music_genres'
error    : Corrupt
mythconverg.music_playlists
Error    : Incorrect file format 'music_playlists'
error    : Corrupt
mythconverg.music_smartplaylist_categories
Error    : Incorrect file format 'music_smartplaylist_categories'
error    : Corrupt
mythconverg.music_smartplaylist_items
Error    : Incorrect file format 'music_smartplaylist_items'
error    : Corrupt
mythconverg.music_smartplaylists
Error    : Incorrect file format 'music_smartplaylists'
error    : Corrupt
mythconverg.music_songs
Error    : Incorrect file format 'music_songs'
error    : Corrupt
mythconverg.music_stats
Error    : Incorrect file format 'music_stats'
error    : Corrupt
mythconverg.mythlog
Error    : Incorrect file format 'mythlog'
error    : Corrupt
mythconverg.mythweb_sessions
Error    : Incorrect file format 'mythweb_sessions'
error    : Corrupt
mythconverg.networkiconmap
Error    : Incorrect file format 'networkiconmap'
error    : Corrupt
mythconverg.newssites
Error    : Incorrect file format 'newssites'
error    : Corrupt
mythconverg.oldfind
Error    : Incorrect file format 'oldfind'
error    : Corrupt
mythconverg.oldprogram
Error    : Incorrect file format 'oldprogram'
error    : Corrupt
mythconverg.oldrecorded
Error    : Incorrect file format 'oldrecorded'
error    : Corrupt
mythconverg.people
Error    : Incorrect file format 'people'
error    : Corrupt
mythconverg.phonecallhistory
Error    : Incorrect file format 'phonecallhistory'
error    : Corrupt
mythconverg.phonedirectory
Error    : Incorrect file format 'phonedirectory'
error    : Corrupt
mythconverg.pidcache
Error    : Incorrect file format 'pidcache'
error    : Corrupt
mythconverg.playgroup
Error    : Incorrect file format 'playgroup'
error    : Corrupt
mythconverg.powerpriority
Error    : Incorrect file format 'powerpriority'
error    : Corrupt
mythconverg.profilegroups
Error    : Incorrect file format 'profilegroups'
error    : Corrupt
mythconverg.program
Error    : Incorrect file format 'program'
error    : Corrupt
mythconverg.programgenres
Error    : Incorrect file format 'programgenres'
error    : Corrupt
mythconverg.programrating
Error    : Incorrect file format 'programrating'
error    : Corrupt
mythconverg.recgrouppassword
Error    : Incorrect file format 'recgrouppassword'
error    : Corrupt
mythconverg.record
Error    : Incorrect file format 'record'
error    : Corrupt
mythconverg.record_tmp
Error    : Incorrect file format 'record_tmp'
error    : Corrupt
mythconverg.recorded
Error    : Incorrect file format 'recorded'
error    : Corrupt
mythconverg.recordedcredits
Error    : Incorrect file format 'recordedcredits'
error    : Corrupt
mythconverg.recordedfile
Error    : Incorrect file format 'recordedfile'
error    : Corrupt
mythconverg.recordedmarkup
Error    : Incorrect file format 'recordedmarkup'
error    : Corrupt
mythconverg.recordedprogram
Error    : Incorrect file format 'recordedprogram'
error    : Corrupt
mythconverg.recordedrating
Error    : Incorrect file format 'recordedrating'
error    : Corrupt
mythconverg.recordedseek
Error    : Incorrect file format 'recordedseek'
error    : Corrupt
mythconverg.recordingprofiles
Error    : Incorrect file format 'recordingprofiles'
error    : Corrupt
mythconverg.recordmatch
Error    : Incorrect file format 'recordmatch'
error    : Corrupt
mythconverg.romdb
Error    : Incorrect file format 'romdb'
error    : Corrupt
mythconverg.schemalock
Error    : Incorrect file format 'schemalock'
error    : Corrupt
mythconverg.settings
Error    : Incorrect file format 'settings'
error    : Corrupt
mythconverg.storagegroup
Error    : Incorrect file format 'storagegroup'
error    : Corrupt
mythconverg.tvchain
Error    : Incorrect file format 'tvchain'
error    : Corrupt
mythconverg.tvosdmenu
Error    : Incorrect file format 'tvosdmenu'
error    : Corrupt
mythconverg.upnpmedia
Error    : Incorrect file format 'upnpmedia'
error    : Corrupt
mythconverg.videocast
Error    : Incorrect file format 'videocast'
error    : Corrupt
mythconverg.videocategory
Error    : Incorrect file format 'videocategory'
error    : Corrupt
mythconverg.videocountry
Error    : Incorrect file format 'videocountry'
error    : Corrupt
mythconverg.videogenre
Error    : Incorrect file format 'videogenre'
error    : Corrupt
mythconverg.videometadata
Error    : Incorrect file format 'videometadata'
error    : Corrupt
mythconverg.videometadatacast
Error    : Incorrect file format 'videometadatacast'
error    : Corrupt
mythconverg.videometadatacountry
Error    : Incorrect file format 'videometadatacountry'
error    : Corrupt
mythconverg.videometadatagenre
Error    : Incorrect file format 'videometadatagenre'
error    : Corrupt
mythconverg.videosource
Error    : Incorrect file format 'videosource'
error    : Corrupt
mythconverg.videotypes
Error    : Incorrect file format 'videotypes'
error    : Corrupt

```

Not sure how to move forward from here.

---

### Post by OffAxis on 2009-12-03
I'd start here:
[http://dev.mysql.com/doc/refman/5.0/en/myisam-check.html](http://dev.mysql.com/doc/refman/5.0/en/myisam-check.html)

paying particular attention to this page:
[http://dev.mysql.com/doc/refman/5.0/en/myisam-crash-recovery.html](http://dev.mysql.com/doc/refman/5.0/en/myisam-crash-recovery.html)

And just in case you need it...
the three file types that page sites (.frm, .MYD, .MYI) are found in the /var/lib/mysql/ folder. Each database on your server will have a folder in there, and each table in your db will have those three files. They should all belong to mysql:mysql

---

### Post by OffAxis on 2009-12-03
If you need to re-create the database there are sql scripts in 
/usr/share/mythtv/sql/

I believe the correct re-create statement is:
```
mysql mythconverg </usr/share/mythtv/sql/mythtv_0.22.0.sql -u mythtv -p
```

You'll have to redo all your settings and you'll lose your recorded history, so I'd definitely try to recover them first.

---

### Post by williammanda on 2009-12-04
Well it appears that I had a problem with my hard drive. I had to boot using a usb stick with ubuntu and load smartmontools to do a drive check and repair. Just before that I tried a complete re-install of ubuntu and myth but had the same problem. Once I ran the smartmontools everything seems ok.

---

