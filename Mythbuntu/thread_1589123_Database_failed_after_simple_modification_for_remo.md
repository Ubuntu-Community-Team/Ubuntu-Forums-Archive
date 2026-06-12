---
title: "Database failed after simple modification for remote control"
date: 2010-10-05
forum: Mythbuntu
---

### Post by SchneiderIS on 2010-10-05
I made what I expected to be a simple change as documented for remote controlling of my frontend.    This happened after following posted instructions on how to enable MyMote use with MythTV.  What I did was follow the instructions at [http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2]("http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2") for initially the following:

```
$ mysql -u root mythconverg
mysql> grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv";
mysql> flush privileges;
```

and then followed with the instructions for:

> You'll also need to check that the "networking" feature of MySQL is turned on. Check that /etc/mysql/my.cnf does not contain skip-networking. If it does, either remove that line or comment it out. Also verify that bind-address is set to your IP address instead of 127.0.0.1. If you change either of these items, restart MySQL.

What ended up happening though is that suddenly my backend failed communications with MySQL and with that then went my frontend.

I have been looking in the logs for any sort of clues and cannot find a thing that makes any sense.

Has anyone seen this sort of behaviour or has some suggestions for debugging?

---

### Post by SchneiderIS on 2010-10-05
An update.

Looking at the passwords in MYSQL there appears to be different for some but I am not sure if it should be the same for all or not.  Here is what the output from the database is showing.

```
mysql> select host,user,password from user;
+-----------+------------------+-------------------------------------------+
| host      | user             | password                                  |
+-----------+------------------+-------------------------------------------+
| localhost | root             | *293705AF6DFE06C75E7922824B93841891DF3F96 |
| king      | root             | *293705AF6DFE06C75E7922824B93841891DF3F96 |
| 127.0.0.1 | root             | *293705AF6DFE06C75E7922824B93841891DF3F96 |
| localhost | debian-sys-maint | *8A8D5DCD4CE103ADA4A370D3B1AA8178BA8C5574 |
| localhost | mythtv           | *293705AF6DFE06C75E7922824B93841891DF3F96 |
| %         | mythtv           | *CC8F35F587CA5A556B4132C2407E556D92172FFC |
| 10.0.1.%  | mythtv           | *CC8F35F587CA5A556B4132C2407E556D92172FFC |
+-----------+------------------+-------------------------------------------+

```

How the change that I made could change this is a mistery to me.  

The end result is that going into MythConfig wants to reconfigure but it says that it can never get to SQL server and that there is no UpNP.  It can never actually do the configuration as a result.

---

### Post by SchneiderIS on 2010-10-06
Doing a "Test Connection" from "Mythbuntu Control Centre" results in a failure.

---

### Post by SchneiderIS on 2010-10-06
Is there no-one out there that can help?

---

### Post by ian dobson on 2010-10-07
Hi,

You should use the same password for all your mythtv accounts or just have one account MythTV @ % (% means all hosts).

Just use mysqladmin or myphpadmin to set the password to the same value as used by mythTV.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-07
Normally I would agree with you however not this time.  With all the passwords aligned I still get the same problem on the frontend.

Running the frontend with verbose on database I get the following that looks interesting:

```

2010-10-07 21:24:56.871 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'View Archive Log' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.872 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Play Created DVD' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.873 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Burn DVD' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.873 Cannot load language en_us for module mytharchive
2010-10-07 21:24:56.879 Cannot load language en_us for module mythbrowser
2010-10-07 21:24:56.881 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'browserdbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:56.882 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'browserdbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:56.882 Disabling Settings Cache.
2010-10-07 21:24:56.882 Clearing Settings Cache.
2010-10-07 21:24:56.883 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'webbrowsercommand' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.884 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'webbrowserzoomlevel' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.884 Enabling Settings Cache.
2010-10-07 21:24:56.885 Clearing Settings Cache.
2010-10-07 21:24:56.885 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'NEXTTAB' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.887 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Browser' AND action = 'PREVTAB' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.887 Registering WebBrowser as a media playback plugin.
2010-10-07 21:24:56.887 Cannot load language en_us for module mythbrowser
2010-10-07 21:24:56.896 Disabling Settings Cache.
2010-10-07 21:24:56.897 Clearing Settings Cache.
2010-10-07 21:24:56.898 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'gallerydbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:56.899 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'gallerydbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:56.899 Enabling Settings Cache.
2010-10-07 21:24:56.899 Clearing Settings Cache.
2010-10-07 21:24:56.902 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GalleryDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.903 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GalleryThumbnailLocation' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.904 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GallerySortOrder' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.905 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GalleryImportDirs' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.907 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GalleryMoviePlayerCmd' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.908 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SlideshowUseOpenGL' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.909 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SlideshowDelay' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.911 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GalleryRecursiveSlideshow' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:56.912 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SlideshowOpenGLTransition' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.913 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SlideshowOpenGLTransitionLength' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.915 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'GalleryOverlayCaption' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:56.916 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SlideshowTransition' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.917 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SlideshowBackground' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.918 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'MythGallery' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.919 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'PLAY' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.920 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'HOME' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.922 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'END' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.923 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SLIDESHOW' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.924 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'RANDOMSHOW' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.925 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ROTRIGHT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.926 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ROTLEFT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.927 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ZOOMOUT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.928 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ZOOMIN' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.929 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLUP' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.930 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLLEFT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.931 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLRIGHT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.932 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLDOWN' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.933 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'RECENTER' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.934 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'FULLSIZE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.935 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'UPLEFT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.936 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'LOWRIGHT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.937 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'MARK' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.938 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'FULLSCREEN' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:56.940 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'monitordrives' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.941 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mediachangeevents' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.942 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'ignoredevices' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:56.943 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'ignoredevices' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:56.952 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-10-07 21:24:56.953 Cannot load language en_us for module mythgallery
2010-10-07 21:24:56.959 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythmovies.databaseversion' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:56.960 Cannot load language en_us for module mythmovies
2010-10-07 21:24:57.015 Disabling Settings Cache.
2010-10-07 21:24:57.015 Clearing Settings Cache.
2010-10-07 21:24:57.017 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musicdbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.018 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musicdbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.018 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-10-07 21:24:57.018 Enabling Settings Cache.
2010-10-07 21:24:57.018 Clearing Settings Cache.
2010-10-07 21:24:57.029 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MusicLocation' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.030 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MusicAudioDevice' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.031 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MusicDefaultUpmix' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.032 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDDevice' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.034 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'AutoLookupCD' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.035 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'AutoPlayCD' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.036 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'KeyboardAccelerators' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.038 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'TreeLevels' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.039 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'ArtistTreeGroups' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.040 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'NonID3FileNameFormat' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.041 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'Ignore_ID3' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.043 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MusicTagEncoding' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.044 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDWriterEnabled' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.045 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDWriterDevice' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.047 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDDiskSize' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.048 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDCreateDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.049 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDWriteSpeed' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.050 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'CDBlankType' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.053 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'PlayMode' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.054 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'ResumeMode' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.055 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MusicExitAction' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.057 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MaxSearchResults' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.058 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MusicShowRatings' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.059 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'ShowWholeTree' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.060 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'ListAsShuffled' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.062 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'IntelliRatingWeight' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.063 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'IntelliPlayCountWeight' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.064 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'IntelliLastPlayWeight' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.065 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'IntelliRandomWeight' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.066 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualMode' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.067 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualCycleOnSongChange' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.069 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualAlbumArtOnSongChange' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.070 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualRandomize' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.071 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualModeDelay' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.072 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualScaleWidth' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.073 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VisualScaleHeight' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.075 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'ParanoiaLevel' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.076 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'FilenameTemplate' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.078 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'NoWhitespace' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.079 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'PostCDRipScript' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.080 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'EjectCDAfterRipping' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.081 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'EncoderType' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.082 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'DefaultRipQuality' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.084 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'Mp3UseVBR' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.085 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Play music' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.086 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Select music playlists' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.087 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Rip CD' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.088 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Scan music' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.089 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Show Music Miniplayer' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.090 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'NEXTTRACK' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.091 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'PREVTRACK' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.092 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'FFWD' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.093 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'RWND' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.094 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'PAUSE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.095 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'PLAY' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.096 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'STOP' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.097 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'VOLUMEDOWN' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.098 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'VOLUMEUP' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.100 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'MUTE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.101 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'TOGGLEUPMIX' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.102 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'CYCLEVIS' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.103 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'BLANKSCR' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.104 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'THMBUP' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.105 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'THMBDOWN' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.106 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'REFRESH' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.107 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'FILTER' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.108 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'INCSEARCH' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.109 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'INCSEARCHNEXT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.110 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'SPEEDUP' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.111 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'SPEEDDOWN' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.112 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-10-07 21:24:57.113 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musiclocation' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.114 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'ignore_id3' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.116 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'cddevice' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.117 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'playmode' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.119 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'repeatmode' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.120 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'repeatmode' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.121 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'resumemode' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.122 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musiclastplaydelay' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.123 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musiclastplaydelay' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.124 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musicautoshowplayer' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.125 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'musicautoshowplayer' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.126 Cannot load language en_us for module mythmusic
2010-10-07 21:24:57.134 Disabling Settings Cache.
2010-10-07 21:24:57.134 Clearing Settings Cache.
2010-10-07 21:24:57.135 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'netvisiondbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.136 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'netvisiondbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.137 Disabling Settings Cache.
2010-10-07 21:24:57.137 Clearing Settings Cache.
2010-10-07 21:24:57.138 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'MythNetSearch' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.139 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'MythNetTree' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.140 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythnetvision.backgroundfetch' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.141 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythnetvision.backgroundfetch' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.142 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythnetvision.rssbackgroundfetch' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.143 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythnetvision.rssbackgroundfetch' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.144 Cannot load language en_us for module mythnetvision
2010-10-07 21:24:57.150 Disabling Settings Cache.
2010-10-07 21:24:57.150 Clearing Settings Cache.
2010-10-07 21:24:57.151 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'newsdbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.152 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'newsdbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.152 Disabling Settings Cache.
2010-10-07 21:24:57.153 Clearing Settings Cache.
2010-10-07 21:24:57.153 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'MythNews' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.154 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'News' AND action = 'RETRIEVENEWS' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.155 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'News' AND action = 'FORCERETRIEVE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.157 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'News' AND action = 'CANCEL' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.158 Cannot load language en_us for module mythnews
2010-10-07 21:24:57.169 Disabling Settings Cache.
2010-10-07 21:24:57.170 Clearing Settings Cache.
2010-10-07 21:24:57.171 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythvideo.dbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.172 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythvideo.dbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.173 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dvddbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.174 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dvddbschemaver' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.175 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'videodbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.176 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'videodbschemaver' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.177 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythvideo.dbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.178 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'mythvideo.dbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.178 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-10-07 21:24:57.178 Enabling Settings Cache.
2010-10-07 21:24:57.178 Clearing Settings Cache.
2010-10-07 21:24:57.183 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoStartupDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.185 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.TrailersDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.186 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoArtworkDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.187 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.screenshotDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.188 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.bannerDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.190 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.fanartDir' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.191 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'DVDOnInsertDVD' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.192 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'DVDDriveSpeed' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.193 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'EnableDVDBookmark' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.194 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'DVDBookmarkPrompt' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.196 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'DVDBookmarkDays' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.197 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoDefaultParentalLevel' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.198 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoAdminPassword' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.200 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoAdminPasswordThree' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.201 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoAdminPasswordTwo' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.202 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'VideoAggressivePC' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.203 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.ParentalLevelFromRating' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.205 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.AutoR2PL1' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.206 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.AutoR2PL2' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.207 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.AutoR2PL3' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.208 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.AutoR2PL4' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.210 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'DVDRipLocation' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.211 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'TitlePlayCommand' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.213 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'SubTitleCommand' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.214 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'TranscodeCommand' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.215 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDPort' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.216 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDNiceLevel' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.218 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDConcurrentTranscodes' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.219 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDRipSize' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.220 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDLogFlag' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.221 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDac3Flag' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.225 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'MTDxvidFlag' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.226 MSqlQuery::exec(DBManager0) SELECT data  FROM settings WHERE value = 'mythvideo.TrustTranscodeFRDetect' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.227 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'MythVideo' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.228 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Video Manager' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.229 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Video Browser' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.230 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Video Listings' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.231 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Video Gallery' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.232 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'PLAYALT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.233 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'FILTER' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.234 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'BROWSE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.235 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'INCPARENT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.236 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'DECPARENT' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.237 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'INCSEARCH' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.238 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'DOWNLOADDATA' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.239 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'ITEMDETAIL' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.240 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'HOME' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.241 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'END' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.242 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Play DVD' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.243 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Play VCD' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.244 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'Rip DVD' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.245 Cannot load language en_us for module mythvideo
2010-10-07 21:24:57.252 Disabling Settings Cache.
2010-10-07 21:24:57.253 Clearing Settings Cache.
2010-10-07 21:24:57.258 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'weatherdbschemaver' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.259 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'weatherdbschemaver' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.260 Enabling Settings Cache.
2010-10-07 21:24:57.260 Clearing Settings Cache.
2010-10-07 21:24:57.261 MSqlQuery::exec(DBManager0) SELECT keylist FROM jumppoints WHERE destination = 'MythWeather' and hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.262 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'PAUSE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.263 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'SEARCH' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.264 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'NEXTSEARCH' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.265 MSqlQuery::exec(DBManager0) SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'UPDATE' AND hostname = 'familyroom' ; <<<< Returns 1 row(s)
2010-10-07 21:24:57.266 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'weatherbackgroundfetch' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.268 MSqlQuery::exec(DBManager0) SELECT DISTINCT wss.sourceid, source_name, update_timeout, retrieve_timeout, path, author, version, email, types FROM weathersourcesettings wss LEFT JOIN weatherdatalayout wdl ON wss.sourceid = wdl.weathersourcesettings_sourceid WHERE hostname = 'FamilyRoom'; <<<< Returns 10 row(s)
2010-10-07 21:24:57.270 MSqlQuery::exec(DBManager0) SELECT DISTINCT location, weathersourcesettings_sourceid,                 weatherscreens.units, weatherscreens.screen_id FROM weatherdatalayout,weatherscreens WHERE weatherscreens.screen_id = weatherscreens_screen_id AND       weatherscreens.hostname = 'FamilyRoom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.271 Cannot load language en_us for module mythweather
2010-10-07 21:24:57.272 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'networkcontrolenabled' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.274 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'networkcontrolport' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.275 NetworkControl: Listening for remote connections on port 6546
2010-10-07 21:24:57.276 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'theme' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.278 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'allowquitshutdown' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.278 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Arclight/menu-ui.xml
2010-10-07 21:24:57.295 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'dateformat' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.298 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'shortdateformat' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.299 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'timeformat' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.421 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-10-07 21:24:57.423 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'language' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:57.425 Found mainmenu.xml for theme 'Arclight'
2010-10-07 21:24:57.459 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'idletimeoutsecs' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.460 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'idletimeoutsecs' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.461 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'masterserverip' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.462 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'masterserverip' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.464 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'masterserverport' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.465 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'masterserverport' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.466 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'wolbackendcommand' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.467 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'wolbackendcommand' AND hostname IS NULL <<<< Returns 1 row(s)
2010-10-07 21:24:57.468 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'backendconnectretry' AND hostname = 'familyroom' <<<< Returns 0 row(s)
2010-10-07 21:24:57.469 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'backendconnectretry' AND hostname IS NULL <<<< Returns 0 row(s)
2010-10-07 21:24:57.469 MythContext: Connecting to backend server: 10.0.1.55:6543 (try 1 of 1)
2010-10-07 21:24:57.470 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-10-07 21:24:59.221 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'nopromptonexit' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:24:59.222 MythContext: Connecting to backend server: 10.0.1.55:6543 (try 1 of 1)
2010-10-07 21:24:59.222 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-10-07 21:24:59.223 MSqlQuery::exec(DBManager0) SELECT data FROM settings WHERE value = 'overrideexitmenu' AND hostname = 'familyroom' <<<< Returns 1 row(s)
2010-10-07 21:25:01.571 Deleting UPnP client...

```

