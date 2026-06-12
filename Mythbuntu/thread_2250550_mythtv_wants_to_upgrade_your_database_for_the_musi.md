---
title: "mythtv wants to upgrade your database for the music schema from 1005 to 1020"
date: 2014-10-29
forum: Mythbuntu
---

### Post by AlecJ on 2014-10-29
every time I start Mythfrontend I get 20sec's of white screen followed by:-
mythtv wants to upgrade your database for the music schema from 1005 to 1020, EXIT or UPGRADE
 I say UPGRADE
 it says
"If your system becomes unstable, a database backup file called
mythconverg-1317-20141029132158.sql.gz
is located in /media/store3/Backups/db_backups

There are other clients using this database. they should be shut down first. EXIT or UPGRADE
I say UPGRADE

I'm then presented with the normal menu, BUT minus the Music?

don't think the database is getting updated

I Google'ed but only found references to .22 where they deleted .ICEautherity so I tried that but had no effect

then I ran from a terminal with super user still not able to update

```
~$ sudo mythfrontend2014-10-29 13:34:21.233434 I  Setup Interrupt handler
2014-10-29 13:34:21.233458 I  Setup Terminated handler
2014-10-29 13:34:21.233466 I  Setup Segmentation fault handler
2014-10-29 13:34:21.233475 I  Setup Aborted handler
2014-10-29 13:34:21.233482 I  Setup Bus error handler
2014-10-29 13:34:21.233491 I  Setup Floating point exception handler
2014-10-29 13:34:21.233499 I  Setup Illegal instruction handler
2014-10-29 13:34:21.233509 I  Setup Real-time signal 0 handler
2014-10-29 13:34:21.233520 I  Setup User defined signal 1 handler
2014-10-29 13:34:21.233529 I  Setup User defined signal 2 handler
2014-10-29 13:34:21.233627 C  mythfrontend version: fixes/0.27 [v0.27.4-6-ge0b0027] www.mythtv.org
2014-10-29 13:34:21.233633 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-10-29 13:34:21.233637 N  Enabled verbose msgs:  general
2014-10-29 13:34:21.233649 N  Setting Log Level to LOG_INFO
2014-10-29 13:34:21.244966 N  Using runtime prefix = /usr
2014-10-29 13:34:21.245017 I  Added logging to the console
2014-10-29 13:34:21.245020 N  Using configuration directory = /home/alectv/.mythtv
2014-10-29 13:34:21.245172 I  Assumed character encoding: en_GB.UTF-8
2014-10-29 13:34:21.246097 N  Empty LocalHostName.
2014-10-29 13:34:21.246114 I  Using localhost value of alectv
2014-10-29 13:34:21.269624 N  Setting QT default locale to en_GB
2014-10-29 13:34:21.269748 I  Current locale en_GB
2014-10-29 13:34:21.269827 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2014-10-29 13:34:21.277982 I  Starting process manager
2014-10-29 13:34:21.278317 I  Starting IO manager (read)
2014-10-29 13:34:21.278407 I  Starting process signal handler
2014-10-29 13:34:21.281856 I  Starting IO manager (write)
2014-10-29 13:34:21.348506 I  New Client:  (#1)
2014-10-29 13:34:21.348567 I  Added syslogging
2014-10-29 13:34:21.378983 I  ScreenSaverX11Private: XScreenSaver support enabled
2014-10-29 13:34:21.384613 I  ScreenSaverX11Private: DPMS is disabled.
2014-10-29 13:34:21.406051 N  Desktop video mode: 1920x1080 50.044 Hz
2014-10-29 13:34:21.507448 I  Listening on TCP 127.0.0.1:6547
2014-10-29 13:34:21.507527 I  Listening on TCP 192.168.1.4:6547
2014-10-29 13:34:21.513601 I  Listening on TCP [::1]:6547
2014-10-29 13:34:21.513779 I  Listening on TCP [fe80::ca60:ff:fe5a:f0df%eth1]:6547
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2014-10-29 13:34:22.275450 I  Loading en_gb translation for module mythfrontend
2014-10-29 13:34:22.285917 I  LIRC: Successfully initialized '/dev/lircd' using '/home/alectv/.mythtv/lircrc' config
2014-10-29 13:34:22.286094 E  JoystickMenuThread: Joystick disabled - Failed to read /home/alectv/.mythtv/joystickmenurc
2014-10-29 13:34:22.295180 E  CECAdapter: Failed to load libcec.
2014-10-29 13:34:22.295225 I  UDPListener: Enabling
2014-10-29 13:34:22.296094 I  Binding to UDP 127.0.0.1:6948
2014-10-29 13:34:22.296204 I  Binding to UDP 192.168.1.4:6948
2014-10-29 13:34:22.301187 I  Binding to UDP [::1]:6948
2014-10-29 13:34:22.301345 I  Binding to UDP [fe80::ca60:ff:fe5a:f0df%eth1]:6948
2014-10-29 13:34:22.301455 I  Binding to UDP 192.168.1.255:6948
2014-10-29 13:34:22.339914 I  Using Frameless Window
2014-10-29 13:34:22.339926 I  Using Full Screen Window
2014-10-29 13:34:22.478551 I  Using the Qt painter
2014-10-29 13:34:22.634944 I  MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2014-10-29 13:34:22.636601 I  MythUIWebBrowser: enabling plugins
2014-10-29 13:34:22.735837 I  MythCoreContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2014-10-29 13:34:22.737747 I  Using protocol version 77
2014-10-29 13:34:22.803873 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-10-29 13:34:23.568706 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2014-10-29 13:34:23.568734 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2014-10-29 13:34:23.570237 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2014-10-29 13:34:23.570254 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2014-10-29 13:34:23.767365 N  Registering Internal as a media playback plugin.
2014-10-29 13:34:23.840278 I  Loading en_gb translation for module mytharchive
2014-10-29 13:34:23.846067 N  Registering WebBrowser as a media playback plugin.
2014-10-29 13:34:23.846168 I  Loading en_gb translation for module mythbrowser
2014-10-29 13:34:23.870998 I  Loading en_gb translation for module mythgallery
2014-10-29 13:34:23.878118 I  Current MythMusic Schema Version (MusicDBSchemaVer): 1005
2014-10-29 13:34:23.893900 E  Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2014-10-29 13:34:40.309978 C  Database Backup complete.
2014-10-29 13:34:40.310757 C  Backed up database to file: '/media/store3/Backups/db_backups/mythconverg-1317-20141029133423.sql.gz'
2014-10-29 13:34:40.446707 I  Bonjour: Service registration complete: name 'Mythfrontend on alectv' type '_mythfrontend._tcp.' domain: 'local.'
2014-10-29 13:34:46.402320 N  Upgrading to MythMusic schema version 1006
2014-10-29 13:34:46.402783 E  DB Error (Performing database upgrade): 
Query was: CREATE TABLE music_albums (    album_id int(11) unsigned NOT NULL auto_increment PRIMARY KEY,    artist_id int(11) unsigned NOT NULL default '0',    album_name varchar(255) NOT NULL default '',    year smallint(6) NOT NULL default '0',    compilation tinyint(1) unsigned NOT NULL default '0',    INDEX idx_album_name(album_name)); 
Error was: Driver error was [2/1050]:
QMYSQL: Unable to execute query
Database error was:
Table 'music_albums' already exists
 
new version: 1006
2014-10-29 13:34:46.402813 E  Database schema upgrade failed.
2014-10-29 13:34:46.403126 E  Couldn't upgrade music database schema, exiting.
2014-10-29 13:34:46.403150 E  Unable to initialize plugin 'mythmusic'.
2014-10-29 13:34:46.405528 I  Listening on TCP 127.0.0.1:6546
2014-10-29 13:34:46.405632 I  Listening on TCP 192.168.1.4:6546
2014-10-29 13:34:46.410782 I  Listening on TCP [::1]:6546
2014-10-29 13:34:46.410976 I  Listening on TCP [fe80::ca60:ff:fe5a:f0df%eth1]:6546
2014-10-29 13:34:46.486596 N  Found mainmenu.xml for theme 'MythCenter-wide'
2014-10-29 13:34:46.489215 I  Registering HouseKeeperTask 'HardwareProfiler'.
2014-10-29 13:34:46.490172 I  Starting HouseKeeper.
2014-10-29 13:34:46.490306 N  Found a handler for MEDIATYPE_DATA - 'MythGallery Media Handler 1/2'
2014-10-29 13:34:56.414247 I  Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on alectv'
2014-10-29 13:34:56.414628 I  RAOP Device: Cleaning up.
2014-10-29 13:34:56.414677 I  AirPlay: Cleaning up.
2014-10-29 13:34:56.414713 I  Shutting down UPnP client...
2014-10-29 13:34:57.526914 I  Waiting for threads to exit.
2014-10-29 13:34:57.618204 I  Removing syslogging
```

