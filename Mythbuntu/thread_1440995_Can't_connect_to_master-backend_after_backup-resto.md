---
title: "Can't connect to master-backend after backup-restore"
date: 2010-03-28
forum: Mythbuntu
---

### Post by Stevi on 2010-03-28
Hi,
today I installed Mythbuntu 10.04 beta and tried to restore my database backup. At least I have been able to restore everything but when I start mythfrontend I get:

*Could not connect to the master-backend. Is it running?*

Here's what I did ([Mythtv Wiki]("http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore")):
```

myth@myth-desktop:~$ mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'
Enter password: 
myth@myth-desktop:~$ cd /usr/share/mythtv/sql
myth@myth-desktop:/usr/share/mythtv/sql$ mysql -uroot -p1234 < mc.sql
myth@myth-desktop:/usr/share/mythtv/sql$ cd
myth@myth-desktop:~$ cd /home/mythalt
myth@myth-desktop:/home/mythalt$ mysql -uroot -p1234 mysqlReading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 51
Server version: 5.1.41-3ubuntu9 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> UPDATE mysql.user SET Password=PASSWORD('passfrommysql.txtAA') WHERE User='mythtv'; FLUSH PRIVILEGES;
Query OK, 2 rows affected (0.00 sec)
Rows matched: 2  Changed: 2  Warnings: 0

Query OK, 0 rows affected (0.00 sec)

mysql> exit
Bye
myth@myth-desktop:/home/mythalt$ ./mythconverg_restore.pl --directory /home/mythalt --filename mythconverg-1254-20100327182627.sql.gz --verbose

Configuring environment:
  -    username: myth
  -        HOME: /home/myth
  - MYTHCONFDIR: /home/myth/.mythtv

Parsing configuration files:
  - checking: /home/myth/.mythtv/config.xml
     parsing: /home/myth/.mythtv/config.xml
  - checking: /home/myth/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

Database Information:
         DBHostName: localhost
             DBPort: 0
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: /home/mythalt
   DBBackupFilename: mythconverg-1254-20100327182627.sql.gz
    create_database: 

Executables:
       mysql_client: mysql
         uncompress: gzip -d

Miscellaneous:
    partial_restore: no
   restore_xmltvids: no
    change_hostname: no

Checking database.

Found 0 tables in the database.

Backup file is compressed.
 - Uncompressing backup file with IO::Uncompress::Gunzip.

Attempting to use supplied password for mysql command-line client.
Any [client] or [mysql] password specified in the MySQL options file will
take precedence.

Executing command:
'mysql' --defaults-extra-file='/tmp/e9kp8aLkb_' --host='localhost' --user='mythtv' 'mythconverg'

mysql exited with status: 0

Restored 3175 of 3175 lines.

Successfully restored backup.


myth@myth-desktop:/home/mythalt$ mythfrontend
2010-03-28 14:02:46.643 mythfrontend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 14:02:46.644 Using runtime prefix = /usr
2010-03-28 14:02:46.644 Using configuration directory = /home/myth/.mythtv
2010-03-28 14:02:47.337 Empty LocalHostName.
2010-03-28 14:02:47.338 Using localhost value of myth-desktop
2010-03-28 14:02:47.349 New DB connection, total: 1
2010-03-28 14:02:47.356 Connected to database 'mythconverg' at host: localhost
2010-03-28 14:02:47.357 Closing DB connection named 'DBManager0'
2010-03-28 14:02:47.393 ScreenSaverX11Private: XScreenSaver support enabled
2010-03-28 14:02:47.395 DPMS is disabled.
2010-03-28 14:02:47.398 Primary screen: 0.
2010-03-28 14:02:47.399 Connected to database 'mythconverg' at host: localhost
2010-03-28 14:02:47.407 Using screen 0, 1920x1080 at 0,0
2010-03-28 14:02:47.448 Desktop video mode: 1920x1080 50 Hz
2010-03-28 14:02:48.078 MythUI Image Cache size set to 20971520 bytes
2010-03-28 14:02:48.116 Enabled verbose msgs:  important general
2010-03-28 14:02:48.128 Primary screen: 0.
2010-03-28 14:02:48.129 Using screen 0, 1920x1080 at 0,0
2010-03-28 14:02:48.131 Using theme base resolution of 1280x720
2010-03-28 14:02:48.160 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2010-03-28 14:02:48.160 JoystickMenuThread Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2010-03-28 14:02:48.260 Using Frameless Window
2010-03-28 14:02:48.260 Using Full Screen Window
2010-03-28 14:02:48.271 Using the Qt painter
2010-03-28 14:02:48.330 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 5
			Name: 'basesmall'	Type: 'font'
2010-03-28 14:02:48.339 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 10
			Name: 'basemedium'	Type: 'font'
2010-03-28 14:02:48.348 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 14
			Name: 'baselarge'	Type: 'font'
2010-03-28 14:02:48.358 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 18
			Name: 'baseextralarge'	Type: 'font'
2010-03-28 14:02:48.358 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 27
			Name: 'basesmallbrown'	Type: 'font'
2010-03-28 14:02:48.358 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 33
			Name: 'basesmallgrey'	Type: 'font'
2010-03-28 14:02:48.359 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 37
			Name: 'basesmallpurple'	Type: 'font'
2010-03-28 14:02:48.359 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 41
			Name: 'basesmallblack'	Type: 'font'
2010-03-28 14:02:48.359 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 45
			Name: 'basesmallyellow'	Type: 'font'
2010-03-28 14:02:48.359 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 49
			Name: 'basesmallgreen'	Type: 'font'
2010-03-28 14:02:48.360 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 53
			Name: 'basesmallblue'	Type: 'font'
2010-03-28 14:02:48.360 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 57
			Name: 'basesmallred'	Type: 'font'
2010-03-28 14:02:48.360 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 61
			Name: 'basemediumgrey'	Type: 'font'
2010-03-28 14:02:48.360 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 65
			Name: 'basemediumgreen'	Type: 'font'
2010-03-28 14:02:48.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 69
			Name: 'basemediumred'	Type: 'font'
2010-03-28 14:02:48.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 73
			Name: 'basemediumpurple'	Type: 'font'
2010-03-28 14:02:48.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 77
			Name: 'basemediumbrown'	Type: 'font'
2010-03-28 14:02:48.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 83
			Name: 'baselargebrown'	Type: 'font'
2010-03-28 14:02:48.438 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 479
			Name: 'datefont'	Type: 'font'
2010-03-28 14:02:48.447 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/Terra/base.xml @ 483
			Name: 'timefont'	Type: 'font'
2010-03-28 14:02:48.600 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Terra/base.xml'
2010-03-28 14:02:48.653 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-03-28 14:02:48.661 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/default/base.xml @ 71
			Name: 'basemediumyellow'	Type: 'font'
2010-03-28 14:02:48.663 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-03-28 14:02:51.650 Current MythTV Schema Version (DBSchemaVer): 1254
2010-03-28 14:02:51.652 New DB connection, total: 2
2010-03-28 14:02:51.653 Connected to database 'mythconverg' at host: localhost
2010-03-28 14:02:52.744 Registering Internal as a media playback plugin.
2010-03-28 14:02:52.828 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.835 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.841 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.851 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.856 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.860 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.876 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.883 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.887 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-28 14:02:52.892 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-03-28 14:02:52.897 Setting Up MythMovies Database Tables
2010-03-28 14:02:53.089 MythMovies Database Setup Complete
2010-03-28 14:02:53.089 Cannot load language de for module mythmovies
2010-03-28 14:02:53.117 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-03-28 14:02:53.250 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-03-28 14:02:53.273 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-28 14:02:53.273 MythVideo database schema is old. Waiting to see if DB is being upgraded.
2010-03-28 14:02:54.278 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-28 14:02:55.281 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-28 14:02:56.285 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-28 14:02:56.285 Timed out waiting.
2010-03-28 14:02:56.305 SG(Default) Error: FindNextDirMostFree: '/home/myth/aufnahmen' does not exist!
2010-03-28 14:02:56.308 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2010-03-28 14:03:05.260 Database Backup complete.
2010-03-28 14:03:05.261 Backed up database to file: '/tmp/mythconverg-1254-20100328140256.sql.gz'
2010-03-28 14:03:09.009 Couldn't upgrade video database schema, exiting.
2010-03-28 14:03:09.009 Unable to initialize plugin 'mythvideo'.
2010-03-28 14:03:09.030 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Terra/menu-ui.xml
2010-03-28 14:03:09.218 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-03-28 14:03:09.220 Found mainmenu.xml for theme 'Terra'
2010-03-28 14:03:09.558 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:09.560 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:12.760 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-03-28 14:03:14.437 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-03-28 14:03:14.814 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:14.814 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:19.822 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:19.822 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:24.834 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:24.835 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:29.839 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:29.840 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:31.788 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:31.789 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:31.794 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:31.795 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:34.564 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:34.565 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:34.988 MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
2010-03-28 14:03:34.989 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-03-28 14:03:36.645 Deleting UPnP client...

```

etc/mythtv/mysql.txt new
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=passfrommysql.txtAA
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```
etc/mythtv/mysql.txt old
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=mythtv
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
DBPassword=passfrommysql.txtBBB
```

database configuration in mythfrontend
```
name: mythconverg
user: mythtv
password: passfrommysql.txtAAA
```

I'm logging into Mythbuntu as user myth. User myth is member of the group mythtv.

When I start mythfrontend I'm asked to update my database from 1028 to 1032. It makes no difference if I update or not. I always get the error message:*Could not connect to the master-backend. Is it running?*

Any ideas? Thx in advance.