This is a small snippit of the log but you can see that there are records coming back but with the last ones giving the indication of problems.  What I don't know as of yet is where the database is that the frontend is querying, is it the backend?

---

### Post by ian dobson on 2010-10-07
Hi,

Are you sure your backend is running/ip address is ok:-

```
2010-10-07 21:24:57.469 MythContext: Connecting to backend server: 10.0.1.55:6543 (try 1 of 1)
2010-10-07 21:24:57.470 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address
```

The frontend appears to be getting data from the sql server, but can't connect to the mythtv backend server.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-08
It looks to me like it is running.  Pardon my asking a question that I should know but is there a way to tell from the terminal?

---

### Post by SchneiderIS on 2010-10-08
Looking at the mythbackend.log I find the following repeating itself which makes me think there is still a database issue.

```
Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-10-07 22:13:56.495 Deleting UPnP client...
2010-10-07 22:13:57.068 Failed to init MythContext, exiting.
2010-10-07 22:13:57.281 mythbackend version: branches/release-0-23-fixes [s25362] www.mythtv.org
2010-10-07 22:13:57.281 Using runtime prefix = /usr
2010-10-07 22:13:57.316 Using configuration directory = /home/mythtv/.mythtv
2010-10-07 22:13:57.328 Empty LocalHostName.
2010-10-07 22:13:57.336 Using localhost value of mythtv-primary
2010-10-07 22:13:57.345 Testing network connectivity to 'mythconverg'
................................................................................
2010-10-07 22:13:59.926 UPnPautoconf() - No UPnP backends found
2010-10-07 22:13:59.935 No UPnP backends found
```

