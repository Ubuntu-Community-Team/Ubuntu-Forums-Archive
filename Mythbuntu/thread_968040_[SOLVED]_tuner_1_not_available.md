---
title: "[SOLVED] tuner 1 not available"
date: 2008-11-02
forum: Mythbuntu
---

### Post by TVtalker on 2008-11-02
Hi,
I´m a newbie at linux and mythbuntu.

Since an update to new cannel frequenzes I have problems with live-tv. It isn´t working since that:
- deleted the tv-card
- deleted the videosources
- configered both new
- channelsearch worked well
- everything looked well in backendsetup

But now in frontend watching tv isn´t working. after klick on watch-tv there is a short flash an then i see the menu again - no tv.

With Kaffeine everything works well - so I think it´s a problem with mythbuntu.

has anyone an idea where the problem is? i´m totaly lost.

Thanks

--

Mythbuntu 8.04
Satelco EasyWatch DVB-C

---

### Post by ian dobson on 2008-11-02
Hi,

Do you see anything interesting in the backend log file (/var/log/mythtv/mythbackend.log).

I've written a small script that checks the mythtv configuration. Maybe it'll help you find the problem.

To get/use the script just go to the terminal and type.

```

wget http://www.planet-ian.com/MythTV/CheckMythDB.txt
mv CheckMythDB.txt CheckMythDB.pl
chmod +x CheckMythDB.pl
CheckMythDB.pl -a

```

Regards
Ian Dobson

---

### Post by TVtalker on 2008-11-03
I tried your code as you explained. But it did not work. What have I done wrong?

wget [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)
--19:12:49--  [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt)
           => `CheckMythDB.txt'
Resolving [www.planet-ian.com](www.planet-ian.com)... 213.188.236.119
Connecting to [www.planet-ian.com|213.188.236.119|:80](www.planet-ian.com|213.188.236.119|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23.583 (23K) [text/plain]

100%[====================================>] 23.583        97.99K/s             

19:12:50 (97.93 KB/s) - `CheckMythDB.txt' saved [23583/23583]

detlef@MythbuntuRecorder:~$ mv CheckMythDB.txt CheckMythDB.pl
detlef@MythbuntuRecorder:~$ chmod +x CheckMythDB.pl
detlef@MythbuntuRecorder:~$ CheckMythDB.pl -a
bash: CheckMythDB.pl: command not found

---

### Post by ian dobson on 2008-11-03
Hi,

Sorry the command is

./CheckMythDB.pl -a

regards
Ian Dobson

---

### Post by TVtalker on 2008-11-03
Hi Ian,

ok thanks. now it works. but for me everything looks fine.

[--].Checking configuration for host 'VideoZentrale'
[OK].Found 1 video sources
[OK].Videosource (1) 'Satelco' has a EPG source defined (eitonly)
[OK].Found 1 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 11 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex

---

### Post by TVtalker on 2008-11-03
here is my mythbackend.log

2008-11-03 19:52:13.918 Using runtime prefix = /usr
2008-11-03 19:52:13.921 Empty LocalHostName.
2008-11-03 19:52:13.922 Using localhost value of MythbuntuRecorder
2008-11-03 19:52:13.931 New DB connection, total: 1
2008-11-03 19:52:13.934 Connected to database 'mythconverg' at host: localhost
2008-11-03 19:52:13.936 Closing DB connection named 'DBManager0'
2008-11-03 19:52:13.937 Connected to database 'mythconverg' at host: localhost
2008-11-03 19:52:13.939 New DB connection, total: 2
2008-11-03 19:52:13.950 Connected to database 'mythconverg' at host: localhost
2008-11-03 19:52:13.958 Current Schema Version: 1214
Starting up as the master server.
2008-11-03 19:52:13.972 New DB scheduler connection
2008-11-03 19:52:13.973 Connected to database 'mythconverg' at host: localhost
2008-11-03 19:52:15.199 Main::Registering HttpStatus Extension
2008-11-03 19:52:15.200 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-03 19:52:15.200 Enabled verbose msgs:  important general
2008-11-03 19:52:15.202 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-03 19:52:15.570 MainServer::HandleAnnounce Monitor
2008-11-03 19:52:15.573 adding: VideoZentrale as a client (events: 0)
2008-11-03 19:52:15.574 MainServer::HandleAnnounce Monitor
2008-11-03 19:52:15.574 adding: VideoZentrale as a client (events: 1)
2008-11-03 19:52:16.976 Reschedule requested for id -1.
2008-11-03 19:52:16.982 Invalid search key in recordid 67
2008-11-03 19:52:17.000 Scheduled 2 items in 0.0 = 0.01 match + 0.02 place
2008-11-03 19:52:17.005 Seem to be woken up by USER
2008-11-03 19:52:18.007 I'm idle now... shutdown will occur in 120 seconds.
2008-11-03 19:52:23.996 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-03 19:52:23.997 UPnpMedia: BuildMediaMap Done. Found 0 objects

