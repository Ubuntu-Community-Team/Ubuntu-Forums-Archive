---
title: "No TV on Secondary Backend"
date: 2008-10-06
forum: Mythbuntu
---

### Post by MailerDaemon on 2008-10-06
Hi,

I installed mythbuntu 8.04.1 on my pc as a Primary Backend with Frontend. TV and reconrding works.
Now i installed a Secondary Backend with Frontend on an other pc with no tv card. I want to watch tv from the primary backend on the secondary but everytime i go to watch tv just nothing happens. But i can watch shows, that i recorded on the primary backend with the secondary and the mysql connection is also succesfull. 
In the mythtv backend setup of the secondary backend are the channels listet that i have on the primary, but "capture cards" and "input connectors" have no entry. Under "Video Sources" is the same entry like on the primary backend.

bye, 

Till

---

### Post by newlinux on 2008-10-06
please post your backend and frontend logs when watch tv fails on your remote frontend. They are in

/var/log/mythtv/

Your secondary backend setup should show no cards as the backend setup only shows cards that are definied for that machine, so that isn't the problem. it should show the same video sources and channels as those are globally available to all backends.There's probably nothing wrong with your secondary backend, just probably something wrong with the remote frontend.

---

### Post by MailerDaemon on 2008-10-07
okay here is the Backend Log of the secondary backend:

```

No error type from QSqlError?  Strange...
2008-10-07 20:15:03.960 Cannot login to database?
2008-10-07 20:15:03.961 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [192.168.0.101]  
[console is not interactive, using default '192.168.0.101']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [XXX]  
[console is not interactive, using default 'XXX']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2008-10-07 20:15:03.972 Unable to connect to database!
2008-10-07 20:15:03.973 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.0.101' (101)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-10-07 20:15:04.026 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-10-07 20:15:04.077 Cannot login to database?
2008-10-07 20:15:04.079 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [192.168.0.101]  
[console is not interactive, using default '192.168.0.101']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [XXX]  
[console is not interactive, using default 'XXX']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2008-10-07 20:15:04.169 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-07 20:15:04.171 Closing DB connection named 'DBManager0'
2008-10-07 20:15:04.172 Deleting UPnP client...
2008-10-07 20:15:04.172 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-10-07 20:15:04.837 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-07 20:15:04.843 New DB connection, total: 2
2008-10-07 20:15:04.891 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-07 20:15:04.894 Current Schema Version: 1214
Running as a slave backend.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-10-07 20:15:04.923 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-10-07 20:15:04.924 Main::Registering HttpStatus Extension
2008-10-07 20:15:04.925 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-10-07 20:15:04.925 Enabled verbose msgs:  important general
2008-10-07 20:15:05.952 Connecting to master server: 192.168.0.101:6543
2008-10-07 20:15:05.980 Connected successfully
2008-10-07 20:16:36.608 MainServer::HandleAnnounce Playback
2008-10-07 20:16:36.613 adding: keller-media as a client (events: 0)
2008-10-07 20:16:36.614 MainServer::HandleRecorderQuery() Unknown encoder: 1
2008-10-07 20:16:38.664 MainServer::HandleAnnounce Playback
2008-10-07 20:16:38.665 adding: keller-media as a client (events: 0)
2008-10-07 20:16:38.666 MainServer::HandleRecorderQuery() Unknown encoder: 1

```

and the log of the front end:

```

Starting mythfrontend.real..
2008-10-07 19:13:12.040 New DB connection, total: 2
2008-10-07 19:13:12.087 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-07 19:13:12.091 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-07 19:13:12.091 Enabled verbose msgs:  important general
2008-10-07 19:13:12.321 Unable to parse themeinfo.xml for glass-wide
2008-10-07 19:13:12.321 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-07 19:13:12.660 Unable to parse themeinfo.xml for glass-wide
2008-10-07 19:13:12.660 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-07 19:13:13.134 Primary screen 0.
2008-10-07 19:13:13.135 Using screen 0, 800x600 at 0,0
2008-10-07 19:13:13.136 Switching to square mode (Mythbuntu-8.04)
2008-10-07 19:13:13.149 Using the Qt painter
2008-10-07 19:13:13.150 lirc_init failed for mythtv, see preceding messages
2008-10-07 19:13:13.150 JoystickMenuClient Error: Joystick disabled - Failed to read /home/till/.mythtv/joystickmenurc
2008-10-07 19:13:13.293 Specified base font 'medium' does not exist for font clock
2008-10-07 19:13:13.293 Specified base font 'medium' does not exist for font small
2008-10-07 19:13:13.293 Specified base font 'medium' does not exist for font medium
2008-10-07 19:13:13.293 Specified base font 'medium' does not exist for font large
2008-10-07 19:13:13.295 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-10-07 19:13:13.395 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-07 19:13:13.467 Registering Internal as a media playback plugin.
2008-10-07 19:13:13.610 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-07 19:13:13.916 Failed to run 'cdrecord --scanbus'
2008-10-07 19:13:13.919 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-07 19:13:13.922 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-07 19:13:13.971 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-10-07 19:13:16.768 Connecting to backend server: 192.168.0.101:6543 (try 1 of 5)
2008-10-07 19:13:16.769 Using protocol version 40
2008-10-07 19:13:18.432 Deleting UPnP client...
Starting mythfrontend.real..
2008-10-07 20:15:12.407 New DB connection, total: 2
2008-10-07 20:15:12.460 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-07 20:15:12.463 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-07 20:15:12.463 Enabled verbose msgs:  important general
2008-10-07 20:15:13.898 Unable to parse themeinfo.xml for glass-wide
2008-10-07 20:15:13.898 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-07 20:15:14.870 Unable to parse themeinfo.xml for glass-wide
2008-10-07 20:15:14.870 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-07 20:15:16.275 No theme dir: /home/till/.mythtv/themes/Mythbuntu-8.04
2008-10-07 20:15:16.276 Primary screen 0.
2008-10-07 20:15:16.276 Using screen 0, 800x600 at 0,0
2008-10-07 20:15:16.278 No theme dir: /home/till/.mythtv/themes/Mythbuntu-8.04
2008-10-07 20:15:16.278 Switching to square mode (Mythbuntu-8.04)
2008-10-07 20:15:16.370 Using the Qt painter
2008-10-07 20:15:16.371 JoystickMenuClient Error: Joystick disabled - Failed to read /home/till/.mythtv/joystickmenurc
2008-10-07 20:15:16.371 lirc init success using configuration file: /home/till/.mythtv/lircrc
2008-10-07 20:15:16.698 Specified base font 'medium' does not exist for font clock
2008-10-07 20:15:16.698 Specified base font 'medium' does not exist for font small
2008-10-07 20:15:16.698 Specified base font 'medium' does not exist for font medium
2008-10-07 20:15:16.698 Specified base font 'medium' does not exist for font large
2008-10-07 20:15:16.699 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-10-07 20:15:16.814 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-07 20:15:16.902 Registering Internal as a media playback plugin.
2008-10-07 20:15:17.049 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-07 20:15:17.369 Failed to run 'cdrecord --scanbus'
2008-10-07 20:15:17.372 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-07 20:15:17.375 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-07 20:15:17.422 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-10-07 20:15:17.640 No theme dir: /home/till/.mythtv/themes/Mythbuntu-8.04
2008-10-07 20:16:36.596 Connecting to backend server: 192.168.0.101:6543 (try 1 of 5)
2008-10-07 20:16:36.597 Using protocol version 40
2008-10-07 20:16:36.608 TV: Attempting to change from None to WatchingLiveTV
2008-10-07 20:16:36.608 Using protocol version 40
2008-10-07 20:16:36.616 GetEntryAt(-1) failed.
2008-10-07 20:16:36.623 EntryToProgram(0@Do Jan 1 01:00:00 1970) failed to get pginfo
2008-10-07 20:16:36.623 TV Error: LiveTV not successfully started
2008-10-07 20:16:36.623 TV Error: LiveTV not successfully started
2008-10-07 20:16:36.713 TV: Deleting TV Chain in destructor
2008-10-07 20:16:36.716 DPMS Deactivated 
2008-10-07 20:16:36.717 DPMS Reactivated.
2008-10-07 20:16:38.664 TV: Attempting to change from None to WatchingLiveTV
2008-10-07 20:16:38.664 Using protocol version 40
2008-10-07 20:16:38.667 GetEntryAt(-1) failed.
2008-10-07 20:16:38.669 EntryToProgram(0@Do Jan 1 01:00:00 1970) failed to get pginfo
2008-10-07 20:16:38.669 TV Error: LiveTV not successfully started
2008-10-07 20:16:38.669 TV Error: LiveTV not successfully started
2008-10-07 20:16:38.767 TV: Deleting TV Chain in destructor
2008-10-07 20:16:38.770 DPMS Deactivated 
2008-10-07 20:16:38.770 DPMS Reactivated.
2008-10-07 20:16:41.540 Deleting UPnP client...

```

