---
title: "iPod Touch syncing problem in Lucid"
date: 2010-09-29
forum: Multimedia Software
---

### Post by chaanakya_chiraag on 2010-09-29
Hey guys!

I'm running Lucid and am syncing my iPod Touch 1G (3.1.3 software) with Rhythmbox.  I'm trying to create playlists (I haven't found a way to sync my smart playlists with the iPod Touch yet) on the iPod Touch.  Whenever I try, it works for a short while (1 or 2 playlists).  Then, it suddenly crashes.  I ran it from Terminal and got the following output:
```
(process:3290): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(process:3290): Gdk-WARNING **: locale not supported by C library
** (rhythmbox:3290): DEBUG: Loading the real store page
** (rhythmbox:3290): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 723804: 2000400. Trying to continue.


** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 725116: 2000400. Trying to continue.


** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 726426: 2000400. Trying to continue.


** (rhythmbox:3290): WARNING **: Unknown action (0x2000400) in smart playlist will be ignored.


** (rhythmbox:3290): WARNING **: Unknown smart rule action at 728944: 2000400. Trying to continue.

Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=05ac and PID=1291) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team

(rhythmbox:3290): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/chiraag/.gvfs/Chiraag%2527s%20iPod%20Touch/iTunes_Control/Music/F35/03%20-%20Track%203.m4a

(rhythmbox:3290): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/chiraag/.gvfs/Chiraag%2527s%20iPod%20Touch/iTunes_Control/Music/F34/08%20-%20Track%208.m4a
** (rhythmbox:3290): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=480&partner=983
libitdbprep: itdb_iphone_start_sync called with uuid=bde24831f4765347c27fb0f5d852c14b62fcebba
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file /home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunesCDB and uuid bde24831f4765347c27fb0f5d852c14b62fcebba
itlp directory='/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileVBVlBO/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 479 tracks
[mk_Dynamic] - processing 7 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileVBVlBO/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileVBVlBO/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xe4ceb9c77496bbd9
[mk_Library] Processing '/tmp/fileVBVlBO/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Chiraag's iPod Touch' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Geeta Dutt' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Golden Collection - Duets' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Good Music' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kalinga Rao' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kishore Kumar' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Lata Mangeshkar Duets' into "container"
library_persistent_id = 0xe4ceb9c77496bbd9
device name = Chiraag's iPod Touch
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 479 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileVBVlBO/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 479 tracks...
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
itdbprep: copying 'Dynamic.itdb'
itdbprep: copying 'Extras.itdb'
itdbprep: copying 'Genius.itdb'
itdbprep: copying 'Library.itdb'
itdbprep: copying 'Locations.itdb'
itdbprep: copying 'Locations.itdb.cbk'
libitdbprep: itdb_iphone_stop_sync called
Could not delete '.status-com.apple.itdprep.command.runPostProcess'
itdb_iphone_stop_sync: posted syncDidFinish
libitdbprep: itdb_iphone_start_sync called with uuid=bde24831f4765347c27fb0f5d852c14b62fcebba
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

** (rhythmbox:3290): WARNING **: Unknown action type 33555456



** (rhythmbox:3290): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed
libitdbprep: itdb_sqlite_generate_itdbs called with file /home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunesCDB and uuid bde24831f4765347c27fb0f5d852c14b62fcebba
itlp directory='/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
*.itdb files will be stored in '/home/chiraag/.gvfs/Chiraag%27s iPod Touch/iTunes_Control/iTunes/iTunes Library.itlp'
[mk_Dynamic] Processing '/tmp/fileWjUDvX/Dynamic.itdb'
[mk_Dynamic] creating table structure
[mk_Dynamic] - processing 479 tracks
[mk_Dynamic] - processing 8 playlists
[mk_Dynamic] done.
[mk_Extras] Processing '/tmp/fileWjUDvX/Extras.itdb'
[mk_Extras] re-building table structure
[mk_Extras] done.
[mk_Genius] Processing '/tmp/fileWjUDvX/Genius.itdb'
[mk_Genius] re-building table structure
[mk_Genius] done.
library_persistent_id = 0xe4ceb9c77496bbd9
[mk_Library] Processing '/tmp/fileWjUDvX/Library.itdb'
[mk_Library] building table structure
[mk_Library] compiling SQL statements
[mk_Library] - inserting into "version_info"
[mk_Library] - inserting into "genre_map"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Chiraag's iPod Touch' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Geeta Dutt' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Golden Collection - Duets' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Good Music' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kalinga Rao' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Kishore Kumar' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'Lata Mangeshkar Duets' into "container"
[mk_Library] - inserting songs into "item_to_container"
[mk_Library] - inserting playlist 'New playlist' into "container"
library_persistent_id = 0xe4ceb9c77496bbd9
device name = Chiraag's iPod Touch
[mk_Library] - inserting into "db_info"
[mk_Library] - processing 479 tracks
[mk_Library] done.
[mk_Locations] Processing '/tmp/fileWjUDvX/Locations.itdb'
[mk_Locations] re-building table structure
[mk_Locations] Processing 479 tracks...
[mk_Locations] done.
[run_post_process_commands] Getting SQL post process commands
[run_post_process_commands] WARNING: ignoring non-string value for key 'Version'
[run_post_process_commands] Running 240 post process commands now
[run_post_process_commands] ERROR when executing 'AddIsITunesUColumn': duplicate column name: is_itunes_u
[run_post_process_commands] 239 out of 240 post process commands successfully executed
[run_post_process_commands] done.
itdbprep: copying 'Dynamic.itdb'
itdbprep: copying 'Extras.itdb'
itdbprep: copying 'Genius.itdb'
itdbprep: copying 'Library.itdb'
itdbprep: copying 'Locations.itdb'
itdbprep: copying 'Locations.itdb.cbk'
libitdbprep: itdb_iphone_stop_sync called
itdb_iphone_stop_sync: posted syncDidFinish
Segmentation fault

```Does anyone know what's going on?  Thanks!

---

### Post by chaanakya_chiraag on 2010-09-30
Sorry if this is too soon, but...bump?

---

### Post by chaanakya_chiraag on 2010-10-03
No one??

---