---

### Post by ian dobson on 2008-11-03
Hi,

I'm not sure whats the problem.

Do you see anything in your backend.log file (/var/log/mythtv/mythbackend.log).

The card should work, I have 2 DVB-C cards in my backend one's a Satelco EasyWatch DVB-C and it just works.
The only thing I did was to extend the tuning delay abit in mythtv-setup.

Regards
Ian Dobson

---

### Post by TVtalker on 2008-11-03
Hi,

I´ve no idea where the problem is. For me the backend.log looks normal. But I´m not an expert in it.

Is there somewhere else a config file for the tuner? Is it possible i did something wrong when I deleted my tuner-card before I made the new configuration?

Hope we will find some answers.
Thanks for helping!

---

### Post by ian dobson on 2008-11-03
Hi,

And what do you see in your frontend log file?

Regards
Ian Dobson

---

### Post by TVtalker on 2008-11-04
Hi,

here my mythwelcom.log:

2008-11-04 16:55:58.649 Using runtime prefix = /usr
2008-11-04 16:55:58.704 XScreenSaver support enabled
2008-11-04 16:55:58.704 DPMS is active.
2008-11-04 16:55:58.704 Using localhost value of VideoZentrale
2008-11-04 16:55:58.713 New DB connection, total: 1
2008-11-04 16:55:58.717 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 16:55:58.718 Closing DB connection named 'DBManager0'
2008-11-04 16:55:58.719 Primary screen 0.
2008-11-04 16:55:58.720 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 16:55:58.721 Using screen 0, 1440x900 at 0,0
2008-11-04 16:55:58.781 Primary screen 0.
2008-11-04 16:55:58.782 Using screen 0, 1440x900 at 0,0
2008-11-04 16:55:59.640 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-04 16:55:59.671 Switching to square mode (Retro)
2008-11-04 16:55:59.783 Using the Qt painter
2008-11-04 16:55:59.783 lirc_init failed for mythtv, see preceding messages
2008-11-04 16:55:59.784 JoystickMenuClient Error: Joystick disabled - Failed to read /home/detlef/.mythtv/joystickmenurc
2008-11-04 16:56:01.289 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2008-11-04 16:56:01.575 Starting mythlcdserver
2008-11-04 16:56:02.078 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-11-04 16:56:02.610 New DB connection, total: 2
2008-11-04 16:56:02.612 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 16:56:02.616 Connecting to backend server: 192.168.178.32:6543 (try 1 of 5)
2008-11-04 16:56:02.617 Using protocol version 40
2008-11-04 16:56:03.013 mythshutdown --startup returned: 1
2008-11-04 19:03:04.045 Using runtime prefix = /usr
2008-11-04 19:03:04.568 XScreenSaver support enabled
2008-11-04 19:03:04.569 DPMS is active.
2008-11-04 19:03:04.569 Using localhost value of VideoZentrale
2008-11-04 19:03:04.578 New DB connection, total: 1
2008-11-04 19:03:04.581 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 19:03:04.583 Closing DB connection named 'DBManager0'
2008-11-04 19:03:04.584 Primary screen 0.
2008-11-04 19:03:04.585 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 19:03:04.586 Using screen 0, 1440x900 at 0,0
2008-11-04 19:03:04.591 New DB connection, total: 2
2008-11-04 19:03:04.592 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-04 19:03:04.594 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-04 19:03:04.594 Enabled verbose msgs:  important general
2008-11-04 19:03:04.604 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-11-04 19:03:06.142 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-04 19:03:06.143 Primary screen 0.
2008-11-04 19:03:06.144 Using screen 0, 1440x900 at 0,0
2008-11-04 19:03:06.145 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-04 19:03:06.146 Switching to square mode (Retro)
2008-11-04 19:03:06.160 Using the Qt painter
2008-11-04 19:03:06.161 lirc_init failed for mythtv, see preceding messages
2008-11-04 19:03:06.161 JoystickMenuClient Error: Joystick disabled - Failed to read /home/detlef/.mythtv/joystickmenurc
2008-11-04 19:03:07.236 Loading from: /usr/share/mythtv/themes/Retro/base.xml
2008-11-04 19:03:07.354 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-04 19:03:07.418 Registering Internal as a media playback plugin.
2008-11-04 19:03:07.643 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-04 19:03:07.990 Failed to run 'cdrecord --scanbus'
2008-11-04 19:03:07.995 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-04 19:03:07.999 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-04 19:03:08.041 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-11-04 19:03:08.284 Connecting to backend server: 192.168.178.32:6543 (try 1 of 5)
2008-11-04 19:03:08.285 Using protocol version 40
2008-11-04 19:03:08.296 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-04 19:03:59.495 Deleting UPnP client...

