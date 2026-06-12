---
title: "sync iPhone to gtkpod?"
date: 2010-02-24
forum: Multimedia Software
---

### Post by id10twork on 2010-02-24
I know it is possible to add music to my iPhone through gtkpod, but I have no idea how, and I heard it's quite a feat to do it. I'd really appreciate any help in finding out how to get this done.

---

### Post by mastermindg on 2010-02-24
I'm running Karmic Koala and have my iPod Touch 3.1 working with RhythmBox - syncing music,playlists...

gtkpod is giving me this error when attempting to initiliaze my iPod when mounted with fuse:

```
The overwriting error message was: iTunes directory not found: '/mnt/ipod/iPod_Control/iTunes' (or similar).
```

This path seems to be for previous versions, maybe before 3.0. 

Has anybody gotten gtkpod to work with an iPhone or iPod Touch running 3.1?

---

### Post by Kruptein on 2010-02-24
You have a lot of options,
gtkpod and rhythmbox were not sufficient for me =D
I use Songbird

but I thought if you plugin your ipod and choose gtkpod it would work?
have you tried that yet

---

### Post by mastermindg on 2010-02-24
It works fine if I open with RhythmBox. The mount path is following:

afc://ce78b6b40dd452fe5b8a3c05fd245ec68468e866/
which is a repoint from
/home/ken/.gvfs/ken's iPod/

What is weird is the RhythmBox uses libgpod just like gtkpod does. I'm not sure what one works and another doesn't. It seems that gtkpod is looking for an old iTunesDB while RhythmBox is using the correct iTunesDB for 3.x.

It would be awesome if somebody could shed some light on this subject :-)

---

### Post by Kruptein on 2010-02-24
if you start gtkpod from command line, does it throw any error?

---

### Post by mastermindg on 2010-02-24
It did originally, the error that I posted earlier. But I just created the directory: /mnt/ipod/iPod_Control/iTunes

OK, made some progress:

I figured out that I was using the wrong model in gtkpod. I switched to the one being used in RhythmBox. This is how far I got now:

```
~/Downloads/libgpod$ gtkpod

Couldn't find get device UUID itdbprep processing won't work!ERROR: Could not start sync!
libitdbprep: itdb_sqlite_generate_itdbs called with file (null) and uuid (null)
itlp directory='afc://ce78b6b40dd452fe5b8a3c05fd245ec68468e866/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in 'afc://ce78b6b40dd452fe5b8a3c05fd245ec68468e866/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/filej4bUZ3/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - No tracks available, none written.
[mk_Dynamic] - processing 1 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/filej4bUZ3/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/filej4bUZ3/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xd2ddb77c7a8744f3
[mk_Library] Processing '/tmp/filej4bUZ3/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'ken’s iPod 2andahalf' into "container"
library_persistent_id = 0xd2ddb77c7a8744f3
device name = ken’s iPod 2andahalf
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 0 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/filej4bUZ3/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] No tracks available, none written.
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
libitdbprep: itdb_iphone_stop_sync called
Segmentation fault
```

---