Or is there specifically a UPnP setup problem?

---

### Post by SchneiderIS on 2010-10-08
Running Mythtv-setup gives no indication of problems as it starts and I can look at the configuration.  Running fill database also appears to be running fine.

---

### Post by SchneiderIS on 2010-10-08
Did a "ps -aef" and it shows the mythbackend in the list so I think it is running.  It looks to me like the backend though is not listening for any connections to it.

---

### Post by ian dobson on 2010-10-08
Hi,

OK
1) Check if the IP addresses defined in your mysql.txt are correct (Usually in your home directory/mythtv). Also check the login name/passwords
2) Try pinging the IP address defined for all your myth systems.
3) Check the my.cnf (/etc/mysql/my.cnf) that mysql is binding to all IP addresses.
4) Delete the mythtv user (all of them) and recreate only one account that is valid for all IP addresses.
5) Make sure the backend starts up without any errors.
6) When the backend starts correctly check that the frontend starts OK.

When the Frontend starts, it reads it's configuration information out of the SQL database (using mysql.txt to find IP/Name/password), one of the config options that it reads is the IP address of the Master Backend MythTV process. The frontend attempts to connect to this process using the IP address read on port 6543. In your case it looks as if the backend process is stuck in an endless loop. The message :-
```
Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
```
Worries me abit, it looks as if the backend process can't find the configuration for the mySQL server. Maybe have a look there first.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-08
I thought the same thing about not being able to read the database but the verbose database on starting the frontend showed rows being retrieved so that is where I started to wonder about another database being used.  