i replaced the passwort of the sql db to XXX

thanks for the help

---

### Post by MailerDaemon on 2008-10-10
any idea? :(

---

### Post by newlinux on 2008-10-10
Looks like your secondary backend got setup correctly at the end of the log. May I ask why you are using a secondary backend with no tuners? ARe you using it for job processing?

Also, can you show us the backend log from the machine that has the tuner you are trying to access in liveTV (your primary backend). That will have more info on what's happening with your liveTV.

---

### Post by MailerDaemon on 2008-10-10
there is no tv access in the room the secondary backend stands. and i want to watch dvds on it with its own dvd device. Can i do this with a front end only?

---

### Post by newlinux on 2008-10-10
You don't need a secondary backend on a machine to watch DVDs from mythfrontend.

---

### Post by MailerDaemon on 2008-10-11
okay thanks then i will try only a frontend!!! i thought a frontend can only stream media! :-k

---

### Post by MailerDaemon on 2008-10-11
Now i set it to frontend only. The front end say: Can not connect to master backend :(

here is the log of the frontend:

```

Starting mythfrontend.real..
2008-10-12 02:37:16.081 New DB connection, total: 2
2008-10-12 02:37:16.128 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-12 02:37:16.132 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-12 02:37:16.132 Enabled verbose msgs:  important general
2008-10-12 02:37:16.564 Unable to parse themeinfo.xml for glass-wide
2008-10-12 02:37:16.564 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-12 02:37:16.929 Unable to parse themeinfo.xml for glass-wide
2008-10-12 02:37:16.930 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-12 02:37:17.509 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:37:17.511 Primary screen 0.
2008-10-12 02:37:17.512 Using screen 0, 800x600 at 0,0
2008-10-12 02:37:17.513 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:37:17.514 Switching to square mode (G.A.N.T)
2008-10-12 02:37:17.541 Using the Qt painter
2008-10-12 02:37:17.541 lirc_init failed for mythtv, see preceding messages
2008-10-12 02:37:17.541 JoystickMenuClient Error: Joystick disabled - Failed to read /home/till/.mythtv/joystickmenurc
2008-10-12 02:37:17.675 Removing stale cache dir: /home/till/.mythtv/themecache/Mythbuntu-8.04.800.600
2008-10-12 02:37:17.770 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-10-12 02:37:17.869 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-12 02:37:18.072 Registering Internal as a media playback plugin.
2008-10-12 02:37:18.173 Inserting MythFlix initial database information.
2008-10-12 02:37:18.173 Upgrading to MythFlix schema version 1000
2008-10-12 02:37:18.201 Upgrading to MythFlix schema version 1001
2008-10-12 02:37:18.402 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-12 02:37:18.423 Setting Up MythMovies Database Tables
2008-10-12 02:37:18.455 MythMovies Database Setup Complete
2008-10-12 02:37:18.705 Failed to run 'cdrecord --scanbus'
2008-10-12 02:37:18.708 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-12 02:37:18.711 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-12 02:37:18.834 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-10-12 02:37:19.212 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:37:23.809 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:37:23.810 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:37:25.574 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:37:25.574 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:37:29.748 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T/ui.xml
2008-10-12 02:37:29.929 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:37:29.929 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:37:43.267 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml
2008-10-12 02:37:43.562 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-10-12 02:37:43.563 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2008-10-12 02:37:48.633 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:37:48.634 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:37:51.189 Deleting UPnP client...
Starting mythfrontend.real..
2008-10-12 02:39:12.635 New DB connection, total: 2
2008-10-12 02:39:12.685 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-12 02:39:12.688 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-12 02:39:12.689 Enabled verbose msgs:  important general
2008-10-12 02:39:13.818 Unable to parse themeinfo.xml for glass-wide
2008-10-12 02:39:13.818 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-12 02:39:15.507 Unable to parse themeinfo.xml for glass-wide
2008-10-12 02:39:15.507 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-12 02:39:16.132 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:39:16.134 Primary screen 0.
2008-10-12 02:39:16.135 Using screen 0, 800x600 at 0,0
2008-10-12 02:39:16.137 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:39:16.138 Switching to square mode (G.A.N.T)
2008-10-12 02:39:16.259 Using the Qt painter
2008-10-12 02:39:16.260 JoystickMenuClient Error: Joystick disabled - Failed to read /home/till/.mythtv/joystickmenurc
2008-10-12 02:39:16.260 lirc init success using configuration file: /home/till/.mythtv/lircrc
2008-10-12 02:39:16.729 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-10-12 02:39:16.830 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-12 02:39:16.978 Registering Internal as a media playback plugin.
2008-10-12 02:39:17.138 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-12 02:39:17.456 Failed to run 'cdrecord --scanbus'
2008-10-12 02:39:17.459 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-12 02:39:17.462 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-12 02:39:17.550 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-10-12 02:39:17.822 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:40:18.333 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:40:18.334 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:40:19.279 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:40:19.279 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:40:22.963 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:40:22.964 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:40:24.154 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:40:24.154 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:40:28.175 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:40:28.175 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:40:30.188 Deleting UPnP client...
Starting mythfrontend.real..
2008-10-12 02:41:21.199 New DB connection, total: 2
2008-10-12 02:41:21.248 Connected to database 'mythconverg' at host: 192.168.0.101
2008-10-12 02:41:21.253 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-12 02:41:21.253 Enabled verbose msgs:  important general
2008-10-12 02:41:21.402 Unable to parse themeinfo.xml for glass-wide
2008-10-12 02:41:21.402 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-12 02:41:21.559 Unable to parse themeinfo.xml for glass-wide
2008-10-12 02:41:21.559 The theme (glass-wide) is missing a themeinfo.xml file
2008-10-12 02:41:21.845 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:41:21.849 Primary screen 0.
2008-10-12 02:41:21.849 Using screen 0, 800x600 at 0,0
2008-10-12 02:41:21.850 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:41:21.851 Switching to square mode (G.A.N.T)
2008-10-12 02:41:21.860 Using the Qt painter
2008-10-12 02:41:21.861 JoystickMenuClient Error: Joystick disabled - Failed to read /home/till/.mythtv/joystickmenurc
2008-10-12 02:41:21.861 lirc init success using configuration file: /home/till/.mythtv/lircrc
2008-10-12 02:41:22.129 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-10-12 02:41:22.180 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-12 02:41:22.255 Registering Internal as a media playback plugin.
2008-10-12 02:41:22.321 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-12 02:41:22.351 Failed to run 'cdrecord --scanbus'
2008-10-12 02:41:22.354 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-12 02:41:22.357 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-12 02:41:22.417 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-10-12 02:41:22.536 No theme dir: /home/till/.mythtv/themes/G.A.N.T
2008-10-12 02:41:25.694 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:41:25.695 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:41:26.306 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:41:26.307 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:42:04.428 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:42:04.428 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:42:10.266 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:42:10.266 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:42:20.435 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:42:20.435 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:42:21.275 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:42:21.276 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:42:23.576 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-12 02:42:23.576 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-10-12 02:42:28.803 Deleting UPnP client...

```

the log of the master backend is

```


2008-10-12 03:07:30.865 Using runtime prefix = /usr
2008-10-12 03:07:30.922 Empty LocalHostName.
2008-10-12 03:07:30.955 Using localhost value of till-media
2008-10-12 03:07:31.191 New DB connection, total: 1
2008-10-12 03:07:31.199 Connected to database 'mythconverg' at host: localhost
2008-10-12 03:07:31.202 Closing DB connection named 'DBManager0'
2008-10-12 03:07:31.204 Connected to database 'mythconverg' at host: localhost
2008-10-12 03:07:31.224 New DB connection, total: 2
2008-10-12 03:07:31.229 Connected to database 'mythconverg' at host: localhost
2008-10-12 03:07:31.307 Current Schema Version: 1214
Starting up as the master server.
2008-10-12 03:07:31.564 New DB connection, total: 3
2008-10-12 03:07:31.569 Connected to database 'mythconverg' at host: localhost
2008-10-12 03:07:31.575 New DB connection, total: 4
2008-10-12 03:07:31.582 Connected to database 'mythconverg' at host: localhost
2008-10-12 03:07:32.396 DVBChan(2:0) Warning: Your frequency setting (11836500) is out of range. (min/max:950000/2150000)
2008-10-12 03:07:32.594 New DB scheduler connection
2008-10-12 03:07:32.617 Connected to database 'mythconverg' at host: localhost
2008-10-12 03:07:32.906 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-10-12 03:07:32.918 Main::Registering HttpStatus Extension
2008-10-12 03:07:32.976 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-10-12 03:07:32.977 Enabled verbose msgs:  important general
2008-10-12 03:07:33.000 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-12 03:07:35.749 Reschedule requested for id -1.
2008-10-12 03:07:35.921 Scheduled 0 items in 0.2 = 0.07 match + 0.10 place
2008-10-12 03:07:36.045 Seem to be woken up by USER
2008-10-12 03:08:52.749 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-10-12 03:08:52.777 Expiring 0 MBytes for 18501 @ Sun Oct 12 03:04:53 2008 => Unbekannt
2008-10-12 03:08:52.783 Expiring 3 MBytes for 18501 @ Sun Oct 12 03:04:55 2008 => Unbekannt
2008-10-12 03:10:25.988 Reschedule requested for id -1.
2008-10-12 03:10:26.017 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-10-12 03:11:15.860 MainServer::HandleAnnounce Monitor
2008-10-12 03:11:15.864 adding: till-media as a client (events: 0)
2008-10-12 03:11:15.866 MainServer::HandleAnnounce Monitor
2008-10-12 03:11:15.867 adding: till-media as a client (events: 1)

```

the name off the 2nd front end is keller-media. I think i have to set up the master backend for the frontend but i dont know where :confused:

---

### Post by newlinux on 2008-10-11
Make sure in your master backend setup you are using the real IP of the machine, not the localhost (127.0.0.1) in mythtv-setup. Then in your frontend make sure it is pointing the IP of your backend. And of course make sure the db passwords match... Right now your logs indicate your remote frontend is looking for a backend on localhost.

---