anybody had this before?

---

### Post by tgm4883 on 2014-10-29
> **AlecJ said:**
> every time I start Mythfrontend I get 20sec's of white screen followed by:-
mythtv wants to upgrade your database for the music schema from 1005 to 1020, EXIT or UPGRADE
 I say UPGRADE
 it says
"If your system becomes unstable, a database backup file called
mythconverg-1317-20141029132158.sql.gz
is located in /media/store3/Backups/db_backups

There are other clients using this database. they should be shut down first. EXIT or UPGRADE
I say UPGRADE

I'm then presented with the normal menu, BUT minus the Music?

don't think the database is getting updated

I Google'ed but only found references to .22 where they deleted .ICEautherity so I tried that but had no effect

then I ran from a terminal with super user still not able to update

```
~$ sudo mythfrontend2014-10-29 13:34:21.233434 I  Setup Interrupt handler
2014-10-29 13:34:21.233458 I  Setup Terminated handler
2014-10-29 13:34:21.233466 I  Setup Segmentation fault handler
2014-10-29 13:34:21.233475 I  Setup Aborted handler
2014-10-29 13:34:21.233482 I  Setup Bus error handler
2014-10-29 13:34:21.233491 I  Setup Floating point exception handler
2014-10-29 13:34:21.233499 I  Setup Illegal instruction handler
2014-10-29 13:34:21.233509 I  Setup Real-time signal 0 handler
2014-10-29 13:34:21.233520 I  Setup User defined signal 1 handler
2014-10-29 13:34:21.233529 I  Setup User defined signal 2 handler
2014-10-29 13:34:21.233627 C  mythfrontend version: fixes/0.27 [v0.27.4-6-ge0b0027] www.mythtv.org
2014-10-29 13:34:21.233633 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-10-29 13:34:21.233637 N  Enabled verbose msgs:  general
2014-10-29 13:34:21.233649 N  Setting Log Level to LOG_INFO
2014-10-29 13:34:21.244966 N  Using runtime prefix = /usr
2014-10-29 13:34:21.245017 I  Added logging to the console
2014-10-29 13:34:21.245020 N  Using configuration directory = /home/alectv/.mythtv
2014-10-29 13:34:21.245172 I  Assumed character encoding: en_GB.UTF-8
2014-10-29 13:34:21.246097 N  Empty LocalHostName.
2014-10-29 13:34:21.246114 I  Using localhost value of alectv
2014-10-29 13:34:21.269624 N  Setting QT default locale to en_GB
2014-10-29 13:34:21.269748 I  Current locale en_GB
2014-10-29 13:34:21.269827 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2014-10-29 13:34:21.277982 I  Starting process manager
2014-10-29 13:34:21.278317 I  Starting IO manager (read)
2014-10-29 13:34:21.278407 I  Starting process signal handler
2014-10-29 13:34:21.281856 I  Starting IO manager (write)
2014-10-29 13:34:21.348506 I  New Client:  (#1)
2014-10-29 13:34:21.348567 I  Added syslogging
2014-10-29 13:34:21.378983 I  ScreenSaverX11Private: XScreenSaver support enabled
2014-10-29 13:34:21.384613 I  ScreenSaverX11Private: DPMS is disabled.
2014-10-29 13:34:21.406051 N  Desktop video mode: 1920x1080 50.044 Hz
2014-10-29 13:34:21.507448 I  Listening on TCP 127.0.0.1:6547
2014-10-29 13:34:21.507527 I  Listening on TCP 192.168.1.4:6547
2014-10-29 13:34:21.513601 I  Listening on TCP [::1]:6547
2014-10-29 13:34:21.513779 I  Listening on TCP [fe80::ca60:ff:fe5a:f0df%eth1]:6547
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2014-10-29 13:34:22.275450 I  Loading en_gb translation for module mythfrontend
2014-10-29 13:34:22.285917 I  LIRC: Successfully initialized '/dev/lircd' using '/home/alectv/.mythtv/lircrc' config
2014-10-29 13:34:22.286094 E  JoystickMenuThread: Joystick disabled - Failed to read /home/alectv/.mythtv/joystickmenurc
2014-10-29 13:34:22.295180 E  CECAdapter: Failed to load libcec.
2014-10-29 13:34:22.295225 I  UDPListener: Enabling
2014-10-29 13:34:22.296094 I  Binding to UDP 127.0.0.1:6948
2014-10-29 13:34:22.296204 I  Binding to UDP 192.168.1.4:6948
2014-10-29 13:34:22.301187 I  Binding to UDP [::1]:6948
2014-10-29 13:34:22.301345 I  Binding to UDP [fe80::ca60:ff:fe5a:f0df%eth1]:6948
2014-10-29 13:34:22.301455 I  Binding to UDP 192.168.1.255:6948
2014-10-29 13:34:22.339914 I  Using Frameless Window
2014-10-29 13:34:22.339926 I  Using Full Screen Window
2014-10-29 13:34:22.478551 I  Using the Qt painter
2014-10-29 13:34:22.634944 I  MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2014-10-29 13:34:22.636601 I  MythUIWebBrowser: enabling plugins
2014-10-29 13:34:22.735837 I  MythCoreContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2014-10-29 13:34:22.737747 I  Using protocol version 77
2014-10-29 13:34:22.803873 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-10-29 13:34:23.568706 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2014-10-29 13:34:23.568734 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2014-10-29 13:34:23.570237 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2014-10-29 13:34:23.570254 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2014-10-29 13:34:23.767365 N  Registering Internal as a media playback plugin.
2014-10-29 13:34:23.840278 I  Loading en_gb translation for module mytharchive
2014-10-29 13:34:23.846067 N  Registering WebBrowser as a media playback plugin.
2014-10-29 13:34:23.846168 I  Loading en_gb translation for module mythbrowser
2014-10-29 13:34:23.870998 I  Loading en_gb translation for module mythgallery
2014-10-29 13:34:23.878118 I  Current MythMusic Schema Version (MusicDBSchemaVer): 1005
2014-10-29 13:34:23.893900 E  Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2014-10-29 13:34:40.309978 C  Database Backup complete.
2014-10-29 13:34:40.310757 C  Backed up database to file: '/media/store3/Backups/db_backups/mythconverg-1317-20141029133423.sql.gz'
2014-10-29 13:34:40.446707 I  Bonjour: Service registration complete: name 'Mythfrontend on alectv' type '_mythfrontend._tcp.' domain: 'local.'
2014-10-29 13:34:46.402320 N  Upgrading to MythMusic schema version 1006
2014-10-29 13:34:46.402783 E  DB Error (Performing database upgrade): 
Query was: CREATE TABLE music_albums (    album_id int(11) unsigned NOT NULL auto_increment PRIMARY KEY,    artist_id int(11) unsigned NOT NULL default '0',    album_name varchar(255) NOT NULL default '',    year smallint(6) NOT NULL default '0',    compilation tinyint(1) unsigned NOT NULL default '0',    INDEX idx_album_name(album_name)); 
Error was: Driver error was [2/1050]:
QMYSQL: Unable to execute query
Database error was:
Table 'music_albums' already exists
 
new version: 1006
2014-10-29 13:34:46.402813 E  Database schema upgrade failed.
2014-10-29 13:34:46.403126 E  Couldn't upgrade music database schema, exiting.
2014-10-29 13:34:46.403150 E  Unable to initialize plugin 'mythmusic'.
2014-10-29 13:34:46.405528 I  Listening on TCP 127.0.0.1:6546
2014-10-29 13:34:46.405632 I  Listening on TCP 192.168.1.4:6546
2014-10-29 13:34:46.410782 I  Listening on TCP [::1]:6546
2014-10-29 13:34:46.410976 I  Listening on TCP [fe80::ca60:ff:fe5a:f0df%eth1]:6546
2014-10-29 13:34:46.486596 N  Found mainmenu.xml for theme 'MythCenter-wide'
2014-10-29 13:34:46.489215 I  Registering HouseKeeperTask 'HardwareProfiler'.
2014-10-29 13:34:46.490172 I  Starting HouseKeeper.
2014-10-29 13:34:46.490306 N  Found a handler for MEDIATYPE_DATA - 'MythGallery Media Handler 1/2'
2014-10-29 13:34:56.414247 I  Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on alectv'
2014-10-29 13:34:56.414628 I  RAOP Device: Cleaning up.
2014-10-29 13:34:56.414677 I  AirPlay: Cleaning up.
2014-10-29 13:34:56.414713 I  Shutting down UPnP client...
2014-10-29 13:34:57.526914 I  Waiting for threads to exit.
2014-10-29 13:34:57.618204 I  Removing syslogging
```