[/QUOTE]1) Check if the IP addresses defined in your mysql.txt are correct (Usually in your home directory/mythtv). Also check the login name/passwords[/QUOTE]

They all match up.

> 2) Try pinging the IP address defined for all your myth systems.

They ping with no problem.

> 3) Check the my.cnf (/etc/mysql/my.cnf) that mysql is binding to all IP addresses.

here is the content of my "my.cnf".

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 10.0.1.55
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

It appears to be binding to the right IP address.  Not sure how it would bind to all including the localhost.

> 4) Delete the mythtv user (all of them) and recreate only one account that is valid for all IP addresses.

If I delete and then recreate the mythtv user, is there a script for creation of the user that has all the grants that are required?

---

### Post by ian dobson on 2010-10-08
Hi,

Just remove the line bind-address= 10.0.1.55 and get rid of the tabs. Mysql will then bind to all ip addresses.
You'll need to manually recreate the use/set the right correctly. The mythtv user needs full rights for the mythconverg table.
 
Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-08
Did the bind instruction but what did you mean by "get rid of the tabs"?

---

### Post by ian dobson on 2010-10-08
Hi,

You've used the tab key to format the config file. Just use spaces.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-08
Ah, that was from the default.

---

### Post by SchneiderIS on 2010-10-08
Did all that including the dropping and recreating of the user.  I granted ALL from mythconverge to the new mythtv user and still the same problem.

I can't help but think this is a permissions problem that I just haven't seen.  I need to find the database creation scripts and go through to see what is created and granted to see what I might be missing.  My suspicion is that there is something created in the mythtv users account and if so it is missing.

---

### Post by SchneiderIS on 2010-10-08
I have looked through the mtythtv sql scripts and the only other thing that I could see being needed was the temp grants.  Otherwise I have executed the scripts to no avail.

Any other ideas?

---