edit: Some more information from var/log/mythtv/mythbackendlog:
```
2010-03-28 16:23:32.158 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:32.203 Using runtime prefix = /usr
2010-03-28 16:23:32.207 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:32.502 Empty LocalHostName.
2010-03-28 16:23:32.534 Using localhost value of myth-desktop
2010-03-28 16:23:32.653 New DB connection, total: 1
2010-03-28 16:23:32.724 Unable to connect to database!
2010-03-28 16:23:32.768 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-03-28 16:23:32.796 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:23:32.799 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
2010-03-28 16:23:32.907 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
................................................................................
2010-03-28 16:23:34.990 UPnPautoconf() - No UPnP backends found
2010-03-28 16:23:35.049 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:23:35.165 Deleting UPnP client...
2010-03-28 16:23:35.174 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:23:35.838 Failed to init MythContext, exiting.
2010-03-28 16:23:36.054 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:36.074 Using runtime prefix = /usr
2010-03-28 16:23:36.124 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:36.166 Empty LocalHostName.
2010-03-28 16:23:36.174 Using localhost value of myth-desktop
2010-03-28 16:23:36.199 New DB connection, total: 1
2010-03-28 16:23:36.219 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:36.265 Closing DB connection named 'DBManager0'
2010-03-28 16:23:36.299 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:36.315 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:36.468 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:36.469 Using runtime prefix = /usr
2010-03-28 16:23:36.474 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:36.482 Empty LocalHostName.
2010-03-28 16:23:36.490 Using localhost value of myth-desktop
2010-03-28 16:23:36.504 New DB connection, total: 1
2010-03-28 16:23:36.510 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:36.515 Closing DB connection named 'DBManager0'
2010-03-28 16:23:36.524 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:36.536 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:36.626 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:36.627 Using runtime prefix = /usr
2010-03-28 16:23:36.632 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:36.641 Empty LocalHostName.
2010-03-28 16:23:36.648 Using localhost value of myth-desktop
2010-03-28 16:23:36.662 New DB connection, total: 1
2010-03-28 16:23:36.668 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:36.674 Closing DB connection named 'DBManager0'
2010-03-28 16:23:36.682 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:36.695 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:36.788 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:36.793 Using runtime prefix = /usr
2010-03-28 16:23:36.815 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:37.080 Empty LocalHostName.
2010-03-28 16:23:37.125 Using localhost value of myth-desktop
2010-03-28 16:23:37.212 New DB connection, total: 1
2010-03-28 16:23:37.232 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:37.254 Closing DB connection named 'DBManager0'
2010-03-28 16:23:37.263 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:37.275 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:37.386 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:37.393 Using runtime prefix = /usr
2010-03-28 16:23:37.395 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:37.404 Empty LocalHostName.
2010-03-28 16:23:37.412 Using localhost value of myth-desktop
2010-03-28 16:23:37.432 New DB connection, total: 1
2010-03-28 16:23:37.440 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:37.445 Closing DB connection named 'DBManager0'
2010-03-28 16:23:37.454 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:37.467 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:37.608 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:37.622 Using runtime prefix = /usr
2010-03-28 16:23:37.637 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:37.662 Empty LocalHostName.
2010-03-28 16:23:37.670 Using localhost value of myth-desktop
2010-03-28 16:23:37.688 New DB connection, total: 1
2010-03-28 16:23:37.702 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:37.704 Closing DB connection named 'DBManager0'
2010-03-28 16:23:37.713 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:37.726 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:37.804 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:37.804 Using runtime prefix = /usr
2010-03-28 16:23:37.812 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:37.929 Empty LocalHostName.
2010-03-28 16:23:38.054 Using localhost value of myth-desktop
2010-03-28 16:23:38.068 New DB connection, total: 1
2010-03-28 16:23:38.076 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.079 Closing DB connection named 'DBManager0'
2010-03-28 16:23:38.087 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.100 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:38.178 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:38.178 Using runtime prefix = /usr
2010-03-28 16:23:38.187 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:38.196 Empty LocalHostName.
2010-03-28 16:23:38.203 Using localhost value of myth-desktop
2010-03-28 16:23:38.220 New DB connection, total: 1
2010-03-28 16:23:38.232 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.237 Closing DB connection named 'DBManager0'
2010-03-28 16:23:38.246 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.258 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:38.419 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:38.423 Using runtime prefix = /usr
2010-03-28 16:23:38.437 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:38.483 Empty LocalHostName.
2010-03-28 16:23:38.495 Using localhost value of myth-desktop
2010-03-28 16:23:38.514 New DB connection, total: 1
2010-03-28 16:23:38.524 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.529 Closing DB connection named 'DBManager0'
2010-03-28 16:23:38.538 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.550 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:23:38.642 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:23:38.643 Using runtime prefix = /usr
2010-03-28 16:23:38.645 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:23:38.654 Empty LocalHostName.
2010-03-28 16:23:38.662 Using localhost value of myth-desktop
2010-03-28 16:23:38.681 New DB connection, total: 1
2010-03-28 16:23:38.724 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.729 Closing DB connection named 'DBManager0'
2010-03-28 16:23:38.738 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:23:38.750 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:29:09.977 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:10.038 Using runtime prefix = /usr
2010-03-28 16:29:10.131 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:10.261 Unable to read configuration file mysql.txt
2010-03-28 16:29:10.306 Empty LocalHostName.
2010-03-28 16:29:10.414 Using localhost value of myth-desktop
2010-03-28 16:29:10.598 New DB connection, total: 1
2010-03-28 16:29:10.653 Unable to connect to database!
2010-03-28 16:29:10.681 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-03-28 16:29:10.718 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:29:10.781 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
..2010-03-28 16:29:10.918 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
............................................................................
2010-03-28 16:29:12.903 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:12.922 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:12.972 Deleting UPnP client...
2010-03-28 16:29:12.980 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:29:13.878 Failed to init MythContext, exiting.
2010-03-28 16:29:14.121 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:14.134 Using runtime prefix = /usr
2010-03-28 16:29:14.180 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:14.222 Unable to read configuration file mysql.txt
2010-03-28 16:29:14.272 Empty LocalHostName.
2010-03-28 16:29:14.280 Using localhost value of myth-desktop
2010-03-28 16:29:14.294 New DB connection, total: 1
2010-03-28 16:29:14.300 Unable to connect to database!
2010-03-28 16:29:14.305 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2010-03-28 16:29:14.315 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:29:14.322 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.2010-03-28 16:29:14.415 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

................................................................................
2010-03-28 16:29:16.448 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:16.638 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:16.805 Deleting UPnP client...
2010-03-28 16:29:17.334 Failed to init MythContext, exiting.
2010-03-28 16:29:17.387 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:17.388 Using runtime prefix = /usr
2010-03-28 16:29:17.396 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:17.405 Unable to read configuration file mysql.txt
2010-03-28 16:29:17.413 Empty LocalHostName.
2010-03-28 16:29:17.421 Using localhost value of myth-desktop
2010-03-28 16:29:17.435 New DB connection, total: 1
2010-03-28 16:29:17.441 Unable to connect to database!
2010-03-28 16:29:17.446 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:20.017 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:20.028 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:20.078 Deleting UPnP client...
2010-03-28 16:29:20.725 Failed to init MythContext, exiting.
2010-03-28 16:29:20.775 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:20.775 Using runtime prefix = /usr
2010-03-28 16:29:20.778 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:20.786 Unable to read configuration file mysql.txt
2010-03-28 16:29:20.794 Empty LocalHostName.
2010-03-28 16:29:20.803 Using localhost value of myth-desktop
2010-03-28 16:29:20.817 New DB connection, total: 1
2010-03-28 16:29:20.822 Unable to connect to database!
2010-03-28 16:29:20.828 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:23.506 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:23.518 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:23.568 Deleting UPnP client...
2010-03-28 16:29:24.206 Failed to init MythContext, exiting.
2010-03-28 16:29:24.255 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:24.256 Using runtime prefix = /usr
2010-03-28 16:29:24.259 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:24.267 Unable to read configuration file mysql.txt
2010-03-28 16:29:24.275 Empty LocalHostName.
2010-03-28 16:29:24.284 Using localhost value of myth-desktop
2010-03-28 16:29:24.298 New DB connection, total: 1
2010-03-28 16:29:24.303 Unable to connect to database!
2010-03-28 16:29:24.309 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:26.988 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:26.999 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:27.049 Deleting UPnP client...
2010-03-28 16:29:28.687 Failed to init MythContext, exiting.
2010-03-28 16:29:28.745 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:28.745 Using runtime prefix = /usr
2010-03-28 16:29:28.748 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:28.756 Unable to read configuration file mysql.txt
2010-03-28 16:29:28.764 Empty LocalHostName.
2010-03-28 16:29:28.773 Using localhost value of myth-desktop
2010-03-28 16:29:28.804 New DB connection, total: 1
2010-03-28 16:29:28.817 Unable to connect to database!
2010-03-28 16:29:28.823 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:31.501 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:31.529 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:31.579 Deleting UPnP client...
2010-03-28 16:29:33.201 Failed to init MythContext, exiting.
2010-03-28 16:29:33.258 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:33.259 Using runtime prefix = /usr
2010-03-28 16:29:33.262 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:33.270 Unable to read configuration file mysql.txt
2010-03-28 16:29:33.278 Empty LocalHostName.
2010-03-28 16:29:33.287 Using localhost value of myth-desktop
2010-03-28 16:29:33.301 New DB connection, total: 1
2010-03-28 16:29:33.306 Unable to connect to database!
2010-03-28 16:29:33.312 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:35.990 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:36.002 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:36.052 Deleting UPnP client...
2010-03-28 16:29:37.690 Failed to init MythContext, exiting.
2010-03-28 16:29:37.747 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:37.748 Using runtime prefix = /usr
2010-03-28 16:29:37.751 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:37.759 Unable to read configuration file mysql.txt
2010-03-28 16:29:37.767 Empty LocalHostName.
2010-03-28 16:29:37.775 Using localhost value of myth-desktop
2010-03-28 16:29:37.790 New DB connection, total: 1
2010-03-28 16:29:37.795 Unable to connect to database!
2010-03-28 16:29:37.800 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:40.479 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:40.490 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:40.540 Deleting UPnP client...
2010-03-28 16:29:42.179 Failed to init MythContext, exiting.
2010-03-28 16:29:42.236 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:42.236 Using runtime prefix = /usr
2010-03-28 16:29:42.239 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:42.248 Unable to read configuration file mysql.txt
2010-03-28 16:29:42.256 Empty LocalHostName.
2010-03-28 16:29:42.264 Using localhost value of myth-desktop
2010-03-28 16:29:42.279 New DB connection, total: 1
2010-03-28 16:29:42.351 Unable to connect to database!
2010-03-28 16:29:42.356 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:45.034 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:45.064 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:45.121 Deleting UPnP client...
2010-03-28 16:29:46.734 Failed to init MythContext, exiting.
2010-03-28 16:29:46.791 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:46.792 Using runtime prefix = /usr
2010-03-28 16:29:46.825 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:46.837 Unable to read configuration file mysql.txt
2010-03-28 16:29:46.845 Empty LocalHostName.
2010-03-28 16:29:46.853 Using localhost value of myth-desktop
2010-03-28 16:29:46.867 New DB connection, total: 1
2010-03-28 16:29:46.873 Unable to connect to database!
2010-03-28 16:29:46.878 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:49.556 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:49.585 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:49.635 Deleting UPnP client...
2010-03-28 16:29:51.257 Failed to init MythContext, exiting.
2010-03-28 16:29:51.313 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:51.314 Using runtime prefix = /usr
2010-03-28 16:29:51.317 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:51.326 Unable to read configuration file mysql.txt
2010-03-28 16:29:51.334 Empty LocalHostName.
2010-03-28 16:29:51.342 Using localhost value of myth-desktop
2010-03-28 16:29:51.356 New DB connection, total: 1
2010-03-28 16:29:51.362 Unable to connect to database!
2010-03-28 16:29:51.367 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:54.045 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:54.057 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:54.107 Deleting UPnP client...
2010-03-28 16:29:55.746 Failed to init MythContext, exiting.
2010-03-28 16:29:55.811 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:29:55.812 Using runtime prefix = /usr
2010-03-28 16:29:55.814 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:29:55.823 Unable to read configuration file mysql.txt
2010-03-28 16:29:55.831 Empty LocalHostName.
2010-03-28 16:29:55.839 Using localhost value of myth-desktop
2010-03-28 16:29:55.854 New DB connection, total: 1
2010-03-28 16:29:55.859 Unable to connect to database!
2010-03-28 16:29:55.864 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:29:58.542 UPnPautoconf() - No UPnP backends found
2010-03-28 16:29:58.554 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:29:58.604 Deleting UPnP client...
2010-03-28 16:30:00.243 Failed to init MythContext, exiting.
2010-03-28 16:30:00.301 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:00.301 Using runtime prefix = /usr
2010-03-28 16:30:00.303 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:00.312 Unable to read configuration file mysql.txt
2010-03-28 16:30:00.320 Empty LocalHostName.
2010-03-28 16:30:00.328 Using localhost value of myth-desktop
2010-03-28 16:30:00.342 New DB connection, total: 1
2010-03-28 16:30:00.348 Unable to connect to database!
2010-03-28 16:30:00.353 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:03.032 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:03.043 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:03.110 Deleting UPnP client...
2010-03-28 16:30:04.732 Failed to init MythContext, exiting.
2010-03-28 16:30:04.789 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:04.789 Using runtime prefix = /usr
2010-03-28 16:30:04.792 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:04.801 Unable to read configuration file mysql.txt
2010-03-28 16:30:04.809 Empty LocalHostName.
2010-03-28 16:30:04.817 Using localhost value of myth-desktop
2010-03-28 16:30:04.831 New DB connection, total: 1
2010-03-28 16:30:04.837 Unable to connect to database!
2010-03-28 16:30:04.842 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:07.520 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:07.532 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:07.582 Deleting UPnP client...
2010-03-28 16:30:09.221 Failed to init MythContext, exiting.
2010-03-28 16:30:09.277 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:09.278 Using runtime prefix = /usr
2010-03-28 16:30:09.281 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:09.290 Unable to read configuration file mysql.txt
2010-03-28 16:30:09.298 Empty LocalHostName.
2010-03-28 16:30:09.306 Using localhost value of myth-desktop
2010-03-28 16:30:09.320 New DB connection, total: 1
2010-03-28 16:30:09.326 Unable to connect to database!
2010-03-28 16:30:09.331 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:12.010 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:12.021 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:12.071 Deleting UPnP client...
2010-03-28 16:30:12.709 Failed to init MythContext, exiting.
2010-03-28 16:30:12.806 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:12.807 Using runtime prefix = /usr
2010-03-28 16:30:12.812 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:12.821 Unable to read configuration file mysql.txt
2010-03-28 16:30:12.829 Empty LocalHostName.
2010-03-28 16:30:12.837 Using localhost value of myth-desktop
2010-03-28 16:30:12.857 New DB connection, total: 1
2010-03-28 16:30:12.868 Unable to connect to database!
2010-03-28 16:30:12.871 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:15.553 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:15.586 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:15.636 Deleting UPnP client...
2010-03-28 16:30:17.251 Failed to init MythContext, exiting.
2010-03-28 16:30:17.362 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:17.363 Using runtime prefix = /usr
2010-03-28 16:30:17.368 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:17.376 Unable to read configuration file mysql.txt
2010-03-28 16:30:17.385 Empty LocalHostName.
2010-03-28 16:30:17.393 Using localhost value of myth-desktop
2010-03-28 16:30:17.413 New DB connection, total: 1
2010-03-28 16:30:17.424 Unable to connect to database!
2010-03-28 16:30:17.468 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:20.150 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:20.166 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:20.216 Deleting UPnP client...
2010-03-28 16:30:21.848 Failed to init MythContext, exiting.
2010-03-28 16:30:21.958 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:21.960 Using runtime prefix = /usr
2010-03-28 16:30:21.965 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:21.974 Unable to read configuration file mysql.txt
2010-03-28 16:30:21.982 Empty LocalHostName.
2010-03-28 16:30:21.990 Using localhost value of myth-desktop
2010-03-28 16:30:22.011 New DB connection, total: 1
2010-03-28 16:30:22.021 Unable to connect to database!
2010-03-28 16:30:22.023 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:24.594 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:24.605 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:24.655 Deleting UPnP client...
2010-03-28 16:30:26.304 Failed to init MythContext, exiting.
2010-03-28 16:30:26.415 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:26.417 Using runtime prefix = /usr
2010-03-28 16:30:26.421 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:26.429 Unable to read configuration file mysql.txt
2010-03-28 16:30:26.437 Empty LocalHostName.
2010-03-28 16:30:26.446 Using localhost value of myth-desktop
2010-03-28 16:30:26.466 New DB connection, total: 1
2010-03-28 16:30:26.477 Unable to connect to database!
2010-03-28 16:30:26.479 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:29.161 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:29.177 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:29.227 Deleting UPnP client...
2010-03-28 16:30:30.859 Failed to init MythContext, exiting.
2010-03-28 16:30:30.961 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:30.963 Using runtime prefix = /usr
2010-03-28 16:30:30.968 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:30.977 Unable to read configuration file mysql.txt
2010-03-28 16:30:30.985 Empty LocalHostName.
2010-03-28 16:30:30.993 Using localhost value of myth-desktop
2010-03-28 16:30:31.014 New DB connection, total: 1
2010-03-28 16:30:31.024 Unable to connect to database!
2010-03-28 16:30:31.026 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:33.708 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:33.724 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:33.774 Deleting UPnP client...
2010-03-28 16:30:35.407 Failed to init MythContext, exiting.
2010-03-28 16:30:35.518 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:35.520 Using runtime prefix = /usr
2010-03-28 16:30:35.566 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:35.574 Unable to read configuration file mysql.txt
2010-03-28 16:30:35.582 Empty LocalHostName.
2010-03-28 16:30:35.590 Using localhost value of myth-desktop
2010-03-28 16:30:35.610 New DB connection, total: 1
2010-03-28 16:30:35.621 Unable to connect to database!
2010-03-28 16:30:35.623 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:38.306 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:38.322 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:38.372 Deleting UPnP client...
2010-03-28 16:30:40.004 Failed to init MythContext, exiting.
2010-03-28 16:30:40.115 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:40.116 Using runtime prefix = /usr
2010-03-28 16:30:40.121 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:40.129 Unable to read configuration file mysql.txt
2010-03-28 16:30:40.137 Empty LocalHostName.
2010-03-28 16:30:40.146 Using localhost value of myth-desktop
2010-03-28 16:30:40.165 New DB connection, total: 1
2010-03-28 16:30:40.177 Unable to connect to database!
2010-03-28 16:30:40.179 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:42.749 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:42.761 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:42.811 Deleting UPnP client...
2010-03-28 16:30:44.459 Failed to init MythContext, exiting.
2010-03-28 16:30:44.571 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:44.572 Using runtime prefix = /usr
2010-03-28 16:30:44.576 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:44.585 Unable to read configuration file mysql.txt
2010-03-28 16:30:44.593 Empty LocalHostName.
2010-03-28 16:30:44.601 Using localhost value of myth-desktop
2010-03-28 16:30:44.621 New DB connection, total: 1
2010-03-28 16:30:44.632 Unable to connect to database!
2010-03-28 16:30:44.634 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:47.317 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:47.324 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:47.374 Deleting UPnP client...
2010-03-28 16:30:49.015 Failed to init MythContext, exiting.
2010-03-28 16:30:49.125 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:49.127 Using runtime prefix = /usr
2010-03-28 16:30:49.132 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:49.140 Unable to read configuration file mysql.txt
2010-03-28 16:30:49.148 Empty LocalHostName.
2010-03-28 16:30:49.157 Using localhost value of myth-desktop
2010-03-28 16:30:49.177 New DB connection, total: 1
2010-03-28 16:30:49.188 Unable to connect to database!
2010-03-28 16:30:49.190 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:51.872 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:51.888 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:51.972 Deleting UPnP client...
2010-03-28 16:30:53.571 Failed to init MythContext, exiting.
2010-03-28 16:30:53.682 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:53.684 Using runtime prefix = /usr
2010-03-28 16:30:53.687 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:53.696 Unable to read configuration file mysql.txt
2010-03-28 16:30:53.704 Empty LocalHostName.
2010-03-28 16:30:53.712 Using localhost value of myth-desktop
2010-03-28 16:30:53.732 New DB connection, total: 1
2010-03-28 16:30:53.743 Unable to connect to database!
2010-03-28 16:30:53.746 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:30:56.428 UPnPautoconf() - No UPnP backends found
2010-03-28 16:30:56.444 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:30:56.494 Deleting UPnP client...
2010-03-28 16:30:58.126 Failed to init MythContext, exiting.
2010-03-28 16:30:58.231 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:30:58.232 Using runtime prefix = /usr
2010-03-28 16:30:58.234 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:30:58.243 Unable to read configuration file mysql.txt
2010-03-28 16:30:58.251 Empty LocalHostName.
2010-03-28 16:30:58.259 Using localhost value of myth-desktop
2010-03-28 16:30:58.279 New DB connection, total: 1
2010-03-28 16:30:58.291 Unable to connect to database!
2010-03-28 16:30:58.293 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:00.975 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:00.991 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:01.041 Deleting UPnP client...
2010-03-28 16:31:02.673 Failed to init MythContext, exiting.
2010-03-28 16:31:02.785 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:02.786 Using runtime prefix = /usr
2010-03-28 16:31:02.790 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:02.799 Unable to read configuration file mysql.txt
2010-03-28 16:31:02.807 Empty LocalHostName.
2010-03-28 16:31:02.815 Using localhost value of myth-desktop
2010-03-28 16:31:02.835 New DB connection, total: 1
2010-03-28 16:31:02.846 Unable to connect to database!
2010-03-28 16:31:02.848 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:05.530 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:05.547 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:05.597 Deleting UPnP client...
2010-03-28 16:31:07.229 Failed to init MythContext, exiting.
2010-03-28 16:31:07.340 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:07.342 Using runtime prefix = /usr
2010-03-28 16:31:07.345 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:07.354 Unable to read configuration file mysql.txt
2010-03-28 16:31:07.362 Empty LocalHostName.
2010-03-28 16:31:07.370 Using localhost value of myth-desktop
2010-03-28 16:31:07.390 New DB connection, total: 1
2010-03-28 16:31:07.402 Unable to connect to database!
2010-03-28 16:31:07.404 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:10.117 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:10.127 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:10.177 Deleting UPnP client...
2010-03-28 16:31:11.815 Failed to init MythContext, exiting.
2010-03-28 16:31:11.922 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:11.923 Using runtime prefix = /usr
2010-03-28 16:31:11.926 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:11.935 Unable to read configuration file mysql.txt
2010-03-28 16:31:11.943 Empty LocalHostName.
2010-03-28 16:31:11.951 Using localhost value of myth-desktop
2010-03-28 16:31:11.971 New DB connection, total: 1
2010-03-28 16:31:11.982 Unable to connect to database!
2010-03-28 16:31:11.984 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:14.667 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:14.683 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:14.733 Deleting UPnP client...
2010-03-28 16:31:16.365 Failed to init MythContext, exiting.
2010-03-28 16:31:16.467 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:16.469 Using runtime prefix = /usr
2010-03-28 16:31:16.473 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:16.482 Unable to read configuration file mysql.txt
2010-03-28 16:31:16.490 Empty LocalHostName.
2010-03-28 16:31:16.498 Using localhost value of myth-desktop
2010-03-28 16:31:16.518 New DB connection, total: 1
2010-03-28 16:31:16.529 Unable to connect to database!
2010-03-28 16:31:16.531 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:19.214 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:19.230 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:19.280 Deleting UPnP client...
2010-03-28 16:31:20.912 Failed to init MythContext, exiting.
2010-03-28 16:31:21.023 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:21.024 Using runtime prefix = /usr
2010-03-28 16:31:21.029 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:21.037 Unable to read configuration file mysql.txt
2010-03-28 16:31:21.045 Empty LocalHostName.
2010-03-28 16:31:21.054 Using localhost value of myth-desktop
2010-03-28 16:31:21.073 New DB connection, total: 1
2010-03-28 16:31:21.085 Unable to connect to database!
2010-03-28 16:31:21.087 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:23.769 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:23.777 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:23.827 Deleting UPnP client...
2010-03-28 16:31:25.468 Failed to init MythContext, exiting.
2010-03-28 16:31:25.570 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:25.571 Using runtime prefix = /usr
2010-03-28 16:31:25.576 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:25.625 Unable to read configuration file mysql.txt
2010-03-28 16:31:25.634 Empty LocalHostName.
2010-03-28 16:31:25.643 Using localhost value of myth-desktop
2010-03-28 16:31:25.662 New DB connection, total: 1
2010-03-28 16:31:25.674 Unable to connect to database!
2010-03-28 16:31:25.676 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:28.358 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:28.374 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:28.424 Deleting UPnP client...
2010-03-28 16:31:30.056 Failed to init MythContext, exiting.
2010-03-28 16:31:30.168 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:30.169 Using runtime prefix = /usr
2010-03-28 16:31:30.173 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:30.182 Unable to read configuration file mysql.txt
2010-03-28 16:31:30.190 Empty LocalHostName.
2010-03-28 16:31:30.198 Using localhost value of myth-desktop
2010-03-28 16:31:30.218 New DB connection, total: 1
2010-03-28 16:31:30.229 Unable to connect to database!
2010-03-28 16:31:30.231 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:32.914 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:32.930 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:32.980 Deleting UPnP client...
2010-03-28 16:31:34.612 Failed to init MythContext, exiting.
2010-03-28 16:31:34.723 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:34.724 Using runtime prefix = /usr
2010-03-28 16:31:34.729 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:34.737 Unable to read configuration file mysql.txt
2010-03-28 16:31:34.745 Empty LocalHostName.
2010-03-28 16:31:34.754 Using localhost value of myth-desktop
2010-03-28 16:31:34.774 New DB connection, total: 1
2010-03-28 16:31:34.785 Unable to connect to database!
2010-03-28 16:31:34.787 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:37.470 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:37.477 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:37.527 Deleting UPnP client...
2010-03-28 16:31:39.168 Failed to init MythContext, exiting.
2010-03-28 16:31:39.278 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:39.280 Using runtime prefix = /usr
2010-03-28 16:31:39.284 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:39.293 Unable to read configuration file mysql.txt
2010-03-28 16:31:39.301 Empty LocalHostName.
2010-03-28 16:31:39.309 Using localhost value of myth-desktop
2010-03-28 16:31:39.329 New DB connection, total: 1
2010-03-28 16:31:39.340 Unable to connect to database!
2010-03-28 16:31:39.342 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:42.025 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:42.032 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:42.099 Deleting UPnP client...
2010-03-28 16:31:43.723 Failed to init MythContext, exiting.
2010-03-28 16:31:43.835 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:43.836 Using runtime prefix = /usr
2010-03-28 16:31:43.840 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:43.848 Unable to read configuration file mysql.txt
2010-03-28 16:31:43.856 Empty LocalHostName.
2010-03-28 16:31:43.865 Using localhost value of myth-desktop
2010-03-28 16:31:43.885 New DB connection, total: 1
2010-03-28 16:31:43.896 Unable to connect to database!
2010-03-28 16:31:43.898 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:46.580 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:46.596 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:46.646 Deleting UPnP client...
2010-03-28 16:31:48.278 Failed to init MythContext, exiting.
2010-03-28 16:31:48.381 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:48.382 Using runtime prefix = /usr
2010-03-28 16:31:48.387 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:48.395 Unable to read configuration file mysql.txt
2010-03-28 16:31:48.404 Empty LocalHostName.
2010-03-28 16:31:48.412 Using localhost value of myth-desktop
2010-03-28 16:31:48.432 New DB connection, total: 1
2010-03-28 16:31:48.443 Unable to connect to database!
2010-03-28 16:31:48.445 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:51.128 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:51.144 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:51.194 Deleting UPnP client...
2010-03-28 16:31:52.826 Failed to init MythContext, exiting.
2010-03-28 16:31:52.937 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:52.939 Using runtime prefix = /usr
2010-03-28 16:31:52.942 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:52.951 Unable to read configuration file mysql.txt
2010-03-28 16:31:52.959 Empty LocalHostName.
2010-03-28 16:31:52.967 Using localhost value of myth-desktop
2010-03-28 16:31:52.987 New DB connection, total: 1
2010-03-28 16:31:52.998 Unable to connect to database!
2010-03-28 16:31:53.001 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:31:55.683 UPnPautoconf() - No UPnP backends found
2010-03-28 16:31:55.691 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:31:55.741 Deleting UPnP client...
2010-03-28 16:31:57.382 Failed to init MythContext, exiting.
2010-03-28 16:31:57.493 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:31:57.494 Using runtime prefix = /usr
2010-03-28 16:31:57.498 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:31:57.506 Unable to read configuration file mysql.txt
2010-03-28 16:31:57.515 Empty LocalHostName.
2010-03-28 16:31:57.523 Using localhost value of myth-desktop
2010-03-28 16:31:57.543 New DB connection, total: 1
2010-03-28 16:31:57.554 Unable to connect to database!
2010-03-28 16:31:57.556 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:00.273 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:00.280 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:00.330 Deleting UPnP client...
2010-03-28 16:32:01.971 Failed to init MythContext, exiting.
2010-03-28 16:32:02.081 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:02.082 Using runtime prefix = /usr
2010-03-28 16:32:02.087 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:02.095 Unable to read configuration file mysql.txt
2010-03-28 16:32:02.104 Empty LocalHostName.
2010-03-28 16:32:02.112 Using localhost value of myth-desktop
2010-03-28 16:32:02.132 New DB connection, total: 1
2010-03-28 16:32:02.143 Unable to connect to database!
2010-03-28 16:32:02.145 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:04.828 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:04.844 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:04.893 Deleting UPnP client...
2010-03-28 16:32:06.526 Failed to init MythContext, exiting.
2010-03-28 16:32:06.629 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:06.630 Using runtime prefix = /usr
2010-03-28 16:32:06.634 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:06.643 Unable to read configuration file mysql.txt
2010-03-28 16:32:06.651 Empty LocalHostName.
2010-03-28 16:32:06.659 Using localhost value of myth-desktop
2010-03-28 16:32:06.679 New DB connection, total: 1
2010-03-28 16:32:06.690 Unable to connect to database!
2010-03-28 16:32:06.692 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:09.375 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:09.391 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:09.441 Deleting UPnP client...
2010-03-28 16:32:11.073 Failed to init MythContext, exiting.
2010-03-28 16:32:11.184 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:11.185 Using runtime prefix = /usr
2010-03-28 16:32:11.190 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:11.198 Unable to read configuration file mysql.txt
2010-03-28 16:32:11.206 Empty LocalHostName.
2010-03-28 16:32:11.215 Using localhost value of myth-desktop
2010-03-28 16:32:11.235 New DB connection, total: 1
2010-03-28 16:32:11.246 Unable to connect to database!
2010-03-28 16:32:11.248 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:13.930 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:13.946 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:13.996 Deleting UPnP client...
2010-03-28 16:32:15.628 Failed to init MythContext, exiting.
2010-03-28 16:32:15.740 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:15.741 Using runtime prefix = /usr
2010-03-28 16:32:15.745 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:15.754 Unable to read configuration file mysql.txt
2010-03-28 16:32:15.797 Empty LocalHostName.
2010-03-28 16:32:15.812 Using localhost value of myth-desktop
2010-03-28 16:32:15.832 New DB connection, total: 1
2010-03-28 16:32:15.843 Unable to connect to database!
2010-03-28 16:32:15.845 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:18.527 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:18.543 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:18.593 Deleting UPnP client...
2010-03-28 16:32:20.226 Failed to init MythContext, exiting.
2010-03-28 16:32:20.337 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:20.338 Using runtime prefix = /usr
2010-03-28 16:32:20.342 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:20.351 Unable to read configuration file mysql.txt
2010-03-28 16:32:20.359 Empty LocalHostName.
2010-03-28 16:32:20.367 Using localhost value of myth-desktop
2010-03-28 16:32:20.387 New DB connection, total: 1
2010-03-28 16:32:20.398 Unable to connect to database!
2010-03-28 16:32:20.401 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:23.083 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:23.099 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:23.149 Deleting UPnP client...
2010-03-28 16:32:24.781 Failed to init MythContext, exiting.
2010-03-28 16:32:24.892 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:24.894 Using runtime prefix = /usr
2010-03-28 16:32:24.898 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:24.918 Unable to read configuration file mysql.txt
2010-03-28 16:32:24.931 Empty LocalHostName.
2010-03-28 16:32:24.939 Using localhost value of myth-desktop
2010-03-28 16:32:24.960 New DB connection, total: 1
2010-03-28 16:32:24.970 Unable to connect to database!
2010-03-28 16:32:24.973 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:27.655 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:27.663 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:27.713 Deleting UPnP client...
2010-03-28 16:32:29.353 Failed to init MythContext, exiting.
2010-03-28 16:32:29.466 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:29.467 Using runtime prefix = /usr
2010-03-28 16:32:29.470 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:29.479 Unable to read configuration file mysql.txt
2010-03-28 16:32:29.487 Empty LocalHostName.
2010-03-28 16:32:29.495 Using localhost value of myth-desktop
2010-03-28 16:32:29.515 New DB connection, total: 1
2010-03-28 16:32:29.526 Unable to connect to database!
2010-03-28 16:32:29.528 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:32.211 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:32.218 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:32.268 Deleting UPnP client...
2010-03-28 16:32:33.909 Failed to init MythContext, exiting.
2010-03-28 16:32:34.049 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:34.050 Using runtime prefix = /usr
2010-03-28 16:32:34.059 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:34.067 Unable to read configuration file mysql.txt
2010-03-28 16:32:34.076 Empty LocalHostName.
2010-03-28 16:32:34.084 Using localhost value of myth-desktop
2010-03-28 16:32:34.104 New DB connection, total: 1
2010-03-28 16:32:34.115 Unable to connect to database!
2010-03-28 16:32:34.117 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:36.799 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:36.816 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:36.865 Deleting UPnP client...
2010-03-28 16:32:38.498 Failed to init MythContext, exiting.
2010-03-28 16:32:38.610 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:38.611 Using runtime prefix = /usr
2010-03-28 16:32:38.614 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:38.623 Unable to read configuration file mysql.txt
2010-03-28 16:32:38.631 Empty LocalHostName.
2010-03-28 16:32:38.639 Using localhost value of myth-desktop
2010-03-28 16:32:38.659 New DB connection, total: 1
2010-03-28 16:32:38.671 Unable to connect to database!
2010-03-28 16:32:38.673 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:41.355 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:41.371 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:41.421 Deleting UPnP client...
2010-03-28 16:32:43.053 Failed to init MythContext, exiting.
2010-03-28 16:32:43.164 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:43.165 Using runtime prefix = /usr
2010-03-28 16:32:43.170 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:43.178 Unable to read configuration file mysql.txt
2010-03-28 16:32:43.187 Empty LocalHostName.
2010-03-28 16:32:43.195 Using localhost value of myth-desktop
2010-03-28 16:32:43.215 New DB connection, total: 1
2010-03-28 16:32:43.226 Unable to connect to database!
2010-03-28 16:32:43.228 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:45.911 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:45.927 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:45.977 Deleting UPnP client...
2010-03-28 16:32:47.609 Failed to init MythContext, exiting.
2010-03-28 16:32:47.740 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:47.741 Using runtime prefix = /usr
2010-03-28 16:32:47.750 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:47.759 Unable to read configuration file mysql.txt
2010-03-28 16:32:47.767 Empty LocalHostName.
2010-03-28 16:32:47.775 Using localhost value of myth-desktop
2010-03-28 16:32:47.796 New DB connection, total: 1
2010-03-28 16:32:47.807 Unable to connect to database!
2010-03-28 16:32:47.809 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:50.491 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:50.538 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:50.600 Deleting UPnP client...
2010-03-28 16:32:51.289 Failed to init MythContext, exiting.
2010-03-28 16:32:51.393 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:51.394 Using runtime prefix = /usr
2010-03-28 16:32:51.398 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:51.407 Unable to read configuration file mysql.txt
2010-03-28 16:32:51.415 Empty LocalHostName.
2010-03-28 16:32:51.423 Using localhost value of myth-desktop
2010-03-28 16:32:51.443 New DB connection, total: 1
2010-03-28 16:32:51.454 Unable to connect to database!
2010-03-28 16:32:51.457 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:54.027 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:54.038 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:54.088 Deleting UPnP client...
2010-03-28 16:32:54.737 Failed to init MythContext, exiting.
2010-03-28 16:32:54.833 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:54.835 Using runtime prefix = /usr
2010-03-28 16:32:54.838 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:54.846 Unable to read configuration file mysql.txt
2010-03-28 16:32:54.854 Empty LocalHostName.
2010-03-28 16:32:54.863 Using localhost value of myth-desktop
2010-03-28 16:32:54.883 New DB connection, total: 1
2010-03-28 16:32:54.894 Unable to connect to database!
2010-03-28 16:32:54.896 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:32:57.466 UPnPautoconf() - No UPnP backends found
2010-03-28 16:32:57.478 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:32:57.528 Deleting UPnP client...
2010-03-28 16:32:58.176 Failed to init MythContext, exiting.
2010-03-28 16:32:58.287 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:32:58.289 Using runtime prefix = /usr
2010-03-28 16:32:58.294 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:32:58.303 Unable to read configuration file mysql.txt
2010-03-28 16:32:58.311 Empty LocalHostName.
2010-03-28 16:32:58.319 Using localhost value of myth-desktop
2010-03-28 16:32:58.339 New DB connection, total: 1
2010-03-28 16:32:58.350 Unable to connect to database!
2010-03-28 16:32:58.352 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:00.922 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:00.951 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:01.001 Deleting UPnP client...
2010-03-28 16:33:01.635 Failed to init MythContext, exiting.
2010-03-28 16:33:01.709 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:01.710 Using runtime prefix = /usr
2010-03-28 16:33:01.717 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:01.726 Unable to read configuration file mysql.txt
2010-03-28 16:33:01.734 Empty LocalHostName.
2010-03-28 16:33:01.742 Using localhost value of myth-desktop
2010-03-28 16:33:01.792 New DB connection, total: 1
2010-03-28 16:33:01.804 Unable to connect to database!
2010-03-28 16:33:01.808 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:04.379 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:04.390 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:04.440 Deleting UPnP client...
2010-03-28 16:33:05.091 Failed to init MythContext, exiting.
2010-03-28 16:33:05.195 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:05.196 Using runtime prefix = /usr
2010-03-28 16:33:05.198 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:05.207 Unable to read configuration file mysql.txt
2010-03-28 16:33:05.215 Empty LocalHostName.
2010-03-28 16:33:05.223 Using localhost value of myth-desktop
2010-03-28 16:33:05.243 New DB connection, total: 1
2010-03-28 16:33:05.254 Unable to connect to database!
2010-03-28 16:33:05.256 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:07.827 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:07.838 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:07.888 Deleting UPnP client...
2010-03-28 16:33:08.536 Failed to init MythContext, exiting.
2010-03-28 16:33:08.638 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:08.640 Using runtime prefix = /usr
2010-03-28 16:33:08.647 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:08.655 Unable to read configuration file mysql.txt
2010-03-28 16:33:08.663 Empty LocalHostName.
2010-03-28 16:33:08.671 Using localhost value of myth-desktop
2010-03-28 16:33:08.691 New DB connection, total: 1
2010-03-28 16:33:08.702 Unable to connect to database!
2010-03-28 16:33:08.704 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:11.274 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:11.286 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:11.336 Deleting UPnP client...
2010-03-28 16:33:11.984 Failed to init MythContext, exiting.
2010-03-28 16:33:12.101 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:12.102 Using runtime prefix = /usr
2010-03-28 16:33:12.110 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:12.119 Unable to read configuration file mysql.txt
2010-03-28 16:33:12.127 Empty LocalHostName.
2010-03-28 16:33:12.135 Using localhost value of myth-desktop
2010-03-28 16:33:12.156 New DB connection, total: 1
2010-03-28 16:33:12.167 Unable to connect to database!
2010-03-28 16:33:12.169 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:14.739 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:14.751 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:14.801 Deleting UPnP client...
2010-03-28 16:33:15.449 Failed to init MythContext, exiting.
2010-03-28 16:33:15.551 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:15.552 Using runtime prefix = /usr
2010-03-28 16:33:15.586 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:15.600 Unable to read configuration file mysql.txt
2010-03-28 16:33:15.608 Empty LocalHostName.
2010-03-28 16:33:15.617 Using localhost value of myth-desktop
2010-03-28 16:33:15.637 New DB connection, total: 1
2010-03-28 16:33:15.648 Unable to connect to database!
2010-03-28 16:33:15.650 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:18.221 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:18.248 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:18.298 Deleting UPnP client...
2010-03-28 16:33:18.930 Failed to init MythContext, exiting.
2010-03-28 16:33:19.041 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:19.042 Using runtime prefix = /usr
2010-03-28 16:33:19.048 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:19.056 Unable to read configuration file mysql.txt
2010-03-28 16:33:19.090 Empty LocalHostName.
2010-03-28 16:33:19.115 Using localhost value of myth-desktop
2010-03-28 16:33:19.129 New DB connection, total: 1
2010-03-28 16:33:19.151 Unable to connect to database!
2010-03-28 16:33:19.165 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:21.747 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:21.755 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:21.805 Deleting UPnP client...
2010-03-28 16:33:22.460 Failed to init MythContext, exiting.
2010-03-28 16:33:22.558 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:22.559 Using runtime prefix = /usr
2010-03-28 16:33:22.562 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:22.571 Unable to read configuration file mysql.txt
2010-03-28 16:33:22.579 Empty LocalHostName.
2010-03-28 16:33:22.587 Using localhost value of myth-desktop
2010-03-28 16:33:22.607 New DB connection, total: 1
2010-03-28 16:33:22.618 Unable to connect to database!
2010-03-28 16:33:22.621 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:25.189 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:25.202 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:25.252 Deleting UPnP client...
2010-03-28 16:33:25.900 Failed to init MythContext, exiting.
2010-03-28 16:33:25.992 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:25.993 Using runtime prefix = /usr
2010-03-28 16:33:25.994 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:26.002 Unable to read configuration file mysql.txt
2010-03-28 16:33:26.010 Empty LocalHostName.
2010-03-28 16:33:26.019 Using localhost value of myth-desktop
2010-03-28 16:33:26.033 New DB connection, total: 1
2010-03-28 16:33:26.038 Unable to connect to database!
2010-03-28 16:33:26.044 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:28.610 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:28.645 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:28.700 Deleting UPnP client...
2010-03-28 16:33:29.322 Failed to init MythContext, exiting.
2010-03-28 16:33:29.422 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:29.423 Using runtime prefix = /usr
2010-03-28 16:33:29.425 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:29.433 Unable to read configuration file mysql.txt
2010-03-28 16:33:29.442 Empty LocalHostName.
2010-03-28 16:33:29.450 Using localhost value of myth-desktop
2010-03-28 16:33:29.470 New DB connection, total: 1
2010-03-28 16:33:29.481 Unable to connect to database!
2010-03-28 16:33:29.483 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:32.052 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:32.065 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:32.115 Deleting UPnP client...
2010-03-28 16:33:32.763 Failed to init MythContext, exiting.
2010-03-28 16:33:32.860 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:32.861 Using runtime prefix = /usr
2010-03-28 16:33:32.864 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:32.873 Unable to read configuration file mysql.txt
2010-03-28 16:33:32.881 Empty LocalHostName.
2010-03-28 16:33:32.889 Using localhost value of myth-desktop
2010-03-28 16:33:32.909 New DB connection, total: 1
2010-03-28 16:33:32.920 Unable to connect to database!
2010-03-28 16:33:32.923 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:35.493 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:35.521 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:35.571 Deleting UPnP client...
2010-03-28 16:33:36.203 Failed to init MythContext, exiting.
2010-03-28 16:33:36.299 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:36.301 Using runtime prefix = /usr
2010-03-28 16:33:36.304 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:36.313 Unable to read configuration file mysql.txt
2010-03-28 16:33:36.321 Empty LocalHostName.
2010-03-28 16:33:36.329 Using localhost value of myth-desktop
2010-03-28 16:33:36.349 New DB connection, total: 1
2010-03-28 16:33:36.360 Unable to connect to database!
2010-03-28 16:33:36.362 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:38.932 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:38.944 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:38.994 Deleting UPnP client...
2010-03-28 16:33:39.642 Failed to init MythContext, exiting.
2010-03-28 16:33:39.741 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:39.742 Using runtime prefix = /usr
2010-03-28 16:33:39.744 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:39.752 Unable to read configuration file mysql.txt
2010-03-28 16:33:39.760 Empty LocalHostName.
2010-03-28 16:33:39.769 Using localhost value of myth-desktop
2010-03-28 16:33:39.789 New DB connection, total: 1
2010-03-28 16:33:39.830 Unable to connect to database!
2010-03-28 16:33:39.844 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:42.414 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:42.426 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:42.476 Deleting UPnP client...
2010-03-28 16:33:43.123 Failed to init MythContext, exiting.
2010-03-28 16:33:43.222 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:43.223 Using runtime prefix = /usr
2010-03-28 16:33:43.225 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:43.234 Unable to read configuration file mysql.txt
2010-03-28 16:33:43.242 Empty LocalHostName.
2010-03-28 16:33:43.250 Using localhost value of myth-desktop
2010-03-28 16:33:43.270 New DB connection, total: 1
2010-03-28 16:33:43.281 Unable to connect to database!
2010-03-28 16:33:43.283 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:45.854 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:45.865 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:45.915 Deleting UPnP client...
2010-03-28 16:33:46.563 Failed to init MythContext, exiting.
2010-03-28 16:33:46.663 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:46.664 Using runtime prefix = /usr
2010-03-28 16:33:46.673 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:46.682 Unable to read configuration file mysql.txt
2010-03-28 16:33:46.690 Empty LocalHostName.
2010-03-28 16:33:46.698 Using localhost value of myth-desktop
2010-03-28 16:33:46.718 New DB connection, total: 1
2010-03-28 16:33:46.729 Unable to connect to database!
2010-03-28 16:33:46.731 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:49.301 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:49.313 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:49.363 Deleting UPnP client...
2010-03-28 16:33:50.011 Failed to init MythContext, exiting.
2010-03-28 16:33:50.111 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:50.112 Using runtime prefix = /usr
2010-03-28 16:33:50.121 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:50.130 Unable to read configuration file mysql.txt
2010-03-28 16:33:50.138 Empty LocalHostName.
2010-03-28 16:33:50.146 Using localhost value of myth-desktop
2010-03-28 16:33:50.166 New DB connection, total: 1
2010-03-28 16:33:50.177 Unable to connect to database!
2010-03-28 16:33:50.181 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:52.747 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:52.761 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:52.811 Deleting UPnP client...
2010-03-28 16:33:53.459 Failed to init MythContext, exiting.
2010-03-28 16:33:53.562 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:53.563 Using runtime prefix = /usr
2010-03-28 16:33:53.602 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:53.611 Unable to read configuration file mysql.txt
2010-03-28 16:33:53.619 Empty LocalHostName.
2010-03-28 16:33:53.628 Using localhost value of myth-desktop
2010-03-28 16:33:53.648 New DB connection, total: 1
2010-03-28 16:33:53.659 Unable to connect to database!
2010-03-28 16:33:53.661 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:56.231 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:56.243 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:56.293 Deleting UPnP client...
2010-03-28 16:33:56.940 Failed to init MythContext, exiting.
2010-03-28 16:33:57.038 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:33:57.039 Using runtime prefix = /usr
2010-03-28 16:33:57.042 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:33:57.051 Unable to read configuration file mysql.txt
2010-03-28 16:33:57.059 Empty LocalHostName.
2010-03-28 16:33:57.067 Using localhost value of myth-desktop
2010-03-28 16:33:57.087 New DB connection, total: 1
2010-03-28 16:33:57.098 Unable to connect to database!
2010-03-28 16:33:57.101 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2010-03-28 16:33:59.671 UPnPautoconf() - No UPnP backends found
2010-03-28 16:33:59.683 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:33:59.808 Deleting UPnP client...
2010-03-28 16:34:00.481 Failed to init MythContext, exiting.
2010-03-28 16:34:00.586 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:00.587 Using runtime prefix = /usr
2010-03-28 16:34:00.590 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:00.600 Empty LocalHostName.
2010-03-28 16:34:00.674 Using localhost value of myth-desktop
2010-03-28 16:34:00.694 New DB connection, total: 1
2010-03-28 16:34:00.705 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:00.707 Closing DB connection named 'DBManager0'
2010-03-28 16:34:00.717 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:00.733 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:00.863 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:00.864 Using runtime prefix = /usr
2010-03-28 16:34:00.865 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:00.875 Empty LocalHostName.
2010-03-28 16:34:00.882 Using localhost value of myth-desktop
2010-03-28 16:34:00.902 New DB connection, total: 1
2010-03-28 16:34:00.913 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:00.915 Closing DB connection named 'DBManager0'
2010-03-28 16:34:00.925 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:00.940 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:01.071 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:01.072 Using runtime prefix = /usr
2010-03-28 16:34:01.073 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:01.083 Empty LocalHostName.
2010-03-28 16:34:01.090 Using localhost value of myth-desktop
2010-03-28 16:34:01.110 New DB connection, total: 1
2010-03-28 16:34:01.142 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.157 Closing DB connection named 'DBManager0'
2010-03-28 16:34:01.166 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.181 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:01.310 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:01.311 Using runtime prefix = /usr
2010-03-28 16:34:01.315 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:01.324 Empty LocalHostName.
2010-03-28 16:34:01.332 Using localhost value of myth-desktop
2010-03-28 16:34:01.351 New DB connection, total: 1
2010-03-28 16:34:01.363 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.365 Closing DB connection named 'DBManager0'
2010-03-28 16:34:01.374 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.389 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:01.520 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:01.521 Using runtime prefix = /usr
2010-03-28 16:34:01.523 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:01.532 Empty LocalHostName.
2010-03-28 16:34:01.540 Using localhost value of myth-desktop
2010-03-28 16:34:01.560 New DB connection, total: 1
2010-03-28 16:34:01.571 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.573 Closing DB connection named 'DBManager0'
2010-03-28 16:34:01.582 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.598 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:01.727 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:01.728 Using runtime prefix = /usr
2010-03-28 16:34:01.732 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:01.741 Empty LocalHostName.
2010-03-28 16:34:01.748 Using localhost value of myth-desktop
2010-03-28 16:34:01.768 New DB connection, total: 1
2010-03-28 16:34:01.779 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.782 Closing DB connection named 'DBManager0'
2010-03-28 16:34:01.791 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.806 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:01.935 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:01.936 Using runtime prefix = /usr
2010-03-28 16:34:01.940 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:01.949 Empty LocalHostName.
2010-03-28 16:34:01.956 Using localhost value of myth-desktop
2010-03-28 16:34:01.976 New DB connection, total: 1
2010-03-28 16:34:01.988 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:01.990 Closing DB connection named 'DBManager0'
2010-03-28 16:34:01.999 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.014 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:02.143 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:02.144 Using runtime prefix = /usr
2010-03-28 16:34:02.148 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:02.157 Empty LocalHostName.
2010-03-28 16:34:02.165 Using localhost value of myth-desktop
2010-03-28 16:34:02.185 New DB connection, total: 1
2010-03-28 16:34:02.217 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.232 Closing DB connection named 'DBManager0'
2010-03-28 16:34:02.241 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.257 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:02.387 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:02.388 Using runtime prefix = /usr
2010-03-28 16:34:02.390 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:02.399 Empty LocalHostName.
2010-03-28 16:34:02.406 Using localhost value of myth-desktop
2010-03-28 16:34:02.426 New DB connection, total: 1
2010-03-28 16:34:02.437 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.440 Closing DB connection named 'DBManager0'
2010-03-28 16:34:02.449 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.464 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:34:02.586 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:34:02.587 Using runtime prefix = /usr
2010-03-28 16:34:02.589 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:34:02.599 Empty LocalHostName.
2010-03-28 16:34:02.606 Using localhost value of myth-desktop
2010-03-28 16:34:02.626 New DB connection, total: 1
2010-03-28 16:34:02.638 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.641 Closing DB connection named 'DBManager0'
2010-03-28 16:34:02.649 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:34:02.665 Current MythTV Schema Version (DBSchemaVer): 1254
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2010-03-28 16:36:17.709 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:36:17.710 Using runtime prefix = /usr
2010-03-28 16:36:17.725 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:36:17.734 Empty LocalHostName.
2010-03-28 16:36:17.742 Using localhost value of myth-desktop
2010-03-28 16:36:17.757 New DB connection, total: 1
2010-03-28 16:36:17.762 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:36:17.772 Closing DB connection named 'DBManager0'
2010-03-28 16:36:17.777 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:36:17.790 Current MythTV Schema Version (DBSchemaVer): 1254
2010-03-28 16:36:17.794 MythBackend: Running as a slave backend.
2010-03-28 16:36:17.803 New DB connection, total: 2
2010-03-28 16:36:17.809 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:36:17.881 New DB connection, total: 3
2010-03-28 16:36:17.892 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:36:17.900 New DB connection, total: 4
2010-03-28 16:36:17.909 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:36:18.735 DVBChan(10:/dev/dvb/adapter0/frontend0) Warning: Your frequency setting (11836500) is out of range. (min/max:950000/2150000)
2010-03-28 16:36:18.768 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-28 16:36:18.775 Main::Registering HttpStatus Extension
2010-03-28 16:36:18.783 Enabled verbose msgs:  important general
2010-03-28 16:36:19.796 Connecting to master server: localhost:6543
2010-03-28 16:36:19.817 Connection to master server timed out.
2010-03-28 16:36:20.826 Connecting to master server: localhost:6543
2010-03-28 16:36:20.833 Connection to master server timed out.
2010-03-28 16:36:21.842 Connecting to master server: localhost:6543
2010-03-28 16:36:21.858 Connection to master server timed out.
2010-03-28 16:36:22.866 Connecting to master server: localhost:6543
2010-03-28 16:41:03.331 Connection to master server timed out.
2010-03-28 16:41:04.339 Connecting to master server: localhost:6543
2010-03-28 16:41:04.356 Connection to master server timed out.
2010-03-28 16:41:05.364 Connecting to master server: localhost:6543
2010-03-28 16:41:05.381 Connection to master server timed out.
2010-03-28 16:41:06.389 Connecting to master server: localhost:6543
2010-03-28 16:41:06.406 Connection to master server timed out.
2010-03-28 16:41:07.414 Connecting to master server: localhost:6543
2010-03-28 16:41:07.445 Connection to master server timed out.
2010-03-28 16:41:08.464 Connecting to master server: localhost:6543
2010-03-28 16:41:08.481 Connection to master server timed out.
2010-03-28 16:41:08.845 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not count Uncorrected Blocks
			eno: Function not implemented (38)
2010-03-28 16:41:09.489 Connecting to master server: localhost:6543
2010-03-28 16:41:09.497 Connection to master server timed out.
2010-03-28 16:41:10.506 Connecting to master server: localhost:6543
2010-03-28 16:41:10.523 Connection to master server timed out.
2010-03-28 16:41:11.531 Connecting to master server: localhost:6543
2010-03-28 16:46:03.809 Connection to master server timed out.
2010-03-28 16:46:04.817 Connecting to master server: localhost:6543
2010-03-28 16:46:04.834 Connection to master server timed out.
2010-03-28 16:46:05.842 Connecting to master server: localhost:6543
2010-03-28 16:46:05.859 Connection to master server timed out.
2010-03-28 16:46:06.867 Connecting to master server: localhost:6543
2010-03-28 16:46:06.901 Connection to master server timed out.
2010-03-28 16:46:07.909 Connecting to master server: localhost:6543
2010-03-28 16:46:07.934 Connection to master server timed out.
2010-03-28 16:46:08.942 Connecting to master server: localhost:6543
2010-03-28 16:46:08.959 Connection to master server timed out.
2010-03-28 16:46:09.967 Connecting to master server: localhost:6543
2010-03-28 16:46:09.984 Connection to master server timed out.
2010-03-28 16:46:10.992 Connecting to master server: localhost:6543
2010-03-28 16:46:11.009 Connection to master server timed out.
2010-03-28 16:46:12.017 Connecting to master server: localhost:6543
2010-03-28 16:46:12.051 Connection to master server timed out.
2010-03-28 16:46:13.059 Connecting to master server: localhost:6543
2010-03-28 16:46:13.075 Connection to master server timed out.
2010-03-28 16:46:14.084 Connecting to master server: localhost:6543
2010-03-28 16:46:14.100 Connection to master server timed out.
2010-03-28 16:46:15.109 Connecting to master server: localhost:6543
2010-03-28 16:46:15.125 Connection to master server timed out.
2010-03-28 16:46:16.134 Connecting to master server: localhost:6543
2010-03-28 16:46:16.150 Connection to master server timed out.
2010-03-28 16:46:17.159 Connecting to master server: localhost:6543
2010-03-28 16:46:17.209 Connection to master server timed out.
2010-03-28 16:46:18.217 Connecting to master server: localhost:6543
2010-03-28 16:46:18.234 Connection to master server timed out.
2010-03-28 16:46:19.242 Connecting to master server: localhost:6543
2010-03-28 16:46:19.259 Connection to master server timed out.
2010-03-28 16:46:20.267 Connecting to master server: localhost:6543
2010-03-28 16:46:20.284 Connection to master server timed out.
2010-03-28 16:46:21.292 Connecting to master server: localhost:6543
2010-03-28 16:46:21.308 Connection to master server timed out.
2010-03-28 16:46:22.317 Connecting to master server: localhost:6543
2010-03-28 16:46:22.367 Connection to master server timed out.
2010-03-28 16:46:23.375 Connecting to master server: localhost:6543
2010-03-28 16:46:23.392 Connection to master server timed out.
2010-03-28 16:46:24.400 Connecting to master server: localhost:6543
2010-03-28 16:46:24.417 Connection to master server timed out.
2010-03-28 16:46:25.425 Connecting to master server: localhost:6543
2010-03-28 16:46:25.442 Connection to master server timed out.
2010-03-28 16:46:26.450 Connecting to master server: localhost:6543
2010-03-28 16:46:26.467 Connection to master server timed out.
2010-03-28 16:46:27.475 Connecting to master server: localhost:6543
2010-03-28 16:46:27.506 Connection to master server timed out.
2010-03-28 16:46:28.525 Connecting to master server: localhost:6543
2010-03-28 16:46:28.541 Connection to master server timed out.
2010-03-28 16:46:29.550 Connecting to master server: localhost:6543
2010-03-28 16:46:29.566 Connection to master server timed out.
2010-03-28 16:46:30.574 Connecting to master server: localhost:6543
2010-03-28 16:46:30.591 Connection to master server timed out.
2010-03-28 16:46:31.599 Connecting to master server: localhost:6543
2010-03-28 16:46:31.608 Connection to master server timed out.
2010-03-28 16:46:32.616 Connecting to master server: localhost:6543
2010-03-28 16:46:32.656 Connection to master server timed out.
2010-03-28 16:46:33.674 Connecting to master server: localhost:6543
2010-03-28 16:46:33.691 Connection to master server timed out.
2010-03-28 16:46:34.705 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not count Uncorrected Blocks
			eno: Function not implemented (38)
2010-03-28 16:46:34.723 Connecting to master server: localhost:6543
2010-03-28 16:46:34.733 Connection to master server timed out.
2010-03-28 16:46:35.741 Connecting to master server: localhost:6543
2010-03-28 16:46:35.758 Connection to master server timed out.
2010-03-28 16:46:36.766 Connecting to master server: localhost:6543
2010-03-28 16:46:36.783 Connection to master server timed out.
2010-03-28 16:46:37.791 Connecting to master server: localhost:6543
2010-03-28 16:46:37.800 Connection to master server timed out.
2010-03-28 16:46:38.808 Connecting to master server: localhost:6543
2010-03-28 16:46:38.816 Connection to master server timed out.
2010-03-28 16:46:39.513 PID 0xff status: Encrypted
2010-03-28 16:46:39.824 Connecting to master server: localhost:6543
2010-03-28 16:46:39.833 Connection to master server timed out.
2010-03-28 16:46:40.841 Connecting to master server: localhost:6543
2010-03-28 16:46:40.849 Connection to master server timed out.
2010-03-28 16:49:49.871 Connecting to master server: localhost:6543
2010-03-28 16:49:49.895 Connection to master server timed out.
2010-03-28 16:49:50.073 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffb622c240)
2010-03-28 16:49:50.913 Connecting to master server: localhost:6543
2010-03-28 16:49:50.921 Connection to master server timed out.
2010-03-28 16:49:51.904 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:49:51.917 Using runtime prefix = /usr
2010-03-28 16:49:51.921 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:49:51.930 Empty LocalHostName.
2010-03-28 16:49:51.939 Using localhost value of myth-desktop
2010-03-28 16:50:31.694 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:31.790 Using runtime prefix = /usr
2010-03-28 16:50:31.868 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:32.128 Empty LocalHostName.
2010-03-28 16:50:32.151 Using localhost value of myth-desktop
2010-03-28 16:50:32.324 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:50:32.377 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
2010-03-28 16:50:32.432 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
.............................................................................
2010-03-28 16:50:34.566 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:34.584 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:34.693 Deleting UPnP client...
2010-03-28 16:50:34.701 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-03-28 16:50:35.418 Failed to init MythContext, exiting.
2010-03-28 16:50:35.528 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:35.537 Using runtime prefix = /usr
2010-03-28 16:50:35.609 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:35.727 Empty LocalHostName.
2010-03-28 16:50:35.734 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:38.348 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:38.358 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:38.408 Deleting UPnP client...
2010-03-28 16:50:38.873 Failed to init MythContext, exiting.
2010-03-28 16:50:39.014 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:39.035 Using runtime prefix = /usr
2010-03-28 16:50:39.058 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:39.066 Empty LocalHostName.
2010-03-28 16:50:39.074 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:41.644 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:41.656 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:41.706 Deleting UPnP client...
2010-03-28 16:50:42.354 Failed to init MythContext, exiting.
2010-03-28 16:50:42.402 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:42.402 Using runtime prefix = /usr
2010-03-28 16:50:42.437 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:42.448 Empty LocalHostName.
2010-03-28 16:50:42.456 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:45.136 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:45.146 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:45.196 Deleting UPnP client...
2010-03-28 16:50:45.835 Failed to init MythContext, exiting.
2010-03-28 16:50:45.883 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:45.884 Using runtime prefix = /usr
2010-03-28 16:50:45.887 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:45.896 Empty LocalHostName.
2010-03-28 16:50:45.904 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:48.472 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:48.486 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:48.536 Deleting UPnP client...
2010-03-28 16:50:49.183 Failed to init MythContext, exiting.
2010-03-28 16:50:49.231 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:49.232 Using runtime prefix = /usr
2010-03-28 16:50:49.235 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:49.244 Empty LocalHostName.
2010-03-28 16:50:49.252 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:51.932 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:51.959 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:52.008 Deleting UPnP client...
2010-03-28 16:50:52.631 Failed to init MythContext, exiting.
2010-03-28 16:50:52.679 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:52.680 Using runtime prefix = /usr
2010-03-28 16:50:52.683 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:52.692 Empty LocalHostName.
2010-03-28 16:50:52.700 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:55.379 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:55.390 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:55.440 Deleting UPnP client...
2010-03-28 16:50:57.080 Failed to init MythContext, exiting.
2010-03-28 16:50:57.143 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:50:57.144 Using runtime prefix = /usr
2010-03-28 16:50:57.147 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:50:57.156 Empty LocalHostName.
2010-03-28 16:50:57.164 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:50:59.844 UPnPautoconf() - No UPnP backends found
2010-03-28 16:50:59.854 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:50:59.904 Deleting UPnP client...
2010-03-28 16:51:00.543 Failed to init MythContext, exiting.
2010-03-28 16:51:00.600 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:51:00.601 Using runtime prefix = /usr
2010-03-28 16:51:00.604 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:51:00.612 Empty LocalHostName.
2010-03-28 16:51:00.620 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:51:03.318 UPnPautoconf() - No UPnP backends found
2010-03-28 16:51:03.327 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:51:03.377 Deleting UPnP client...
2010-03-28 16:51:04.018 Failed to init MythContext, exiting.
2010-03-28 16:51:04.073 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:51:04.074 Using runtime prefix = /usr
2010-03-28 16:51:04.077 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:51:04.085 Empty LocalHostName.
2010-03-28 16:51:04.093 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:51:06.665 UPnPautoconf() - No UPnP backends found
2010-03-28 16:51:06.675 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:51:06.725 Deleting UPnP client...
2010-03-28 16:51:08.373 Failed to init MythContext, exiting.
2010-03-28 16:51:08.437 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:51:08.437 Using runtime prefix = /usr
2010-03-28 16:51:08.441 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:51:08.449 Empty LocalHostName.
2010-03-28 16:51:08.457 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:51:11.137 UPnPautoconf() - No UPnP backends found
2010-03-28 16:51:11.193 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:51:11.256 Deleting UPnP client...
2010-03-28 16:51:11.937 Failed to init MythContext, exiting.
2010-03-28 16:51:11.984 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:51:11.985 Using runtime prefix = /usr
2010-03-28 16:51:11.989 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:51:11.997 Empty LocalHostName.
2010-03-28 16:51:12.005 Using localhost value of myth-desktop
................................................................................
2010-03-28 16:51:14.688 UPnPautoconf() - No UPnP backends found
2010-03-28 16:51:14.695 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-03-28 16:51:14.745 Deleting UPnP client...
2010-03-28 16:51:15.385 Failed to init MythContext, exiting.
2010-03-28 16:51:15.433 mythbackend version: branches/release-0-23-fixes [23820] www.mythtv.org
2010-03-28 16:51:15.433 Using runtime prefix = /usr
2010-03-28 16:51:15.437 Using configuration directory = /home/mythtv/.mythtv
2010-03-28 16:51:15.445 Empty LocalHostName.
2010-03-28 16:51:15.453 Using localhost value of myth-desktop
2010-03-28 16:51:15.468 New DB connection, total: 1
2010-03-28 16:51:15.473 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:51:15.478 Closing DB connection named 'DBManager0'
2010-03-28 16:51:15.487 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:51:15.499 Current MythTV Schema Version (DBSchemaVer): 1254
2010-03-28 16:51:15.504 MythBackend: Running as a slave backend.
2010-03-28 16:51:15.523 New DB connection, total: 2
2010-03-28 16:51:15.537 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:51:15.633 New DB connection, total: 3
2010-03-28 16:51:15.645 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:51:15.654 New DB connection, total: 4
2010-03-28 16:51:15.662 Connected to database 'mythconverg' at host: localhost
2010-03-28 16:51:16.439 DVBChan(10:/dev/dvb/adapter0/frontend0) Warning: Your frequency setting (11836500) is out of range. (min/max:950000/2150000)
2010-03-28 16:51:16.501 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-28 16:51:16.541 Main::Registering HttpStatus Extension
2010-03-28 16:51:16.553 Enabled verbose msgs:  important general
2010-03-28 16:51:17.564 Connecting to master server: localhost:6543
2010-03-28 16:51:17.577 Connection to master server timed out.
2010-03-28 16:51:18.586 Connecting to master server: localhost:6543
2010-03-28 16:51:18.618 Connection to master server timed out.
2010-03-28 16:51:19.627 Connecting to master server: localhost:6543
2010-03-28 16:51:19.651 Connection to master server timed out.
2010-03-28 16:51:20.659 Connecting to master server: localhost:6543
2010-03-28 16:51:20.676 Connection to master server timed out.
2010-03-28 16:51:21.684 Connecting to master server: localhost:6543
2010-03-28 16:51:21.706 Connection to master server timed out.
2010-03-28 16:51:22.725 Connecting to master server: localhost:6543
2010-03-28 16:51:22.749 Connection to master server timed out.
2010-03-28 16:51:23.774 Connecting to master server: localhost:6543
2010-03-28 16:51:23.782 Connection to master server timed out.
2010-03-28 16:51:24.790 Connecting to master server: localhost:6543
2010-03-28 16:51:24.806 Connection to master server timed out.
2010-03-28 16:51:25.815 Connecting to master server: localhost:6543
2010-03-28 16:51:25.831 Connection to master server timed out.
2010-03-28 16:51:26.839 Connecting to master server: localhost:6543
```

edit2: I changed the mysql password but still the same error.
```
$ mysql -u root mythconverg
mysql> grant all on mythconverg.* to 'mythtv'@'%' identified by "password";
mysql> flush privileges;

mysql> grant all on mythconverg.* to 'mythtv'@'localhost' identified by "password";
mysql> flush privileges;

Then edit /etc/mythtv/mysql.txt and change the following line:
DBPassword=password
replacing the 'password' with your selected password.
```
Strangely I can see the tv guide with all upcoming tv shows. So it seems that not everything is going wrong!?

edit3: I reinstalled again and after first reboot everything was fine. Then I restored from backup-file and again I can't connect to the database; I don't know what's wrong...

---

### Post by Stevi on 2010-03-28
I fixed it with the help of a nice guy from the mythtv-users irc.

I had to change the ip/hostename to the one i used before. now it's working again :)

---