What does this mean? Is here a problem?:
2008-11-04 19:03:07.990 Failed to run 'cdrecord --scanbus'
2008-11-04 19:03:07.995 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-04 19:03:07.999 Failed to run 'cdrecord --scanbus -dev=ATAPI'

---

### Post by ian dobson on 2008-11-04
Hi,

I think I can see what the problem is :)

Connected to database 'mythconverg' at host: 127.0.0.1
Connecting to backend server: 192.168.178.32:6543 (try 1 of 5)

Are you running a seperate frontend/backend? try setting both the backend and sql IP address to the same system as your backend.

Gruss aus Basel
Ian Dobson

---

### Post by TVtalker on 2008-11-04
Hi,

that sounds good :-) 
I´m running both frontend and backend on the same machine. But I havn´t understood what to do exactly. Do you have a more detailled tipp for me?

Danke und
Grüße aus Baden

---

### Post by ian dobson on 2008-11-04
Hi,

First run mythtv-setup and set the IP addresses for your backend and the SQL server to 127.0.0.1 then in mythfrontend set the backend address and sql server also to 127.0.0.1.

Sorry I can't be more specific at the moment. I don't have access to my myth system at the moment.

Gruss aus Basel
Ian Dobson

---

### Post by TVtalker on 2008-11-05
Hi,

I changed the IPs but now I have some other strange things. It looks like there is a problem with mythfilldb. Live TV is not working.

Here are the masterbackend-log with some errors. Is there something wrong with the port behind the IP?

