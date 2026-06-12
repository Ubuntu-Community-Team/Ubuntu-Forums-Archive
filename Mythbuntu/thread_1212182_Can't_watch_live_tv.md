---
title: "Can't watch live tv"
date: 2009-07-13
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-07-13
When I try to watch live TV the screen just goes blank. This is on a fresh install.
the frontend log reported the following:

Starting mythfrontend.real..
2009-07-13 09:02:12.067 New DB connection, total: 2
2009-07-13 09:02:12.067 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 09:02:12.068 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-07-13 09:02:12.068 Enabled verbose msgs:  important general
2009-07-13 09:02:12.283 No theme dir: /home/shaw/.mythtv/themes/Mythbuntu-8.04
2009-07-13 09:02:12.284 Primary screen 0.
2009-07-13 09:02:12.285 Using screen 0, 1360x768 at 0,0
2009-07-13 09:02:12.285 No theme dir: /home/shaw/.mythtv/themes/Mythbuntu-8.04
2009-07-13 09:02:12.285 Switching to square mode (Mythbuntu-8.04)
2009-07-13 09:02:12.298 Using the Qt painter
2009-07-13 09:02:12.299 JoystickMenuClient Error: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
2009-07-13 09:02:12.300 lirc init success using configuration file: /home/shaw/.mythtv/lircrc
2009-07-13 09:02:12.809 Specified base font 'medium' does not exist for font clock
2009-07-13 09:02:12.809 Specified base font 'medium' does not exist for font small
2009-07-13 09:02:12.809 Specified base font 'medium' does not exist for font medium
2009-07-13 09:02:12.809 Specified base font 'medium' does not exist for font large
2009-07-13 09:02:12.810 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-07-13 09:02:12.859 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-07-13 09:02:12.877 Registering Internal as a media playback plugin.
2009-07-13 09:02:12.922 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-07-13 09:02:12.937 Failed to run 'cdrecord --scanbus'
2009-07-13 09:02:12.942 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-07-13 09:02:12.944 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-07-13 09:02:12.961 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-07-13 09:02:12.993 No theme dir: /home/shaw/.mythtv/themes/Mythbuntu-8.04
2009-07-13 09:02:17.358 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2009-07-13 09:02:17.436 Connecting to backend server: 192.168.2.2:6543 (try 1 of 5)
2009-07-13 09:02:17.437 Using protocol version 40
2009-07-13 09:02:25.422 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2009-07-13 09:02:29.547 TV: Attempting to change from None to WatchingLiveTV
2009-07-13 09:05:38.545 RemoteEncoder::openControlSocket(): Connection timed out.
2009-07-13 09:05:38.546 GetEntryAt(-1) failed.
2009-07-13 09:05:38.547 EntryToProgram(0@Wed Dec 31 16:00:00 1969) failed to get pginfo
2009-07-13 09:05:38.547 TV Error: LiveTV not successfully started
2009-07-13 09:05:38.547 TV Error: LiveTV not successfully started
2009-07-13 09:05:38.666 TV: Deleting TV Chain in destructor
2009-07-13 09:05:38.668 DPMS Deactivated 
2009-07-13 09:05:38.668 DPMS Reactivated.

the syslog reported:

Jul 13 09:01:15 myth-hybrid lircd-0.8.4a[2567]: removed client
Jul 13 09:02:12 myth-hybrid lircd-0.8.4a[2567]: accepted new client on /dev/lircd
Jul 13 09:02:12 myth-hybrid lircd-0.8.4a[2567]: could not get file information for /dev/lirc0
Jul 13 09:02:12 myth-hybrid lircd-0.8.4a[2567]: default_init(): No such file or directory 
Jul 13 09:02:12 myth-hybrid lircd-0.8.4a[2567]: Failed to initialize hardware

What do I need to do to correct this?

Thanks,
Trev

---

### Post by tgm4883 on 2009-07-13
Please post your backend logs from
```
/var/log/mythtv/mythbackend.log
```

---

### Post by trevs.bronco on 2009-07-13
OK here is the backend log, i didn't post it earlier as i did not see any entries from when I tried to watch live TV.

Since i first posted i tried removing one of my capture cards to see if it would make a difference. The result is that when I deleted all capture cards and then tried to reinstall the remaining card their is no probed information found, so I am unsure of the settings to manually enter.


