---
title: "Connection to Master Backend Server has gone away..."
date: 2009-10-03
forum: Mythbuntu
---

### Post by SiHa on 2009-10-03
...is it running?

I've had a stable system for over a year, with only the occasional glitch. Recently though, and more since the DVB-T Retune on 30th (maybe a coincidence ...?). I've been getting the above message. It seems to happen only after the system has automatically woken up @ 7am, as it does every morning. If I reboot, all is OK for the rest of the day. Three days out of the last five it's done this in the morning.

Thing is, ```
ps -A|grep myth
```returns mythbackend, mythfrontend.real and myth_watch. The last is a script that I picked up form here with the idea of restarting the backend server if it stops for some reason.

But the backend server doesn't actually appear to be stopped. Both the combined BE/FE, and the remote FE complain. 
As it affects the BE/FE, I'm guessing that it's something to do with a network service stopping or something, so that the FE loses the BE that's on the same machine. I have no idea how to diagnose is from here though.

Logs don't appear to show anything meaningful.

Here's the Backend.log, from startup until I rebooted.

```
2009-10-03 07:22:50.153 Reschedule requested for id -1.
2009-10-03 07:22:50.860 Scheduled 115 items in 0.7 = 0.04 match + 0.67 place
2009-10-03 07:26:56.992 Reschedule requested for id -1.
2009-10-03 07:26:57.719 Scheduled 115 items in 0.7 = 0.04 match + 0.68 place
2009-10-03 07:31:11.986 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-03 07:31:12.113 UPnpMedia: BuildMediaMap Done. Found 97 objects
2009-10-03 07:31:17.972 Reschedule requested for id -1.
2009-10-03 07:31:18.692 Scheduled 115 items in 0.7 = 0.04 match + 0.68 place
2009-10-03 07:32:16.940 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-03 07:34:12.437 Reschedule requested for id -1.
2009-10-03 07:34:13.427 Scheduled 115 items in 1.0 = 0.31 match + 0.68 place
2009-10-03 07:38:51.051 Reschedule requested for id -1.
2009-10-03 07:38:51.784 Scheduled 115 items in 0.7 = 0.03 match + 0.70 place
2009-10-03 07:42:48.585 Reschedule requested for id -1.
2009-10-03 07:42:49.307 Scheduled 115 items in 0.7 = 0.04 match + 0.68 place
2009-10-03 07:46:02.522 Reschedule requested for id -1.
2009-10-03 07:46:03.232 Scheduled 115 items in 0.7 = 0.03 match + 0.67 place
2009-10-03 07:47:16.982 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-03 07:50:12.232 Reschedule requested for id -1.
2009-10-03 07:50:13.160 Scheduled 115 items in 0.9 = 0.27 match + 0.66 place
2009-10-03 07:54:52.900 Reschedule requested for id -1.
2009-10-03 07:54:53.592 Scheduled 115 items in 0.7 = 0.04 match + 0.66 place
2009-10-03 08:00:51.942 Reschedule requested for id -1.
2009-10-03 08:00:52.667 Scheduled 115 items in 0.7 = 0.04 match + 0.69 place
2009-10-03 08:01:14.126 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-03 08:01:14.253 UPnpMedia: BuildMediaMap Done. Found 97 objects
2009-10-03 08:02:17.023 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-03 08:03:41.276 Reschedule requested for id -1.
2009-10-03 08:03:41.990 Scheduled 115 items in 0.7 = 0.04 match + 0.67 place
2009-10-03 08:07:15.900 Reschedule requested for id -1.
2009-10-03 08:07:16.622 Scheduled 115 items in 0.7 = 0.03 match + 0.68 place
2009-10-03 08:11:03.218 Reschedule requested for id -1.
2009-10-03 08:11:03.933 Scheduled 115 items in 0.7 = 0.04 match + 0.67 place
2009-10-03 08:14:24.256 Reschedule requested for id -1.
2009-10-03 08:14:24.966 Scheduled 115 items in 0.7 = 0.03 match + 0.67 place
2009-10-03 08:17:17.064 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-03 08:17:56.502 Reschedule requested for id -1.
2009-10-03 08:17:57.198 Scheduled 115 items in 0.7 = 0.04 match + 0.66 place
2009-10-03 08:21:03.345 Reschedule requested for id -1.
2009-10-03 08:21:04.064 Scheduled 115 items in 0.7 = 0.03 match + 0.68 place
2009-10-03 08:25:00.237 Reschedule requested for id -1.
2009-10-03 08:25:00.947 Scheduled 115 items in 0.7 = 0.03 match + 0.67 place
2009-10-03 08:28:35.436 Reschedule requested for id -1.
2009-10-03 08:28:36.131 Scheduled 115 items in 0.7 = 0.03 match + 0.66 place
2009-10-03 08:31:20.267 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-03 08:31:20.389 UPnpMedia: BuildMediaMap Done. Found 97 objects
2009-10-03 08:32:17.107 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-03 08:32:28.048 Reschedule requested for id -1.
2009-10-03 08:32:28.770 Scheduled 115 items in 0.7 = 0.04 match + 0.68 place
2009-10-03 09:01:26.402 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-10-03 09:01:26.525 UPnpMedia: BuildMediaMap Done. Found 97 objects
2009-10-03 09:02:37.740 MainServer::HandleAnnounce Playback
2009-10-03 09:02:37.744 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:02:37.746 MainServer::HandleAnnounce Monitor
2009-10-03 09:02:37.746 adding: frontend-desktop as a client (events: 1)
2009-10-03 09:03:29.127 MainServer::HandleAnnounce Monitor
2009-10-03 09:03:29.130 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:04:41.297 MainServer::HandleAnnounce Monitor
2009-10-03 09:04:41.297 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:04:48.300 MainServer::HandleAnnounce Monitor
2009-10-03 09:04:48.300 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:05:31.438 MainServer::HandleAnnounce Monitor
2009-10-03 09:05:31.440 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:05:38.449 MainServer::HandleAnnounce Monitor
2009-10-03 09:05:38.452 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:05:48.813 MainServer::HandleAnnounce Monitor
2009-10-03 09:05:48.815 adding: frontend-desktop as a client (events: 0)
2009-10-03 09:18:46.693 MainServer::HandleAnnounce Monitor
2009-10-03 09:18:46.698 adding: mythbox-desktop as a client (events: 0)
2009-10-03 09:19:22.358 MainServer::HandleAnnounce Monitor
2009-10-03 09:19:22.359 adding: mythbox-desktop as a client (events: 0)
2009-10-03 09:20:39.990 Using runtime prefix = /usr, libdir = /usr/lib
2009-10-03 09:20:40.135 Empty LocalHostName.
2009-10-03 09:20:40.154 Using localhost value of mythbox-desktop
2009-10-03 09:20:40.541 Cannot find default UPnP backend
2009-10-03 09:20:40.679 New DB connection, total: 1
2009-10-03 09:20:40.687 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:40.708 Closing DB connection named 'DBManager0'
2009-10-03 09:20:40.709 Deleting UPnP client...
2009-10-03 09:20:41.055 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:41.151 New DB connection, total: 2
2009-10-03 09:20:41.352 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:41.400 Current Schema Version: 1214
Starting up as the master server.
2009-10-03 09:20:41.684 New DB connection, total: 3
2009-10-03 09:20:41.686 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:44.184 New DB scheduler connection
2009-10-03 09:20:44.205 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:45.285 Main::Registering HttpStatus Extension
2009-10-03 09:20:45.297 mythbackend version: 0.21.20080304-1 www.mythtv.org
```

Anyone got any ideas? This is killing the WAF.

TIA,

Simonon

---

### Post by dmfrey on 2009-10-03
Are you using a firewire capture card.  I recently have been getting a similar issue when a firewire connection can't establish a lock on an SD channel.

---

### Post by SiHa on 2009-10-03
Sorry to hear that, but, no Firewire here...

Thanks anyway.

---