2008-11-05 19:39:50.962 Using runtime prefix = /usr
2008-11-05 19:39:51.035 Empty LocalHostName.
2008-11-05 19:39:51.035 Using localhost value of MythbuntuRecorder
2008-11-05 19:39:51.076 New DB connection, total: 1
2008-11-05 19:39:51.080 Connected to database 'mythconverg' at host: localhost
2008-11-05 19:39:51.081 Closing DB connection named 'DBManager0'
2008-11-05 19:39:51.082 Connected to database 'mythconverg' at host: localhost
2008-11-05 19:39:51.084 New DB connection, total: 2
2008-11-05 19:39:51.084 Connected to database 'mythconverg' at host: localhost
2008-11-05 19:39:51.087 Current Schema Version: 1214
Running as a slave backend.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-05 19:39:51.176 New DB connection, total: 3
2008-11-05 19:39:51.256 Connected to database 'mythconverg' at host: localhost
2008-11-05 19:39:52.000 Main::Registering HttpStatus Extension
2008-11-05 19:39:52.001 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-05 19:39:52.001 Enabled verbose msgs:  important general
2008-11-05 19:39:53.024 Connecting to master server: 127.0.0.1:6543
2008-11-05 19:39:53.026 Connected successfully
2008-11-05 19:40:23.026 MythSocket(7f24900100e0:12): readStringList: Error, timeout.
2008-11-05 19:40:23.031 adding: MythbuntuRecorder as a slave backend server
QDateTime::fromString: Parameter out of range
2008-11-05 19:40:23.031 Unknown socket closing
2008-11-05 19:40:23.051 MythSocket(7f2490014880:-1): writeStringList: Error, socket went unconnected.
2008-11-05 19:40:23.211 MythSocket(7f249000dbf0:-1): writeStringList: Error, socket went unconnected.
2008-11-05 19:40:27.598 Unknown socket closing
2008-11-05 19:40:27.599 MythSocket(7f2490010c70:-1): writeStringList: Error, socket went unconnected.

---

### Post by TVtalker on 2008-11-05
now it looks better. the connection to the masterbackend looks good. For me it seems there is a problem with mythfilldatabase. if I understand it right there is now capture card saved in the database. but why not? I have configured it.

Some ideas?

2008-11-05 21:09:29.788 Using runtime prefix = /usr
2008-11-05 21:09:29.793 Empty LocalHostName.
2008-11-05 21:09:29.795 Using localhost value of MythbuntuRecorder
2008-11-05 21:09:29.815 New DB connection, total: 1
2008-11-05 21:09:29.819 Connected to database 'mythconverg' at host: localhost
2008-11-05 21:09:29.820 Closing DB connection named 'DBManager0'
2008-11-05 21:09:29.821 Connected to database 'mythconverg' at host: localhost
2008-11-05 21:09:29.823 New DB connection, total: 2
2008-11-05 21:09:29.824 Connected to database 'mythconverg' at host: localhost
2008-11-05 21:09:29.827 Current Schema Version: 1214
Running as a slave backend.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-05 21:09:30.414 Main::Registering HttpStatus Extension
2008-11-05 21:09:30.415 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-05 21:09:30.415 Enabled verbose msgs:  important general
2008-11-05 21:09:31.419 Connecting to master server: 127.0.0.1:6543
2008-11-05 21:09:31.420 Connected successfully

---

### Post by TVtalker on 2008-11-05
Here the Backendlog when I start the frontend. Strange for me is, that now tuner 3 is not available. Before the changes it was tuner 1.

2008-11-05 21:22:07.469 MainServer::HandleAnnounce Monitor
2008-11-05 21:22:07.471 adding: VideoZentrale as a client (events: 0)
2008-11-05 21:22:07.472 MainServer::HandleAnnounce Monitor
2008-11-05 21:22:07.472 adding: VideoZentrale as a client (events: 1)
2008-11-05 21:22:07.473 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:22:07.832 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:22:15.216 MainServer::HandleAnnounce Playback
2008-11-05 21:22:15.218 adding: VideoZentrale as a client (events: 0)
2008-11-05 21:22:15.219 MainServer::HandleAnnounce Monitor
2008-11-05 21:22:15.219 adding: VideoZentrale as a client (events: 1)
2008-11-05 21:22:48.137 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:22:48.793 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:23:06.770 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:23:09.773 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:23:23.446 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:23:23.849 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:23:39.546 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
2008-11-05 21:23:41.601 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3

---

### Post by TVtalker on 2008-11-05
ok, here the last status for today. the two tuners are gone - now the old message "tuner 1 not available" is there again.