```
2009-07-13 08:22:49.370 Using runtime prefix = /usr
2009-07-13 08:22:49.393 Empty LocalHostName.
2009-07-13 08:22:49.396 Using localhost value of myth-hybrid
2009-07-13 08:22:49.398 Testing network connectivity to 192.168.2.2
2009-07-13 08:22:49.409 New DB connection, total: 1
2009-07-13 08:22:49.414 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 08:22:49.417 Closing DB connection named 'DBManager0'
2009-07-13 08:22:49.419 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 08:22:49.422 New DB connection, total: 2
2009-07-13 08:22:49.425 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 08:22:49.427 Current Schema Version: 1214
Running as a slave backend.
2009-07-13 08:22:49.437 TVRec(5) Error: Problem finding starting channel, setting to default of '3'.
2009-07-13 08:22:49.440 ChannelBase(5) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2009-07-13 08:22:49.445 TVRec(6) Error: Problem finding starting channel, setting to default of '3'.
2009-07-13 08:22:49.447 ChannelBase(6) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-07-13 09:01:18.412 Using runtime prefix = /usr
2009-07-13 09:01:18.563 Empty LocalHostName.
2009-07-13 09:01:18.565 Using localhost value of myth-hybrid
2009-07-13 09:01:18.568 Testing network connectivity to 192.168.2.2
2009-07-13 09:01:18.588 New DB connection, total: 1
2009-07-13 09:01:18.596 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 09:01:18.598 Closing DB connection named 'DBManager0'
2009-07-13 09:01:18.600 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 09:01:18.604 New DB connection, total: 2
2009-07-13 09:01:18.606 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 09:01:18.608 Current Schema Version: 1214
Running as a slave backend.
2009-07-13 09:01:18.618 New DB connection, total: 3
2009-07-13 09:01:18.620 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 09:01:19.441 Main::Registering HttpStatus Extension
2009-07-13 09:01:20.774 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-13 09:01:20.775 Enabled verbose msgs:  important general
2009-07-13 09:01:21.780 Connecting to master server: 192.168.2.2:6543
2009-07-13 09:01:21.785 Connected successfully
2009-07-13 09:01:51.794 MythSocket(1965060:12): readStringList: Error, timeout.
2009-07-13 09:01:51.838 adding: myth-hybrid as a slave backend server
2009-07-13 09:01:51.845 MythSocket(1932b60:-1): writeStringList: Error, socket went unconnected.
2009-07-13 09:01:58.304 MainServer::HandleAnnounce Monitor
2009-07-13 09:01:58.307 adding: myth-hybrid as a client (events: 0)
2009-07-13 09:01:58.309 MainServer::HandleAnnounce Monitor
2009-07-13 09:01:58.310 adding: myth-hybrid as a client (events: 1)
2009-07-13 09:02:17.437 MainServer::HandleAnnounce Monitor
2009-07-13 09:02:17.439 adding: myth-hybrid as a client (events: 0)
2009-07-13 09:02:17.441 MainServer::HandleAnnounce Monitor
2009-07-13 09:02:17.442 adding: myth-hybrid as a client (events: 1)
2009-07-13 10:26:42.625 Using runtime prefix = /usr
2009-07-13 10:26:42.648 Empty LocalHostName.
2009-07-13 10:26:42.650 Using localhost value of myth-hybrid
2009-07-13 10:26:42.653 Testing network connectivity to 192.168.2.2
2009-07-13 10:26:42.663 New DB connection, total: 1
2009-07-13 10:26:42.668 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:26:42.671 Closing DB connection named 'DBManager0'
2009-07-13 10:26:42.673 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:26:42.675 New DB connection, total: 2
2009-07-13 10:26:42.678 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:26:42.681 Current Schema Version: 1214
Running as a slave backend.
2009-07-13 10:26:42.689 New DB connection, total: 3
2009-07-13 10:26:42.691 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:26:43.410 Main::Registering HttpStatus Extension
2009-07-13 10:26:43.413 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-13 10:26:43.415 Enabled verbose msgs:  important general
2009-07-13 10:26:44.419 Connecting to master server: 192.168.2.2:6543
2009-07-13 10:26:44.421 Connected successfully
2009-07-13 10:27:14.431 MythSocket(7fae84009420:12): readStringList: Error, timeout.
2009-07-13 10:27:14.435 adding: myth-hybrid as a slave backend server
2009-07-13 10:27:14.440 MythSocket(7fae840094e0:-1): writeStringList: Error, socket went unconnected.
2009-07-13 10:28:04.993 Using runtime prefix = /usr
2009-07-13 10:28:05.128 Empty LocalHostName.
2009-07-13 10:28:05.129 Using localhost value of myth-hybrid
2009-07-13 10:28:05.133 Testing network connectivity to 192.168.2.2
2009-07-13 10:28:05.149 New DB connection, total: 1
2009-07-13 10:28:05.163 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:28:05.165 Closing DB connection named 'DBManager0'
2009-07-13 10:28:05.167 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:28:05.170 New DB connection, total: 2
2009-07-13 10:28:05.173 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:28:05.176 Current Schema Version: 1214
Running as a slave backend.
2009-07-13 10:28:05.185 New DB connection, total: 3
2009-07-13 10:28:05.189 Connected to database 'mythconverg' at host: 192.168.2.2
2009-07-13 10:28:05.809 Main::Registering HttpStatus Extension
2009-07-13 10:28:05.810 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-13 10:28:05.811 Enabled verbose msgs:  important general
2009-07-13 10:28:06.816 Connecting to master server: 192.168.2.2:6543
2009-07-13 10:28:06.817 Connected successfully
2009-07-13 10:28:36.821 MythSocket(7fa5c4009400:12): readStringList: Error, timeout.
2009-07-13 10:28:36.827 adding: myth-hybrid as a slave backend server
2009-07-13 10:28:36.832 MythSocket(7fa5c40094c0:-1): writeStringList: Error, socket went unconnected.
2009-07-13 10:29:47.868 MainServer::HandleAnnounce Monitor
2009-07-13 10:29:47.870 adding: myth-hybrid as a client (events: 0)
2009-07-13 10:29:47.872 MainServer::HandleAnnounce Monitor
2009-07-13 10:29:47.873 adding: myth-hybrid as a client (events: 1)
2009-07-13 10:29:47.875 Reloading backend settings
2009-07-13 11:04:36.718 Using runtime prefix = /usr
2009-07-13 11:04:36.778 Empty LocalHostName.
2009-07-13 11:04:36.781 Using localhost value of myth-hybrid
2009-07-13 11:04:36.811 Testing network connectivity to 192.168.2.2
2009-07-13 11:04:36.870 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-07-13 11:04:36.885 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
....2009-07-13 11:04:37.071 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
..........................................................................
2009-07-13 11:04:39.003 UPnPautoconf() - No UPnP backends found
2009-07-13 11:04:39.031 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name:  
[console is not interactive, using default '']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [S5PS8Ixt]  
[console is not interactive, using default 'S5PS8Ixt']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-07-13 11:04:39.165 Writing settings file /home/mythtv/.mythtv/mysql.txt
2009-07-13 11:04:39.555 New DB connection, total: 1
2009-07-13 11:04:39.568 Closing DB connection named 'DBManager0'
2009-07-13 11:04:39.574 Deleting UPnP client...
2009-07-13 11:04:39.590 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-07-13 11:04:39.958 New DB connection, total: 2
2009-07-13 11:04:40.102 Current Schema Version: (none)
2009-07-13 11:04:40.303 DataDirectProcessor::FixProgramIDs() -- begin
2009-07-13 11:04:40.368 New DB DataDirect connection
2009-07-13 11:04:40.432 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2009-07-13 11:04:40.753 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2009-07-13 11:04:40.902 DataDirectProcessor::FixProgramIDs() -- end
2009-07-13 11:04:40.985 DBUtil Error: Unable to determine MySQL version.
2009-07-13 11:04:41.043 DB Error (DBUtil Querying DBMS version):
Query was:

No error type from QSqlError?  Strange...
2009-07-13 11:04:41.066 ERROR: Unable to determine MySQL version.
2009-07-13 11:04:41.080 Couldn't upgrade database to new schema
2009-07-13 11:08:47.872 Using runtime prefix = /usr
2009-07-13 11:08:47.897 DBHostName is not set in mysql.txt
2009-07-13 11:08:47.898 Assuming localhost
2009-07-13 11:08:47.900 Empty LocalHostName.
2009-07-13 11:08:47.901 Using localhost value of myth-hybrid
2009-07-13 11:08:47.908 New DB connection, total: 1
2009-07-13 11:08:47.914 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:08:47.916 Closing DB connection named 'DBManager0'
2009-07-13 11:08:47.919 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:08:47.921 New DB connection, total: 2
2009-07-13 11:08:47.923 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:08:47.928 Current Schema Version: 1214
Running as a slave backend.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-07-13 11:08:47.938 New DB connection, total: 3
2009-07-13 11:08:48.007 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:08:48.570 Main::Registering HttpStatus Extension
2009-07-13 11:08:48.576 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-13 11:08:48.577 Enabled verbose msgs:  important general
2009-07-13 11:08:49.582 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:08:49.584 Connected successfully
2009-07-13 11:09:19.585 MythSocket(e0f400:12): readStringList: Error, timeout.
2009-07-13 11:09:19.608 adding: myth-hybrid as a slave backend server
2009-07-13 11:09:19.608 Unknown socket closing
2009-07-13 11:09:19.613 MythSocket(e14420:-1): writeStringList: Error, socket went unconnected.
2009-07-13 11:09:19.617 MythSocket(e15ab0:-1): writeStringList: Error, socket went unconnected.
2009-07-13 11:09:20.619 Unknown socket closing
2009-07-13 11:09:20.622 MythSocket(e15c80:-1): writeStringList: Error, socket went unconnected.
2009-07-13 11:09:22.961 MainServer::HandleAnnounce Monitor
2009-07-13 11:09:22.970 adding: myth-hybrid as a client (events: 0)
2009-07-13 11:09:22.972 MainServer::HandleAnnounce Monitor
2009-07-13 11:09:22.973 adding: myth-hybrid as a client (events: 1)
2009-07-13 11:10:40.867 Using runtime prefix = /usr
2009-07-13 11:10:40.944 DBHostName is not set in mysql.txt
2009-07-13 11:10:40.959 Assuming localhost
2009-07-13 11:10:40.993 Empty LocalHostName.
2009-07-13 11:10:41.003 Using localhost value of myth-hybrid
2009-07-13 11:10:41.123 New DB connection, total: 1
2009-07-13 11:10:41.166 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:10:41.197 Closing DB connection named 'DBManager0'
2009-07-13 11:10:41.203 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:10:41.205 New DB connection, total: 2
2009-07-13 11:10:41.208 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:10:41.282 Current Schema Version: 1214
Running as a slave backend.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-07-13 11:10:41.330 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-07-13 11:10:41.340 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-07-13 11:10:41.905 Main::Registering HttpStatus Extension
2009-07-13 11:10:41.929 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-07-13 11:10:41.937 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-13 11:10:42.148 Enabled verbose msgs:  important general
2009-07-13 11:10:43.311 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:10:43.592 Connection to master server timed out.
2009-07-13 11:10:44.594 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:10:44.611 Connection to master server timed out.
2009-07-13 11:10:45.639 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:10:45.687 Connection to master server timed out.
2009-07-13 11:10:46.693 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:10:46.703 Connection to master server timed out.
2009-07-13 11:10:47.779 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:10:48.123 Connected successfully
2009-07-13 11:11:19.231 MythSocket(7f1408004e70:10): readStringList: Error, timeout.
2009-07-13 11:11:19.260 adding: myth-hybrid as a slave backend server
2009-07-13 11:11:19.265 MythSocket(7f1408007410:-1): writeStringList: Error, socket went unconnected.
2009-07-13 11:14:17.112 MainServer::HandleAnnounce Monitor
2009-07-13 11:14:17.115 adding: myth-hybrid as a client (events: 0)
2009-07-13 11:14:17.117 MainServer::HandleAnnounce Monitor
2009-07-13 11:14:17.118 adding: myth-hybrid as a client (events: 1)
2009-07-13 11:15:25.200 Using runtime prefix = /usr
2009-07-13 11:15:25.224 DBHostName is not set in mysql.txt
2009-07-13 11:15:25.225 Assuming localhost
2009-07-13 11:15:25.227 Empty LocalHostName.
2009-07-13 11:15:25.236 Using localhost value of myth-hybrid
2009-07-13 11:15:25.246 New DB connection, total: 1
2009-07-13 11:15:25.251 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:15:25.254 Closing DB connection named 'DBManager0'
2009-07-13 11:15:25.256 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:15:25.258 New DB connection, total: 2
2009-07-13 11:15:25.261 Connected to database 'mythconverg' at host: localhost
2009-07-13 11:15:25.264 Current Schema Version: 1214
Running as a slave backend.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-07-13 11:15:25.849 Main::Registering HttpStatus Extension
2009-07-13 11:15:25.851 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-07-13 11:15:25.853 Enabled verbose msgs:  important general
2009-07-13 11:15:26.857 Connecting to master server: 192.168.2.2:6543
2009-07-13 11:15:26.858 Connected successfully
2009-07-13 11:15:56.864 MythSocket(146e390:11): readStringList: Error, timeout.
2009-07-13 11:15:56.870 adding: myth-hybrid as a slave backend server
2009-07-13 11:15:56.875 MythSocket(1472130:-1): writeStringList: Error, socket went unconnected.
```