### Post by SchneiderIS on 2010-10-08
Here is something that may be a pointer.  I found a post that used netstat and ran the following command that gave the following output.

```
sudo netstat -tunap | grep 'mythbackend'
tcp        0      0 0.0.0.0:6549            0.0.0.0:*               LISTEN      8055/mythbackend
udp        0      0 255.255.255.255:1900    0.0.0.0:*                           8055/mythbackend
udp        0      0 239.255.255.250:1900    0.0.0.0:*                           8055/mythbackend
udp        0      0 0.0.0.0:6549            0.0.0.0:*                           8055/mythbackend

```

It looks to me like the listener is not looking at the right port or rather for the right IP.   I don't really understand this enough though to know if that is the case.

---

### Post by ian dobson on 2010-10-09
Hi,

That could well be it. I think you can change the default port in mythtv-setup.

First make sure your backend is running 100%, that start looking at the frontend. I imagine that your "simple remote change" changed/deleted one of the basic system parameters from the mysql settings table.

Is your backend really called mythtv-primary? Do you have the correct settings for this host?

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-09
It is called mythtv-primary but I refer to everything via the static IP address.  I wish the verbose database would actually display the SQL that is being executed and the connection parameters.  I feel like I am running blind here and chasing an issue that may actually have a resolution in a completely different area.

---

### Post by SchneiderIS on 2010-10-09
Ian, could you run the "sudo lsof -i | grep 'mythbackend'" statement against your backend andpost what you get?

Could you also post your config.xml for me?

Here is another question for you.  When you run "sudo dpkg-reconfigure mythtv-database" is the only prompt that you get the one for selecting if other computers are going to hit the machine or do you get prompted for other settings as well?

---

### Post by ian dobson on 2010-10-09
Hi,

sudo lsof -i | grep mythbackend doesn't return any open files on my backend.

```
 cat /etc/mythtv/config.xml
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.0.2</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>HIDDEN</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>
```

dpkg-reconfigure mythtv-database only askes if multiple computers should connect to the backend.

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-09
Thanks Ian.

I have it fixed.

So I couldn't sleep tonight and thought I would give things another try.  Part of what I was concerned with was the idea that perhaps the password was hard encoded somewhere within Myth.  As such I went back to MySQL and changed the single MythTV user to have the mythtv password.  I then went to all the config.xml's and changed them to use the new password.  I then deleted all the mysql.txt files.

Now comes the part that I think really did it though.  I found an archive of a forum thread where a couple of people were having a similar problem.  The main helper though noted the following:

> This stems from something exclusive to Ubuntu/Debian MythTV packages that you don't necessarily find in other distros' packages. If you are wanting to update any passwords on your MythTV setup for Ubuntu, its best to do it via dpkg-reconfigure rather than forcefully with phpmyadmin and manually editing ~/.mythtv/mysql.txt or /etc/mythtv/mysql.txt. The password, username, database, and other information are all stored in the debconf database so that future packages can take advantage of this information directly rather than having to use sed/awk/grep on misc mysql.txt files.

If this is the case then the password is not likely hard encoded within the myth source but rather in "debconf" which never gets raised in most postings.

When running "sudo dpkg-reconfigure mythtv-common" I reset the password but I also found another little nasty in that the value for where to find the host was set to "mythconverge" rather than the IP of my server.

I also ran "sudo dpkg-reconfigure mythtv-database" (after mythtv-common so that any adjustments from common would be used here) which only has that one setting but I think it did another interesting bit.  If you recall we deleted all the mythtv accounts from mysql and then created only the mythtv@% account.  Well going back in the mythtv@localhost was now in the list again.  This I  think was a critical part because in looking at my logs I had found some references to localhost that had been bugging me.  I was actually going to go into the database and add it back in myself when I found this out.

So, I did a reboot and now the backend and the frontends are working.  Well sort of.  In doing my testing of the remote frontend I changed channels a couple of times and that caused the frontend to crash but that is for another thread.

Thanks for all your help Ian.

---

### Post by ian dobson on 2010-10-09
Hi,

Good to hear. Sometimes small changes have huge side effects.

Now to get back to my attempt to backup 4Tb data (don't ask).

Regards
Ian Dobson

---

### Post by SchneiderIS on 2010-10-09
Good luck with the backup Ian.  4Tb is not going to be fun to find media for if you don't have a tape drive.

---