anybody had this before?

Your schema update failed. The recommended solution would be to restore your DB from backup and try again. Alternatively you could attempt to fix the errors on the DB, but it's unknown if you will run into other problems.


As for the 20 seconds of whitespace, it sounds like you aren't on the latest version of the Mythbuntu theme. If you aren't using the Mythbuntu theme then disregard this statement.

---

### Post by AlecJ on 2014-10-29
I have many backups to choose from, what happens to the recordings made after the backup was made?
this music problem has been an issue for a good few months, ending up un-installing it.
I had loads of problems after kernel updates losing remote and sound and video, had to keep going back to 3.2.??.61 
this last update to .70 is the only one that's worked.

This is 12.04Lts 64bit with an Nvidia graphics card GT520 i think.

I just reinstalled Music in the hope all was fixed now,

How about deleting just the music related parts in the database? how would I do that?

---

### Post by AlecJ on 2014-10-30
Fixed it!
this is how, BUT there are Dragons so backup the database first.

help from these threads and places:-
[http://ubuntuforums.org/showthread.php?t=2188021&highlight=edit+mythconverg](http://ubuntuforums.org/showthread.php?t=2188021&highlight=edit+mythconverg)
[http://www.gossamer-threads.com/lists/mythtv/users/407460](http://www.gossamer-threads.com/lists/mythtv/users/407460)
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)
[https://www.mythtv.org/wiki/Category:MySQL](https://www.mythtv.org/wiki/Category:MySQL)

1) shutdown backend
```
sudo stop mythtv-backend
```

2) log in mysql