---

### Post by tgm4883 on 2009-07-13
what type of card do you have, and what release of mythbuntu are you using?

---

### Post by trevs.bronco on 2009-07-13
I have a pair of Hauppauge PVR 150 cards and it is the 9.04 Jaunty release

---

### Post by trevs.bronco on 2009-07-13
I have managed to get the capture card detected by physically removing it and reinstalling it but I still can't watch tv. I also tried to record and was unable to because it would not save the recordings when I scheduled them.


Trev

---

### Post by tgm4883 on 2009-07-14
What type of tuner did you set the cards up as in mythtv?

---

### Post by trevs.bronco on 2009-07-15
they are set up as IVTV, this is the only seting I could use which would allow the channels to scan in input connections

Trev

---

### Post by trevs.bronco on 2009-07-15
Well after my third re-install I am finally able to watch TV, now if I could only hear it I would be truly happy.:guitar:

Trev

---

### Post by tgm4883 on 2009-07-15
> **trevs.bronco said:**
> Well after my third re-install I am finally able to watch TV, now if I could only hear it I would be truly happy.:guitar:

Trev

Are you able to test sound outside of MythTV? Perhaps with an audio file?

---

### Post by nogat_bits on 2009-07-16
how you make it work ?? were you reinstalled just MythTV or Linux ? how you configure the Tuner card ? accidentally i have the same capture card just like you but i cant watch TV until now

