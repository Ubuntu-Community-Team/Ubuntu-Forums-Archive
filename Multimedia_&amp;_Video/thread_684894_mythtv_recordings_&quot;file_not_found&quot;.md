---
title: "mythtv recordings &quot;file not found&quot;"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by strattonbrazil on 2008-02-01
I've been using MythTV to watch television lately and recently have wanted to get into recording shows while I'm gone like TiVO.  I tried setting it up and it said everything was ready to go for an episode, and when I came back to play it, it gave me "file not found".  I tried again another time and got the same thing.  The thing is, I really don't know how to debug the thing.  

I'm using Ubuntu 7.10 and have the front-end/back-end on the same machine.  I'm posting a bit from my logs.  Thanks.  

Front-End
```
Starting mythfrontend.real..
2008-02-01 13:40:04.517 Current Schema Version: 1160
2008-02-01 13:40:04.548 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-02-01 13:40:04.548 Enabled verbose msgs:  important general
2008-02-01 13:40:05.369 Total desktop dim: 1680x1050, with 1 screen[s].
2008-02-01 13:40:05.370 Using screen 0, 1680x1050 at 0,0
2008-02-01 13:40:05.370 Switching to square mode (G.A.N.T.)
2008-02-01 13:40:05.417 Using the Qt painter
2008-02-01 13:40:05.815 Joystick disabled.
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2008-02-01 13:40:06.802 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2008-02-01 13:40:06.830 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-02-01 13:40:06.883 Registering Internal as a media playback plugin.
2008-02-01 13:40:06.959 Registering MythDVD DVD Media Handler as a media handler ext()
2008-02-01 13:40:06.960 Registering MythDVD VCD Media Handler as a media handler ext()
2008-02-01 13:40:15.451 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2008-02-01 13:40:15.798 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-02-01 13:40:15.819 Using protocol version 31
2008-02-01 13:40:16.122 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:16.471 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:16.971 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:17.471 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:17.971 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:18.471 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:18.971 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:18.977 PlaybackBox::play(): Error, /var/lib/mythtv/recordings/1654_20080131180500.mpg file not 
found
2008-02-01 13:40:18.980 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:19.471 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:19.971 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:20.471 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:20.618 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:20.624 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
2008-02-01 13:40:20.971 Error: File '/var/lib/mythtv/recordings/1654_20080131180500.mpg' missing.
Starting mythfrontend.real..
2008-02-01 13:44:36.976 Current Schema Version: 1160
2008-02-01 13:44:36.977 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-02-01 13:44:36.977 Enabled verbose msgs:  important general
2008-02-01 13:44:37.111 Total desktop dim: 1680x1050, with 1 screen[s].
2008-02-01 13:44:37.111 Using screen 0, 1680x1050 at 0,0
2008-02-01 13:44:37.111 Switching to square mode (G.A.N.T.)
2008-02-01 13:44:37.122 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2008-02-01 13:44:37.407 Joystick disabled.
2008-02-01 13:44:38.151 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2008-02-01 13:44:38.168 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-02-01 13:44:38.194 Registering Internal as a media playback plugin.
2008-02-01 13:44:38.202 Registering MythDVD DVD Media Handler as a media handler ext()
2008-02-01 13:44:38.203 Registering MythDVD VCD Media Handler as a media handler ext()
2008-02-01 13:44:48.349 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml

```
Back-End
```
2008-02-01 13:40:15.819 MainServer::HandleAnnounce Monitor
2008-02-01 13:40:15.841 adding: atlas as a client (events: 0)
2008-02-01 13:40:15.842 MainServer::HandleAnnounce Monitor
2008-02-01 13:40:15.842 adding: atlas as a client (events: 1)
2008-02-01 13:42:40.480 Using runtime prefix = /usr
2008-02-01 13:42:40.505 New DB connection, total: 1
2008-02-01 13:42:40.510 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:42:40.512 Current Schema Version: 1160
Starting up as the master server.
2008-02-01 13:42:40.525 New DB connection, total: 2
2008-02-01 13:42:40.526 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:42:40.528 EITHelper: localtime offset -7:00:00 
2008-02-01 13:42:40.532 New DB connection, total: 3
2008-02-01 13:42:40.533 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:42:40.539 DVBChan(0) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
2008-02-01 13:42:40.549 New DB scheduler connection
2008-02-01 13:42:40.555 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:42:41.905 Main::Registering HttpStatus Extension
2008-02-01 13:42:41.906 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-01 13:42:41.907 Enabled verbose msgs:  important general
2008-02-01 13:42:41.907 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-02-01 13:42:41.909 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-02-01 13:42:42.564 Reschedule requested for id -1.
2008-02-01 13:42:42.594 Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2008-02-01 13:42:42.598 Seem to be woken up by USER
2008-02-01 13:44:24.038 Using runtime prefix = /usr
2008-02-01 13:44:24.088 New DB connection, total: 1
2008-02-01 13:44:24.092 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:44:24.094 Current Schema Version: 1160
Starting up as the master server.
2008-02-01 13:44:24.100 New DB connection, total: 2
2008-02-01 13:44:24.101 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:44:24.103 EITHelper: localtime offset -7:00:00 
2008-02-01 13:44:24.111 New DB connection, total: 3
2008-02-01 13:44:24.112 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:44:24.137 DVBChan(0) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
2008-02-01 13:44:24.146 New DB scheduler connection
2008-02-01 13:44:24.147 Connected to database 'mythconverg' at host: localhost
2008-02-01 13:44:25.485 Main::Registering HttpStatus Extension
2008-02-01 13:44:25.487 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-01 13:44:25.487 Enabled verbose msgs:  important general
2008-02-01 13:44:25.488 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-02-01 13:44:25.489 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-02-01 13:44:26.175 Reschedule requested for id -1.
2008-02-01 13:44:26.190 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2008-02-01 13:44:26.193 Seem to be woken up by USER
2008-02-01 13:44:48.623 MainServer::HandleAnnounce Monitor
2008-02-01 13:44:48.628 adding: atlas as a client (events: 0)
2008-02-01 13:44:48.629 MainServer::HandleAnnounce Monitor
2008-02-01 13:44:48.631 adding: atlas as a client (events: 1)
2008-02-01 13:46:37.347 Reschedule requested for id 2.
2008-02-01 13:46:37.364 Scheduled 1 items in 0.0 = 0.01 match + 0.01 place
2008-02-01 13:50:02.526 TVRec(3): Changing from None to RecordingOnly
2008-02-01 13:50:04.058 TVRec(3): HW Tuner: 3->3

```

---