the backendlog when starting the frontend
2008-11-05 22:18:17.762 I'm idle now... shutdown will occur in 120 seconds.
2008-11-05 22:18:28.004 MainServer::HandleAnnounce Monitor
2008-11-05 22:18:28.007 adding: VideoZentrale as a client (events: 0)
2008-11-05 22:18:28.007 MainServer::HandleAnnounce Monitor
2008-11-05 22:18:28.008 adding: VideoZentrale as a client (events: 1)
2008-11-05 22:18:28.009 Reschedule requested for id -1.
2008-11-05 22:18:28.019 Invalid search key in recordid 67
2008-11-05 22:18:28.039 Scheduled 4 items in 0.0 = 0.01 match + 0.02 place
2008-11-05 22:18:29.043 I'm idle now... shutdown will occur in 120 seconds.
2008-11-05 22:18:44.582 MainServer::HandleAnnounce Playback
2008-11-05 22:18:44.583 adding: VideoZentrale as a client (events: 0)
2008-11-05 22:18:44.584 MainServer::HandleAnnounce Monitor
2008-11-05 22:18:44.585 adding: VideoZentrale as a client (events: 1)
2008-11-05 22:18:59.045 I'm idle now... shutdown will occur in 120 seconds.

and the frontendlog:
2008-11-05 22:18:27.837 Grabbing EPG data using command:
/usr/bin/mythfilldatabase &
2008-11-05 22:18:27.974 Using runtime prefix = /usr
2008-11-05 22:18:27.974 Using localhost value of VideoZentrale
2008-11-05 22:18:27.983 New DB connection, total: 1
2008-11-05 22:18:27.986 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-05 22:18:27.987 Closing DB connection named 'DBManager0'
2008-11-05 22:18:27.988 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-05 22:18:27.992 New DB connection, total: 2
2008-11-05 22:18:27.992 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-05 22:18:27.993 Source 1 configured to use only the broadcasted guide data. Skipping.
2008-11-05 22:18:27.994 Data fetching complete.
2008-11-05 22:18:27.994 Adjusting program database end times.
2008-11-05 22:18:27.995     0 replacements made
2008-11-05 22:18:27.995 Marking generic episodes.
2008-11-05 22:18:27.995     Found 0
2008-11-05 22:18:27.995 Marking repeats.
2008-11-05 22:18:27.996     Found 0
2008-11-05 22:18:27.997 Unmarking new episode rebroadcast repeats.
2008-11-05 22:18:27.997     Found 0
2008-11-05 22:18:27.997 Marking episode first showings.
2008-11-05 22:18:27.997     Found 0
2008-11-05 22:18:27.997 Marking episode last showings.
2008-11-05 22:18:27.997     Found 0
2008-11-05 22:18:27.999 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-11-05 22:18:28.003 Connecting to backend server: 192.168.178.32:6543 (try 1 of 5)
2008-11-05 22:18:28.003 Using protocol version 40
2008-11-05 22:18:28.009 Received a remote 'Clear Cache' request
2008-11-05 22:18:28.010 Received a remote 'Clear Cache' request
2008-11-05 22:18:28.011 mythfilldatabase run complete.
2008-11-05 22:18:28.011 DataDirect: Deleting temporary files
2008-11-05 22:18:29.053 MythWelcome received a SCHEDULE_CHANGE event
2008-11-05 22:18:41.826 Using runtime prefix = /usr
2008-11-05 22:18:42.349 XScreenSaver support enabled
2008-11-05 22:18:42.349 DPMS is active.
2008-11-05 22:18:42.350 Using localhost value of VideoZentrale
2008-11-05 22:18:42.358 New DB connection, total: 1
2008-11-05 22:18:42.361 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-05 22:18:42.363 Closing DB connection named 'DBManager0'
2008-11-05 22:18:42.364 Primary screen 0.
2008-11-05 22:18:42.365 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-05 22:18:42.366 Using screen 0, 1440x900 at 0,0
2008-11-05 22:18:42.374 New DB connection, total: 2
2008-11-05 22:18:42.374 Connected to database 'mythconverg' at host: 127.0.0.1
2008-11-05 22:18:42.377 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-05 22:18:42.377 Enabled verbose msgs:  important general
2008-11-05 22:18:42.388 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-11-05 22:18:43.280 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-05 22:18:43.281 Primary screen 0.
2008-11-05 22:18:43.281 Using screen 0, 1440x900 at 0,0
2008-11-05 22:18:43.283 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-05 22:18:43.283 Switching to square mode (Retro)
2008-11-05 22:18:43.297 Using the Qt painter
2008-11-05 22:18:43.298 lirc_init failed for mythtv, see preceding messages
2008-11-05 22:18:43.298 JoystickMenuClient Error: Joystick disabled - Failed to read /home/detlef/.mythtv/joystickmenurc
2008-11-05 22:18:44.235 Loading from: /usr/share/mythtv/themes/Retro/base.xml
2008-11-05 22:18:44.334 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-05 22:18:44.374 Registering Internal as a media playback plugin.
2008-11-05 22:18:44.431 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-05 22:18:44.465 Failed to run 'cdrecord --scanbus'
2008-11-05 22:18:44.470 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-05 22:18:44.474 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-05 22:18:44.507 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-11-05 22:18:44.581 Connecting to backend server: 192.168.178.32:6543 (try 1 of 5)
2008-11-05 22:18:44.582 Using protocol version 40
2008-11-05 22:18:44.587 No theme dir: /home/detlef/.mythtv/themes/Retro
2008-11-05 22:18:57.899 Deleting UPnP client...