```
[COLOR=#000000][FONT=Ubuntu Mono]mysql -u mythtv -p[/FONT][/COLOR]
```

you need password, so in another terminal

```
grep DBPassword /etc/mythtv/config.xml
```

cut and paste the password into the prompt and enter or type it you not as lazy

should give the

```
mysql>
```

prompt, if not you not in.

3) now your in you have to select the database, I found I could do this with (there maybe other ways but I'm very new to this area)

```
use mythconverg
```

then I cut and paste each line, one at a time 

```
[COLOR=#660066][FONT=Verdana]UPDATE `settings` SET `data` = '' WHERE `value` = 'MusicDBSchemaVer'; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS musicmetadata; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS musicplaylist; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_albumart; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_albums; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_artists; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_directories; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_genres; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_playlists; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_smartplaylists; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_smartplaylist_categories; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_smartplaylist_items; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_songs; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS music_stats; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS smartplaylistcategory; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS smartplaylist; [/FONT][/COLOR]
[COLOR=#660066][FONT=Verdana]DROP TABLE IF EXISTS smartplaylistitem; [/FONT][/COLOR]

```

4) exit mysql
```
exit
```

5) restart backend

```
sudo start mythtv-backend
```

6) start Frontend and enter Music and do a "scan for new music" to rebuild the datatbase.

I have 38,000ish mp3's so this take's about 40min's or so. 

I will do a new backup of the database after and delete all the old

---

