---
title: "Problem with database: Can't find file (error 2)"
date: 2010-06-15
forum: Mythbuntu
---

### Post by jb5 on 2010-06-15
I can no longer backup my database.
Last successful DB backup 12 days ago, so installing previous backup not really an option.

Lucid (64) Mythtv 0.23 + Fixes {up-to date as of today}

```

Configuring environment:
  -    username: jb
  -        HOME: /home/jb
  - MYTHCONFDIR: /home/jb/.mythtv

Parsing configuration files:
  - checking: /home/jb/.mythtv/config.xml
     parsing: /home/jb/.mythtv/config.xml
  - checking: /home/jb/.mythtv/backuprc
     parsing: /home/jb/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

No DBSchemaVer specified, querying database.
Found DBSchemaVer: 1254.

Database Information:
         DBHostName: localhost
             DBPort: 0
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 1254
  DBBackupDirectory: /hmv/MythtvDBbackup
   DBBackupFilename: mythconverg-1254-20100614154913.sql

Executables:
          mysqldump: mysqldump
           compress: gzip

Attempting to use supplied password for mysqldump.
Any [client] or [mysqldump] password specified in the MySQL options file will
take precedence.

Executing command:
'/usr/bin/mysqldump' --defaults-extra-file='/tmp/9dH5lMw81r' --host='localhost' --user='mythtv' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick --add-drop-table 'mythconverg' 2>&1 1>'/hmv/MythtvDBbackup/mythconverg-1254-20100614154913.sql'

mysqldump exited with status: 2
mysqldump output:
mysqldump: Got error: 1017: Can't find file: 'channelscan_channel' (errno: 2) when using LOCK TABLES

```

After searching around tried to repair using following```
sudo service mythtv-backend stop
mysqlcheck -r -A -umythtv -p > repair.log
```
repair log```

mythconverg.archiveitems                           OK
mythconverg.callsignnetworkmap                     OK
mythconverg.capturecard                            OK
mythconverg.cardinput                              OK
mythconverg.channel                                OK
mythconverg.channelgroup                           OK
mythconverg.channelgroupnames                      OK
mythconverg.channelscan                            OK
mythconverg.channelscan_channel
Error    : Can't find file: 'channelscan_channel' (errno: 2)
status   : Operation failed
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
mythconverg.inuseprograms                          OK
mythconverg.jobqueue                               OK
mythconverg.jumppoints                             OK
mythconverg.keybindings                            OK
mythconverg.keyword                                OK
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
mythconverg.musicmetadata                          OK
mythconverg.musicplaylist                          OK
mythconverg.mythlog
Error    : Can't find file: 'mythlog' (errno: 2)
status   : Operation failed
mythconverg.networkiconmap                         OK
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
mythconverg.recordedcredits                        OK
mythconverg.recordedfile                           OK
mythconverg.recordedmarkup                         OK
mythconverg.recordedprogram                        OK
mythconverg.recordedrating                         OK
mythconverg.recordedseek                           OK
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
mythconverg.videocountry                           OK
mythconverg.videogenre                             OK
mythconverg.videometadata                          OK
mythconverg.videometadatacast                      OK
mythconverg.videometadatacountry                   OK
mythconverg.videometadatagenre                     OK
mythconverg.videosource                            OK
mythconverg.videotypes                             OK
mythconverg.weatherdatalayout
note     : The storage engine for the table doesn't support repair
mythconverg.weatherscreens
note     : The storage engine for the table doesn't support repair
mythconverg.weathersourcesettings
note     : The storage engine for the table doesn't support repair
mythconverg.websites                               OK
```

Not really clued in on database manipulation / repair.

Anybody any ideas how I can SAFELY rectify this problem?

---