### Post by alextop30 on 2010-02-24
This should explain a lot [http://www.howtoforge.com/linux_gtkpod_ipod](http://www.howtoforge.com/linux_gtkpod_ipod) I just did this and it works out. The only complaint is that its kind of slow and it does not allow you to fix detected problems on the spot but it has to be done manually. For example if there are duplicate songs you have to search for them and erase the doubles. 

I am still glad there is something so that I can kick itunes. And by the way songbird does not really work. You have to run an older version of the program on top of which I cannot get it to even see where the ipod is mounted.

---

### Post by mastermindg on 2010-02-24
Well, it worked for a second. Bypassing the rewrite seems to have pushed something. However, gtkpod still had no update abilities and syncing failed. Now that I've restarted it I'm unable to load my iPod up again. I've tried removing and recreating the repository. 

Even worse it seems to have blown away my iTunesDB. My iPod is automounted with fuse with rw permissions, and perfectly accessible in every way. Still gtkpod is causing me grief.:(

I ended up restoring my iPod to 3.1.2 and re-jailbreaking it because the iTunesDB was shot. I'll retry gtkpod once this is done.

---

### Post by mastermindg on 2010-02-24
Still having the issue with gtkpod not looking in the right place for my iTunesDB. It keeps looking under iPod_Control.

---

### Post by id10twork on 2010-02-24
Thanks for tacking your problem on to my thread, that's really awesome that you put yourself before me and got people to help you instead or me. I'll go make a new thread so I can get help.

---

### Post by mastermindg on 2010-02-25
It's the same issue. If you think you can get more answers out of another post, then have it at.

---

### Post by mastermindg on 2010-02-25
id10twork:

Are you running Karmic? Which firmware do you have on your iPhone? 

If you are running Karmic and have 3.1.2 or lower you can use the following guide to get this working:

[URL="http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html"]http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html
[/URL]

If you are running an Jaunty or earlier you can use this guide:

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/]("http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/")

If you are running firwmare 3.1.3 on your iPhone you can go here to grab the 3.1.2 firmware:

[http://www.felixbruns.de/iPod/firmware/]("http://www.felixbruns.de/iPod/firmware/")

Plug your iPhone into a Windows/Mac with iTunes and do a Shift+Restore, find the 3.1.2 image and let it load. Once it's loaded libgpod will have access to the hash via usbmuxd.

Sorry for hijacking your thread, it wasn't my intention. I figured out my issue and am now up and running. Make sure not to create an iPod_Control directory if you are running 3.x firmware :-) 

Besides that, if you have any questions or issues I"m more than qualified to answer them now that I've compiled libgpod half-a-dozen times now.

---

### Post by etteling on 2010-04-01
> **mastermindg said:**
> It did originally, the error that I posted earlier. But I just created the directory: /mnt/ipod/iPod_Control/iTunes

OK, made some progress:

I figured out that I was using the wrong model in gtkpod. I switched to the one being used in RhythmBox. This is how far I got now:

```
~/Downloads/libgpod$ gtkpod

Couldn't find get device UUID itdbprep processing won't work!ERROR: Could not start sync!
libitdbprep: itdb_sqlite_generate_itdbs called with file (null) and uuid (null)
itlp directory='afc://ce78b6b40dd452fe5b8a3c05fd245ec68468e866/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in 'afc://ce78b6b40dd452fe5b8a3c05fd245ec68468e866/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/filej4bUZ3/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - No tracks available, none written.
[mk_Dynamic] - processing 1 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/filej4bUZ3/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/filej4bUZ3/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xd2ddb77c7a8744f3
[mk_Library] Processing '/tmp/filej4bUZ3/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'ken&#8217;s iPod 2andahalf' into "container"
library_persistent_id = 0xd2ddb77c7a8744f3
device name = ken&#8217;s iPod 2andahalf
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 0 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/filej4bUZ3/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] No tracks available, none written.
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
libitdbprep: itdb_iphone_stop_sync called
Segmentation fault
```
Hi mastermindg,

I am having exactly the same problem as this (although I am getting these errors from Rhythmbox, but the exact same run_post_process_commands errors). How did you resolve this problem?

This is what rhythmbox outputs to the console, from when I try to add a track:

```

Couldn't find get device UUID itdbprep processing won't work!ERROR: Could not start sync!

** (rhythmbox:2639): WARNING **: Unknown action type 2048



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:2639): WARNING **: Unknown action type 2048



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:2639): WARNING **: Unknown action type 33556480



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:2639): WARNING **: Unknown action type 33556480



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:2639): WARNING **: Unknown action type 2048



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:2639): WARNING **: Unknown action type 2048



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:2639): WARNING **: Unknown action type 2048



** (rhythmbox:2639): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file /home/candide/.gvfs/iPhone %7BYvette%7D/iTunes_Control/iTunes/iTunesCDB and uuid (null)
itlp directory='/home/candide/.gvfs/iPhone %7BYvette%7D/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/home/candide/.gvfs/iPhone %7BYvette%7D/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileAgcvzq/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 1 tracks
[mk_Dynamic] - processing 1 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileAgcvzq/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileAgcvzq/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xf091d81a18fbf96f
[mk_Library] Processing '/tmp/fileAgcvzq/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'iPhone {Yvette}' into "container"
library_persistent_id = 0xf091d81a18fbf96f
device name = iPhone {Yvette}
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 1 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileAgcvzq/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 1 tracks...
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
libitdbprep: itdb_iphone_stop_sync called
Segmentation fault (core dumped)

```




Thanks,
etteling

---

### Post by FunkyM on 2010-04-02
> Couldn't find get device UUID itdbprep processing won't work!

If you see above error, you have not yet setup your iPhone or iPod Touch to correctly sync using any libgpod application.

To fix it simply do this:

[LIST=1]
[*]Get the 40-digit hex UUID (Unique ID of your iPhone/iPod Touch) by running "idevice_id -l" or "ideviceinfo -k UniqueDeviceID" or copy it from the afc://<uuid>/ uri in Nautilus.
[*]Make sure to have the folder "iTunes_Control/Device" on the device, if not create one.
[*]Run "ipod-read-sysinfo-extended <UUID> ~/.gvfs/<IPOD NAME>/" and check if a SysInfoExtended file was created in the "iTunes_Control/Device" folder.
[*]Have fun syncing with gtkpod/rhythmbox and libgpod friends.
[/LIST]

The issue is already fixed upstream and will be available in the next libgpod release, so no more fiddling around with this in the future.

---

### Post by etteling on 2010-04-02
Thank you so much, FunkyM! This has been driving me crazy. :)

---