---

### Post by trevs.bronco on 2009-07-16
unfortunately it is back to square one for me. after i exited from liveTV i decided it would be a good time to install all the updates. near the end of this process the whole system crashed and some how corrupted the BIOS. I have managed to reinstall the BIOS but the system won't boot from the hard drive, but it will boot from the live CD so tomorrow i will attempt to install it again. some things that have worked are installing the cards as IVTV and creating the LiveTV and DBbackup folders and making sure the  /var/lib/mythtv/ and child folders belong to the mythtv group and have R/W permisions before configuring the backend.

Wish me luck,

Trev

---

### Post by SiHa on 2009-07-16
](*,)

Good Luck

---

### Post by uncle hammy on 2009-07-16
> **trevs.bronco said:**
> unfortunately it is back to square one for me. after i exited from liveTV i decided it would be a good time to install all the updates. near the end of this process the whole system crashed and some how corrupted the BIOS. I have managed to reinstall the BIOS but the system won't boot from the hard drive
Honestly, it sounds like you have bigger issues than you think...

Updating the OS ruined you BIOS?  IMHO that shouldn't ever happen unless you have a bad Motherboard, or perhaps a bad HD, but my first looking would be the MOBO.

---

### Post by trevs.bronco on 2009-07-16
I have been using this MOBO for about a year now with no real issues, Wouldn't mind switching to one with on board video that supports HDMI, maybe this is a good excuse to make the switch. I did manage to install the OS again this morning, and will try to configure the backend when I get home from work.
 
Trev

---

### Post by trevs.bronco on 2009-07-17
It Lives!
 
The Bios may not have been the issue. I saw this message in the Post Log > Powernow-K8: Your BIOS does not provide ACPI_ objects in a way that LINUX understands. Please report this to LINUX ACPI_ Maintainers.  and there where a couple of error codes which I googled with no results. I think this may always be there, I just never saw them before as they flashed by the screen. The only issue I had on instal was no sound. I fixed that by down grading the nvidia drives the 180 driver was installed, I think I have the 173 in there now. Now all I have left to do is load all my media from my old hard drives and the it is on to getting my new remote frontend up and running.
Thanks for the support,
 
Trev

---

