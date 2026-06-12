---
title: "MythBackend process goes defunct when trying to use it"
date: 2008-03-19
forum: Mythbuntu
---

### Post by s73v3r on 2008-03-19
So I'm trying to get Mythtv installed on my Xubuntu install, and the community wiki suggested that I install Mythbuntu-desktop. So I did, and got everything installed and set up. Then I went to Mythtv-frontend to try and watch tv, and after selecting "Watch TV", I get a black screen for a little while, and then it kicks me back to the menu. A check of the backend process shows that it has gone defunct.

```
 professor@professor:~$ ps -ef | grep defunct
mythtv    6595     1  0 02:28 ?        00:00:02 [mythbackend] <defunct>

```

After trolling the forums, I've found that a common troubleshooting tool is to check out the MythTV log. Here it is.
```

2008-03-19 02:20:51.324 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-19 02:20:51.324 Enabled verbose msgs:  important general
2008-03-19 02:20:51.327 AutoExpire: CalcParams(): Max required Free Space: 1.0 G
B w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-03-19 02:20:51.331 Failed to bind port 6543. Exiting.
2008-03-19 02:24:46.672 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 02:24:47.564 Empty LocalHostName.
2008-03-19 02:24:47.595 Using localhost value of professor
2008-03-19 02:24:47.699 New DB connection, total: 1
2008-03-19 02:24:47.709 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:24:47.712 Closing DB connection named 'DBManager0'
2008-03-19 02:24:47.714 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:24:47.718 New DB connection, total: 2
2008-03-19 02:24:47.719 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:24:47.753 Current Schema Version: 1214
Starting up as the master server.
2008-03-19 02:24:48.380 New DB connection, total: 3
2008-03-19 02:24:48.395 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-03-19 02:24:50.086 Main::Registering HttpStatus Extension
2008-03-19 02:24:50.204 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-19 02:24:50.206 Enabled verbose msgs:  important general
2008-03-19 02:24:50.222 AutoExpire: CalcParams(): Max required Free Space: 1.0 G
B w/freq: 15 min
2008-03-19 02:24:58.907 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/li
b/mythtv/videos:
2008-03-19 02:24:59.032 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-03-19 02:25:24.104 MainServer::HandleAnnounce Monitor
2008-03-19 02:25:24.117 adding: professor as a client (events: 0)
2008-03-19 02:25:24.119 MainServer::HandleAnnounce Monitor
2008-03-19 02:25:24.121 adding: professor as a client (events: 1)
2008-03-19 02:25:56.343 MainServer::HandleAnnounce Monitor
2008-03-19 02:25:56.347 adding: Zoidberg.local as a client (events: 0)
2008-03-19 02:25:56.350 MainServer::HandleAnnounce Monitor
2008-03-19 02:25:56.353 adding: Zoidberg.local as a client (events: 1)
2008-03-19 02:26:08.731 AutoExpire: CalcParams(): Max required Free Space: 1.0 G
B w/freq: 15 min
2008-03-19 02:26:37.566 Reloading backend settings
2008-03-19 02:27:10.408 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown e
ncoder: 1
2008-03-19 02:27:12.112 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown e
ncoder: 1
2008-03-19 02:27:13.488 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown e
ncoder: 1
2008-03-19 02:28:13.958 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 02:28:14.367 Empty LocalHostName.
2008-03-19 02:28:14.368 Using localhost value of professor
2008-03-19 02:28:14.385 New DB connection, total: 1
2008-03-19 02:28:14.392 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:28:14.394 Closing DB connection named 'DBManager0'
2008-03-19 02:28:14.396 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:28:14.399 New DB connection, total: 2
2008-03-19 02:28:14.401 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:28:14.405 Current Schema Version: 1214
Starting up as the master server.
2008-03-19 02:28:14.421 New DB connection, total: 3
2008-03-19 02:28:14.423 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:28:14.479 New DB scheduler connection
2008-03-19 02:28:14.486 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:28:15.732 Main::Registering HttpStatus Extension
2008-03-19 02:28:15.741 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-19 02:28:15.742 Enabled verbose msgs:  important general
2008-03-19 02:28:15.745 AutoExpire: CalcParams(): Max required Free Space: 1.0 G
B w/freq: 15 min
2008-03-19 02:28:15.855 MainServer::HandleAnnounce Monitor
2008-03-19 02:28:15.860 adding: professor as a client (events: 0)
2008-03-19 02:28:15.862 MainServer::HandleAnnounce Monitor
2008-03-19 02:28:15.863 adding: professor as a client (events: 1)
2008-03-19 02:28:17.525 Reschedule requested for id -1.
2008-03-19 02:28:17.559 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-03-19 02:28:17.569 Seem to be woken up by USER
2008-03-19 02:28:24.524 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/li
b/mythtv/videos:
2008-03-19 02:28:24.530 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-03-19 02:28:26.813 MainServer::HandleAnnounce Monitor
2008-03-19 02:28:26.817 adding: Zoidberg.local as a client (events: 0)
2008-03-19 02:28:26.820 MainServer::HandleAnnounce Monitor
2008-03-19 02:28:26.821 adding: Zoidberg.local as a client (events: 1)
2008-03-19 02:28:26.833 MainServer::HandleAnnounce Playback
2008-03-19 02:28:26.847 adding: Zoidberg.local as a client (events: 0)
2008-03-19 02:28:26.859 TVRec(1): Changing from None to WatchingLiveTV
2008-03-19 02:28:26.866 TVRec(1): HW Tuner: 1->1
2008-03-19 02:28:28.059 NVR(/dev/video0): Unknown video codec.  Please go into t
he TV Settings, Recording Profiles and setup the four 'Software Encoders' profil
es.  Assuming RTjpeg for now.
2008-03-19 02:28:28.064 NVR(/dev/video0) Error: Unknown audio codec
2008-03-19 02:28:28.079 AutoExpire: CalcParams(): Max required Free Space: 2.0 G
B w/freq: 15 min
2008-03-19 02:28:28.169 MainServer::HandleAnnounce Playback
2008-03-19 02:28:28.173 adding: Zoidberg.local as a client (events: 0)
2008-03-19 02:28:28.177 MainServer::HandleAnnounce FileTransfer
2008-03-19 02:28:28.178 adding: Zoidberg.local as a remote file transfer
2008-03-19 02:29:34.504 AutoExpire: CalcParams(): Max required Free Space: 2.0 G
B w/freq: 15 min
2008-03-19 02:29:44.411 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 02:29:44.432 Empty LocalHostName.
2008-03-19 02:29:44.433 Using localhost value of professor
2008-03-19 02:29:44.454 New DB connection, total: 1
2008-03-19 02:29:44.461 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:29:44.464 Closing DB connection named 'DBManager0'
2008-03-19 02:29:44.466 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:29:44.469 New DB connection, total: 2
2008-03-19 02:29:44.470 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:29:44.474 Current Schema Version: 1214
Starting up as the master server.
2008-03-19 02:29:44.489 New DB connection, total: 3
2008-03-19 02:29:44.491 Connected to database 'mythconverg' at host: localhost
2008-03-19 02:29:44.526 New DB scheduler connection
2008-03-19 02:29:44.527 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2008-03-19 02:29:44.538 MediaServer::HttpServer Create Error
2008-03-19 02:29:44.540 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-19 02:29:44.540 Enabled verbose msgs:  important general
2008-03-19 02:29:44.543 AutoExpire: CalcParams(): Max required Free Space: 1.0 G
B w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-03-19 02:29:44.547 Failed to bind port 6543. Exiting.

```

At this point, I have no idea what to do. Can someone help me fix this, or tell me how to completely remove any scrap of MythTv and  Mythbuntu-desktop from my system, while leaving all the other stuff I had (Xubuntu-desktop) so I can try to install MythTV another way.

---