any ideas where the problem could be? live tv is not working.
thanks for your help!!

---

### Post by TVtalker on 2008-11-09
Any Ideas?

Thanks for help?

---

### Post by TVtalker on 2008-11-09
Any Ideas?

Thanks for help?

---

### Post by ian dobson on 2008-11-09
Hi,

Could it be that your host name is changing?

Try going into mythtv-setup, delete all your tuners. Save and exit. tun setup again and add your cards again and link them back to the video sources.

Then maybe run my script and check that all your tuners are there.

Regards
Ian Dobson

---

### Post by TVtalker on 2008-11-11
I updated the tuner card and linked it to the videosources. I did it three times, but live tv is not working. Here is what I see with your script. Evwerything looks normal from my opinion:
[--].Try ./CheckMythDB.pl -H for help
[--] Using HostName 'VideoZentrale', DatabaseHost '127.0.0.1', SQLUserName 'mythtv', SQLPassword 'xxxxx'
[--].Checking configuration for host 'VideoZentrale'
[OK].Found 1 video sources
[OK].Videosource (1) 'Satelco' has a EPG source defined (eitonly)
[OK].Found 2 card inputs for Videoinput 1
[--].Checking start channel for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 199 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0755 (rwx r-x r-x)
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].24 dtv_multiplex entries do not have a valid channel
[!!].Channel ANIXE HD has 0 programs in EPG.No EPG data
[!!].Channel 3000 5 has 0 programs in EPG.No EPG data
[!!].Channel 3001 4 has 0 programs in EPG.No EPG data
[OK].All EPG entries have a valid channel
[OK].Found 2 storage groups for 'VideoZentrale'
[OK].Storage group 'Default' exists in file system at (/home/mythtv/Media/)
[OK].Storage group 'LiveTV' exists in file system at (/var/lib/mythtv/recordings/)

Thanks for helping!

---

### Post by TVtalker on 2008-11-11
It looks like there are two cards installed in the database. But I have only one card in my computer. In the setup-menu I can not find a second dvb-card to delete.

Some ideas?

---

### Post by TVtalker on 2009-01-06
I solved the problem :P :
- somehow I defined in the backend-setup a special name for the frontend, when I changed the channel configuration. After that I always got the message in the frontend "Tuner 1 not available". In the backend the tuner was detected right and the channelscan worked. But watching LiveTV at the frontend wasn´t possible.
- everytime I deleted the tunercard and add it up again, this tunercard was registered in the myth-database for the new frontend-name. The problem was, that the tuner was installed at the backend
- I deleted the special name for the frontend, added the tuner again and now the tuner is available at the frontend and working correctly.

Can someone tell me, why the tuner was registered for the new frontend-name (Frontend and backend are running on the same machine)? Can someone explain me, how the configuration of mythbuntu backend, frontend and database works? Would be interesting.

Thanks for all your help!!:P

---

