---
title: "No live tv"
date: 2009-01-20
forum: Mythbuntu
---

### Post by buddylind on 2009-01-20
Hello all. I have been trying to get Mythbuntu to work for two weeks now and I just get more frustrated every day. What happens is that when I try to watch TV I get a blank screen for a second then I get returned to the menu. When I try to enter the Mythbuntu Logs the system freezes and I have to reboot. I am using a Hauppauge hd-5500 tuner card and running Intrepid. I have tryed using different configurations for the capture cards with the sme result. I have included some logs to look at. Hope it helps. Any help that anyone can give is greatly appreciated. Thank you.

backend.log
2009-01-19 16:34:56.448 Empty LocalHostName.
2009-01-19 16:34:56.476 Using localhost value of new-york
2009-01-19 16:34:56.581 New DB connection, total: 1
2009-01-19 16:34:56.672 Connected to database 'mythconverg' at host: localhost
2009-01-19 16:34:56.836 Closing DB connection named 'DBManager0'
2009-01-19 16:34:56.847 Connected to database 'mythconverg' at host: localhost
2009-01-19 16:34:56.851 New DB connection, total: 2
2009-01-19 16:34:56.950 Connected to database 'mythconverg' at host: localhost
2009-01-19 16:34:57.078 Current Schema Version: 1214
Starting up as the master server.
2009-01-19 16:34:57.747 New DB connection, total: 3
2009-01-19 16:34:58.151 Connected to database 'mythconverg' at host: localhost
2009-01-19 16:34:58.494 Channel(/dev/video0) Error: GetCurrentChannelNum(116): Failed to find Channel
2009-01-19 16:34:58.553 Channel(/dev/video0)::TuneTo(116): Error, failed to find channel.
2009-01-19 16:34:58.644 New DB scheduler connection
2009-01-19 16:34:58.664 Connected to database 'mythconverg' at host: localhost
2009-01-19 16:34:58.915 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-19 16:34:59.215 Main::Registering HttpStatus Extension
2009-01-19 16:34:59.378 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 16:34:59.435 Enabled verbose msgs:  important general
2009-01-19 16:34:59.578 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 16:35:01.775 Reschedule requested for id -1.
2009-01-19 16:35:02.833 Scheduled 0 items in 1.1 = 0.64 match + 0.42 place
2009-01-19 16:35:02.952 Seem to be woken up by USER
2009-01-19 16:36:18.773 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 16:51:18.809 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 17:13:28.361 Using runtime prefix = /usr
2009-01-19 17:13:28.376 Empty LocalHostName.
2009-01-19 17:13:28.378 Using localhost value of new-york
2009-01-19 17:13:28.394 New DB connection, total: 1
2009-01-19 17:13:28.417 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:13:28.421 Closing DB connection named 'DBManager0'
2009-01-19 17:13:28.423 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:13:28.426 New DB connection, total: 2
2009-01-19 17:13:28.428 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:13:28.434 Current Schema Version: 1214
Starting up as the master server.
2009-01-19 17:13:28.459 New DB connection, total: 3
2009-01-19 17:13:28.462 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:13:28.640 Channel(/dev/video0) Error: GetCurrentChannelNum(116): Failed to find Channel
2009-01-19 17:13:28.642 Channel(/dev/video0)::TuneTo(116): Error, failed to find channel.
2009-01-19 17:13:28.888 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-19 17:13:28.889 DVBChan(2:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-19 17:13:28.905 New DB scheduler connection
2009-01-19 17:13:28.907 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:13:28.931 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-19 17:13:28.932 Main::Registering HttpStatus Extension
2009-01-19 17:13:28.935 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 17:13:28.938 Enabled verbose msgs:  important general
2009-01-19 17:13:28.944 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 17:13:31.913 Reschedule requested for id -1.
2009-01-19 17:13:31.986 Scheduled 0 items in 0.1 = 0.02 match + 0.04 place
2009-01-19 17:13:32.027 Seem to be woken up by USER
2009-01-19 17:14:48.911 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 17:17:29.736 MainServer::HandleAnnounce Monitor
2009-01-19 17:17:31.986 adding: new-york as a client (events: 0)
2009-01-19 17:17:31.988 MainServer::HandleAnnounce Monitor
2009-01-19 17:17:31.989 adding: new-york as a client (events: 1)
2009-01-19 17:17:31.991 Reschedule requested for id -1.
2009-01-19 17:17:32.059 Scheduled 0 items in 0.1 = 0.03 match + 0.04 place
2009-01-19 17:18:15.146 MainServer::HandleAnnounce Monitor
2009-01-19 17:18:15.150 adding: new-york as a client (events: 0)
2009-01-19 17:18:15.152 MainServer::HandleAnnounce Monitor
2009-01-19 17:18:15.154 adding: new-york as a client (events: 1)
2009-01-19 17:18:15.165 MainServer::HandleAnnounce Playback
2009-01-19 17:18:15.190 adding: new-york as a client (events: 0)
2009-01-19 17:18:15.194 TVRec(1): Changing from None to WatchingLiveTV
2009-01-19 17:18:15.203 TVRec(1): HW Tuner: 1->1
2009-01-19 17:18:15.309 Channel(/dev/video0) Error: GetCurrentChannelNum(116): Failed to find Channel
2009-01-19 17:18:15.310 Channel(/dev/video0)::TuneTo(116): Error, failed to find channel.
2009-01-19 17:18:15.310 TVRec(1) Error: Failed to set channel to 116. Reverting to kState_None
2009-01-19 17:18:15.318 TVRec(1): Changing from WatchingLiveTV to None
2009-01-19 17:20:17.632 Using runtime prefix = /usr
2009-01-19 17:20:17.637 Empty LocalHostName.
2009-01-19 17:20:17.640 Using localhost value of new-york
2009-01-19 17:20:17.663 New DB connection, total: 1
2009-01-19 17:20:17.672 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:20:17.675 Closing DB connection named 'DBManager0'
2009-01-19 17:20:17.678 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:20:17.684 New DB connection, total: 2
2009-01-19 17:20:17.688 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:20:17.695 Current Schema Version: 1214
Starting up as the master server.
2009-01-19 17:20:17.725 New DB connection, total: 3
2009-01-19 17:20:17.728 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:20:17.876 Channel(/dev/video0) Error: GetCurrentChannelNum(116): Failed to find Channel
2009-01-19 17:20:17.877 Channel(/dev/video0)::TuneTo(116): Error, failed to find channel.
2009-01-19 17:20:18.165 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-19 17:20:18.167 DVBChan(2:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-19 17:20:18.186 New DB scheduler connection
2009-01-19 17:20:18.188 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:20:18.216 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-19 17:20:18.218 Main::Registering HttpStatus Extension
2009-01-19 17:20:18.219 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 17:20:18.227 Enabled verbose msgs:  important general
2009-01-19 17:20:18.294 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 17:20:21.195 Reschedule requested for id -1.
2009-01-19 17:20:21.227 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-01-19 17:20:21.234 Seem to be woken up by USER
2009-01-19 17:20:45.589 MainServer::HandleAnnounce Monitor
2009-01-19 17:20:45.594 adding: new-york as a client (events: 0)
2009-01-19 17:20:45.596 MainServer::HandleAnnounce Monitor
2009-01-19 17:20:45.597 adding: new-york as a client (events: 1)
2009-01-19 17:20:45.607 MainServer::HandleAnnounce Playback
2009-01-19 17:20:45.608 adding: new-york as a client (events: 0)
2009-01-19 17:20:45.614 TVRec(1): Changing from None to WatchingLiveTV
2009-01-19 17:20:45.622 TVRec(1): HW Tuner: 1->1
2009-01-19 17:20:45.725 Channel(/dev/video0) Error: GetCurrentChannelNum(116): Failed to find Channel
2009-01-19 17:20:45.726 Channel(/dev/video0)::TuneTo(116): Error, failed to find channel.
2009-01-19 17:20:45.730 TVRec(1) Error: Failed to set channel to 116. Reverting to kState_None
2009-01-19 17:20:45.734 TVRec(1): Changing from WatchingLiveTV to None
2009-01-19 17:21:38.195 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 17:36:38.233 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 17:51:38.262 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 18:06:38.289 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 18:23:06.901 Using runtime prefix = /usr
2009-01-19 18:23:06.914 Empty LocalHostName.
2009-01-19 18:23:06.917 Using localhost value of new-york
2009-01-19 18:23:06.940 New DB connection, total: 1
2009-01-19 18:23:06.953 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:23:06.957 Closing DB connection named 'DBManager0'
2009-01-19 18:23:06.960 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:23:06.964 New DB connection, total: 2
2009-01-19 18:23:06.968 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:23:06.977 Current Schema Version: 1214
Starting up as the master server.
2009-01-19 18:23:07.015 New DB connection, total: 3
2009-01-19 18:23:07.017 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:23:07.158 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-19 18:23:07.160 DVBChan(3:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-19 18:23:07.476 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-19 18:23:07.477 DVBChan(4:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-19 18:23:07.588 New DB scheduler connection
2009-01-19 18:23:07.592 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:23:07.615 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-19 18:23:07.616 Main::Registering HttpStatus Extension
2009-01-19 18:23:07.617 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 18:23:07.623 Enabled verbose msgs:  important general
2009-01-19 18:23:07.628 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 18:23:10.598 Reschedule requested for id -1.
2009-01-19 18:23:10.670 Scheduled 0 items in 0.1 = 0.03 match + 0.04 place
2009-01-19 18:23:10.680 Seem to be woken up by USER
2009-01-19 18:24:27.596 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 18:26:11.976 MainServer::HandleAnnounce Monitor
2009-01-19 18:26:12.951 adding: new-york as a client (events: 0)
2009-01-19 18:26:12.958 MainServer::HandleAnnounce Monitor
2009-01-19 18:26:12.959 adding: new-york as a client (events: 1)
2009-01-19 18:26:12.963 Reschedule requested for id -1.
2009-01-19 18:26:13.033 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2009-01-19 18:29:03.848 MainServer::HandleAnnounce Monitor
2009-01-19 18:29:03.851 adding: new-york as a client (events: 0)
2009-01-19 18:29:03.853 MainServer::HandleAnnounce Monitor
2009-01-19 18:29:03.854 adding: new-york as a client (events: 1)
2009-01-19 18:29:03.868 MainServer::HandleAnnounce Playback
2009-01-19 18:29:03.870 adding: new-york as a client (events: 0)
2009-01-19 18:29:03.876 TVRec(3): Changing from None to WatchingLiveTV
2009-01-19 18:29:03.885 TVRec(3): HW Tuner: 3->3
2009-01-19 18:29:03.892 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-19 18:29:03.894 DVBChan(3:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-19 18:29:03.898 TVRec(3) Error: Failed to set channel to 4. Reverting to kState_None
2009-01-19 18:29:03.905 TVRec(3): Changing from WatchingLiveTV to None
2009-01-19 18:39:29.404 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 18:43:10.411 MainServer::HandleAnnounce Monitor
2009-01-19 18:43:10.415 adding: new-york as a client (events: 0)
2009-01-19 18:43:10.416 MainServer::HandleAnnounce Monitor
2009-01-19 18:43:10.417 adding: new-york as a client (events: 1)
2009-01-19 18:54:29.438 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 19:09:29.471 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 19:24:29.498 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 19:39:29.608 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 19:54:29.636 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 20:09:29.681 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 20:24:29.778 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 20:39:29.826 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 20:54:29.867 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 21:09:29.941 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 21:24:29.968 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 21:39:30.017 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 21:54:30.076 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 22:09:30.139 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 22:24:30.168 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 22:39:30.194 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 22:54:30.221 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 23:09:30.246 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 23:24:30.274 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 23:39:30.302 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-19 23:54:30.329 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 00:09:30.354 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 00:24:30.381 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 00:39:30.406 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 00:54:30.433 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:09:30.460 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:24:30.485 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:39:30.514 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:54:30.540 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 02:09:30.565 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 02:24:30.592 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 02:39:30.620 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 02:54:30.646 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 03:09:30.673 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 03:24:30.702 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 03:39:30.732 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 03:54:30.758 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 04:09:30.785 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 04:24:30.815 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 04:39:30.844 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 04:54:30.875 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 05:09:30.902 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 05:24:30.931 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 05:39:30.960 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 05:54:30.988 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 06:09:31.017 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 06:24:31.048 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 06:39:31.077 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 06:54:31.103 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 07:09:31.130 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 07:24:31.159 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 07:39:31.187 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 07:54:31.215 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 08:09:31.241 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 08:24:31.267 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 08:39:31.297 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 08:54:31.324 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 08:55:48.255 MainServer::HandleAnnounce Monitor
2009-01-20 08:55:48.259 adding: new-york as a client (events: 0)
2009-01-20 08:55:48.261 MainServer::HandleAnnounce Monitor
2009-01-20 08:55:48.262 adding: new-york as a client (events: 1)
2009-01-20 08:55:48.270 MainServer::HandleAnnounce Playback
2009-01-20 08:55:48.272 adding: new-york as a client (events: 0)
2009-01-20 08:55:48.276 TVRec(3): Changing from None to WatchingLiveTV
2009-01-20 08:55:48.282 TVRec(3): HW Tuner: 3->3
2009-01-20 08:55:48.291 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-20 08:55:48.292 DVBChan(3:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-20 08:55:48.294 TVRec(3) Error: Failed to set channel to 4. Reverting to kState_None
2009-01-20 08:55:48.298 TVRec(3): Changing from WatchingLiveTV to None
2009-01-20 08:55:53.362 MainServer::HandleAnnounce Playback
2009-01-20 08:55:53.370 adding: new-york as a client (events: 0)
2009-01-20 08:55:53.377 TVRec(3): Changing from None to WatchingLiveTV
2009-01-20 08:55:53.387 TVRec(3): HW Tuner: 3->3
2009-01-20 08:55:53.393 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-20 08:55:53.394 DVBChan(3:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-20 08:55:53.398 TVRec(3) Error: Failed to set channel to 4. Reverting to kState_None
2009-01-20 08:55:53.402 TVRec(3): Changing from WatchingLiveTV to None
2009-01-20 08:57:05.293 Reschedule requested for id 0.
2009-01-20 08:57:05.452 Scheduled 0 items in 0.2 = 0.00 match + 0.16 place
2009-01-20 09:01:50.422 Using runtime prefix = /usr
2009-01-20 09:01:50.582 Empty LocalHostName.
2009-01-20 09:01:50.602 Using localhost value of new-york
2009-01-20 09:01:50.699 New DB connection, total: 1
2009-01-20 09:01:50.806 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:01:50.828 Closing DB connection named 'DBManager0'
2009-01-20 09:01:50.841 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:01:50.964 New DB connection, total: 2
2009-01-20 09:01:51.006 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:01:51.554 Current Schema Version: 1214
Starting up as the master server.
2009-01-20 09:01:52.159 New DB connection, total: 3
2009-01-20 09:01:52.387 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:01:52.746 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-20 09:01:52.821 DVBChan(3:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-20 09:01:53.063 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-20 09:01:53.203 DVBChan(4:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-20 09:01:53.595 New DB scheduler connection
2009-01-20 09:01:53.906 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:01:54.405 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-20 09:01:54.606 Main::Registering HttpStatus Extension
2009-01-20 09:01:54.609 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 09:01:54.611 Enabled verbose msgs:  important general
2009-01-20 09:01:54.644 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:01:57.094 Reschedule requested for id -1.
2009-01-20 09:01:58.003 Scheduled 0 items in 0.9 = 0.81 match + 0.10 place
2009-01-20 09:01:58.026 Seem to be woken up by USER
2009-01-20 09:03:14.083 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:03:37.474 MainServer::HandleAnnounce Monitor
2009-01-20 09:03:37.481 adding: new-york as a client (events: 0)
2009-01-20 09:03:37.483 MainServer::HandleAnnounce Monitor
2009-01-20 09:03:37.484 adding: new-york as a client (events: 1)
2009-01-20 09:03:37.493 MainServer::HandleAnnounce Playback
2009-01-20 09:03:37.524 adding: new-york as a client (events: 0)
2009-01-20 09:03:37.530 TVRec(3): Changing from None to WatchingLiveTV
2009-01-20 09:03:37.540 TVRec(3): HW Tuner: 3->3
2009-01-20 09:03:37.545 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-01-20 09:03:37.546 DVBChan(3:0) Error: SetChannelByString(4): Failed to initialize multiplex options
2009-01-20 09:03:37.547 TVRec(3) Error: Failed to set channel to 4. Reverting to kState_None
2009-01-20 09:03:37.551 TVRec(3): Changing from WatchingLiveTV to None
2009-01-20 09:07:13.395 Using runtime prefix = /usr
2009-01-20 09:07:13.417 Empty LocalHostName.
2009-01-20 09:07:13.418 Using localhost value of new-york
2009-01-20 09:07:13.440 New DB connection, total: 1
2009-01-20 09:07:13.449 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:07:13.451 Closing DB connection named 'DBManager0'
2009-01-20 09:07:13.454 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:07:13.458 New DB connection, total: 2
2009-01-20 09:07:13.460 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:07:13.469 Current Schema Version: 1214
Starting up as the master server.
2009-01-20 09:07:13.495 TVRec(5) Error: Problem finding starting channel, setting to default of '3'.
2009-01-20 09:07:13.496 Channel()::Open(): Can't open video device, error "No such file or directory"
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-20 09:07:13.536 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-20 09:07:13.537 Main::Registering HttpStatus Extension
2009-01-20 09:07:13.539 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 09:07:13.543 Enabled verbose msgs:  important general
2009-01-20 09:07:13.550 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:08:33.511 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:12:17.285 MainServer::HandleAnnounce Monitor
2009-01-20 09:12:18.995 adding: new-york as a client (events: 0)
2009-01-20 09:12:18.997 MainServer::HandleAnnounce Monitor
2009-01-20 09:12:18.999 adding: new-york as a client (events: 1)
2009-01-20 09:13:36.587 MainServer::HandleAnnounce Monitor
2009-01-20 09:13:36.588 adding: new-york as a client (events: 0)
2009-01-20 09:13:36.590 MainServer::HandleAnnounce Monitor
2009-01-20 09:13:36.592 adding: new-york as a client (events: 1)
2009-01-20 09:17:21.416 Using runtime prefix = /usr
2009-01-20 09:17:21.430 Empty LocalHostName.
2009-01-20 09:17:21.432 Using localhost value of new-york
2009-01-20 09:17:21.450 New DB connection, total: 1
2009-01-20 09:17:21.458 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:17:21.461 Closing DB connection named 'DBManager0'
2009-01-20 09:17:21.463 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:17:21.467 New DB connection, total: 2
2009-01-20 09:17:21.469 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:17:21.479 Current Schema Version: 1214
Starting up as the master server.
2009-01-20 09:17:21.506 TVRec(6) Error: Problem finding starting channel, setting to default of '3'.
2009-01-20 09:17:21.510 ChannelBase(6) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-20 09:17:21.545 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-20 09:17:21.546 Main::Registering HttpStatus Extension
2009-01-20 09:17:21.547 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 09:17:21.551 Enabled verbose msgs:  important general
2009-01-20 09:17:21.558 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:18:41.522 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:20:48.471 MainServer::HandleAnnounce Monitor
2009-01-20 09:20:50.137 adding: new-york as a client (events: 0)
2009-01-20 09:20:50.139 MainServer::HandleAnnounce Monitor
2009-01-20 09:20:50.140 adding: new-york as a client (events: 1)
2009-01-20 09:33:50.401 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 09:45:10.337 MainServer::HandleAnnounce Monitor
2009-01-20 09:45:10.340 adding: new-york as a client (events: 0)
2009-01-20 09:45:10.342 MainServer::HandleAnnounce Monitor
2009-01-20 09:45:10.343 adding: new-york as a client (events: 1)
2009-01-20 09:48:50.438 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 10:03:50.469 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 10:18:50.572 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 10:23:16.793 Using runtime prefix = /usr
2009-01-20 10:23:16.801 Empty LocalHostName.
2009-01-20 10:23:16.802 Using localhost value of new-york
2009-01-20 10:23:16.813 New DB connection, total: 1
2009-01-20 10:23:16.818 Connected to database 'mythconverg' at host: localhost
2009-01-20 10:23:16.820 Closing DB connection named 'DBManager0'
2009-01-20 10:23:16.824 Connected to database 'mythconverg' at host: localhost
2009-01-20 10:23:16.832 New DB connection, total: 2
2009-01-20 10:23:16.840 Connected to database 'mythconverg' at host: localhost
2009-01-20 10:23:16.850 Current Schema Version: 1214
Starting up as the master server.
2009-01-20 10:23:16.874 TVRec(6) Error: Problem finding starting channel, setting to default of '3'.
2009-01-20 10:23:16.875 ChannelBase(6) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-20 10:23:16.886 New DB connection, total: 3
2009-01-20 10:23:16.888 Connected to database 'mythconverg' at host: localhost
2009-01-20 10:23:16.920 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-20 10:23:16.933 Main::Registering HttpStatus Extension
2009-01-20 10:23:16.939 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 10:23:16.945 Enabled verbose msgs:  important general
2009-01-20 10:23:16.954 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 10:24:36.886 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 10:26:23.158 MainServer::HandleAnnounce Monitor
2009-01-20 10:26:25.830 adding: new-york as a client (events: 0)
2009-01-20 10:26:25.832 MainServer::HandleAnnounce Monitor
2009-01-20 10:26:25.839 adding: new-york as a client (events: 1)

frontend.log
2009-01-19 13:58:34.366 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-19 13:58:34.367 TV Error: LiveTV not successfully started
2009-01-19 13:58:34.367 TV Error: LiveTV not successfully started
2009-01-19 13:58:34.379 TV: Deleting TV Chain in destructor
2009-01-19 13:58:34.390 DPMS Deactivated 
2009-01-19 13:58:34.390 DPMS Reactivated.
2009-01-19 13:58:41.874 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-19 14:06:27.375 New DB connection, total: 2
2009-01-19 14:06:27.376 Connected to database 'mythconverg' at host: localhost
2009-01-19 14:06:27.378 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 14:06:27.378 Enabled verbose msgs:  important general
2009-01-19 14:06:28.033 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 14:06:28.035 Primary screen 0.
2009-01-19 14:06:28.036 Using screen 0, 1280x1024 at 0,0
2009-01-19 14:06:28.036 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 14:06:28.037 Switching to square mode (G.A.N.T)
2009-01-19 14:06:28.074 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-19 14:06:28.075 lirc_init failed for mythtv, see preceding messages
2009-01-19 14:06:28.076 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2009-01-19 14:06:30.505 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-19 14:06:30.634 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-19 14:06:30.742 Registering Internal as a media playback plugin.
2009-01-19 14:06:30.747 Upgrading to MythArchive schema version 1001
2009-01-19 14:06:30.795 Inserting MythFlix initial database information.
2009-01-19 14:06:30.795 Upgrading to MythFlix schema version 1000
2009-01-19 14:06:30.801 Upgrading to MythFlix schema version 1001
2009-01-19 14:06:30.956 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-19 14:06:30.969 Setting Up MythMovies Database Tables
2009-01-19 14:06:30.979 MythMovies Database Setup Complete
2009-01-19 14:06:31.085 Upgrading to MythMusic schema version 1007
2009-01-19 14:06:31.096 Upgrading to MythMusic schema version 1008
2009-01-19 14:06:31.121 Upgrading to MythMusic schema version 1009
2009-01-19 14:06:31.126 Upgrading to MythMusic schema version 1010
2009-01-19 14:06:31.136 Updating music_albumart image types
2009-01-19 14:06:31.139 Upgrading to MythMusic schema version 1011
2009-01-19 14:06:31.140 Upgrading to MythMusic schema version 1012
2009-01-19 14:06:31.146 Upgrading to MythMusic schema version 1013
2009-01-19 14:06:31.316 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-19 14:06:31.316 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-19 14:06:31.411 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-19 14:06:31.529 Upgrading to MythVideo schema version 1011
2009-01-19 14:06:31.531 Updated from old MythDVD/MythVideo schema to combined version: 1011.
2009-01-19 14:06:31.533 Upgrading to MythVideo schema version 1012
2009-01-19 14:06:31.543 Upgrading to MythVideo schema version 1013
2009-01-19 14:06:31.544 Upgrading to MythVideo schema version 1014
2009-01-19 14:06:31.551 Upgrading to MythVideo schema version 1015
2009-01-19 14:06:31.566 Upgrading to MythVideo schema version 1016
2009-01-19 14:06:31.645 Inserting MythWeather initial database information.
2009-01-19 14:06:31.645 Upgrading to MythWeather schema version 1000
2009-01-19 14:06:31.673 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 14:06:55.440 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml
2009-01-19 14:06:56.833 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-19 14:06:56.834 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-19 14:07:11.031 Loading from: /usr/share/mythtv/themes/default/appear-ui.xml
2009-01-19 14:07:34.318 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-19 14:07:34.324 Using protocol version 40
2009-01-19 14:07:34.337 Received a remote 'Clear Cache' request
2009-01-19 14:08:50.076 Received a remote 'Clear Cache' request
2009-01-19 14:09:03.883 Received a remote 'Clear Cache' request
2009-01-19 14:09:24.056 TV: Attempting to change from None to WatchingLiveTV
2009-01-19 14:09:24.059 Using protocol version 40
2009-01-19 14:09:24.193 GetEntryAt(-1) failed.
2009-01-19 14:09:24.194 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-19 14:09:24.194 TV Error: LiveTV not successfully started
2009-01-19 14:09:24.194 TV Error: LiveTV not successfully started
2009-01-19 14:09:24.203 TV: Deleting TV Chain in destructor
2009-01-19 14:09:24.213 DPMS Deactivated 
2009-01-19 14:09:24.214 DPMS Reactivated.
Destroying SipFsm object 
2009-01-19 14:09:35.003 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-19 16:28:56.645 New DB connection, total: 2
2009-01-19 16:28:56.646 Connected to database 'mythconverg' at host: localhost
2009-01-19 16:28:56.649 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 16:28:56.649 Enabled verbose msgs:  important general
2009-01-19 16:28:57.278 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 16:28:57.280 Primary screen 0.
2009-01-19 16:28:57.281 Using screen 0, 1280x1024 at 0,0
2009-01-19 16:28:57.281 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 16:28:57.282 Switching to square mode (G.A.N.T)
2009-01-19 16:28:57.323 Using the Qt painter
2009-01-19 16:28:57.324 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-19 16:28:57.324 lirc_init failed for mythtv, see preceding messages
2009-01-19 16:28:59.816 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-19 16:28:59.946 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-19 16:29:00.074 Registering Internal as a media playback plugin.
2009-01-19 16:29:00.219 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-19 16:29:00.328 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-19 16:29:00.328 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-19 16:29:00.419 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-19 16:29:00.585 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169:                                                                                                                                                                                                                  Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
                                                                                                                                                                      mythbuntu-log-grabber: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
mythfrontend.real: Fatal IO error: client killed
Starting mythfrontend.real..
2009-01-19 17:18:03.336 New DB connection, total: 2
2009-01-19 17:18:03.336 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:18:03.340 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 17:18:03.340 Enabled verbose msgs:  important general
2009-01-19 17:18:05.105 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 17:18:05.107 Primary screen 0.
2009-01-19 17:18:05.107 Using screen 0, 1280x1024 at 0,0
2009-01-19 17:18:05.108 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 17:18:05.109 Switching to square mode (G.A.N.T)
2009-01-19 17:18:05.144 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-19 17:18:05.145 lirc_init failed for mythtv, see preceding messages
2009-01-19 17:18:05.146 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2009-01-19 17:18:07.603 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-19 17:18:07.732 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-19 17:18:07.861 Registering Internal as a media playback plugin.
2009-01-19 17:18:08.120 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-19 17:18:08.612 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-19 17:18:08.612 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-19 17:18:08.713 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-19 17:18:09.143 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 17:18:15.144 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-19 17:18:15.146 Using protocol version 40
2009-01-19 17:18:15.163 TV: Attempting to change from None to WatchingLiveTV
2009-01-19 17:18:15.165 Using protocol version 40
2009-01-19 17:18:15.323 GetEntryAt(-1) failed.
2009-01-19 17:18:15.325 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-19 17:18:15.325 TV Error: LiveTV not successfully started
2009-01-19 17:18:15.325 TV Error: LiveTV not successfully started
2009-01-19 17:18:15.399 TV: Deleting TV Chain in destructor
2009-01-19 17:18:15.767 DPMS Deactivated 
2009-01-19 17:18:15.769 DPMS Reactivated.
Destroying SipFsm object 
2009-01-19 17:18:28.916 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-19 17:20:32.751 New DB connection, total: 2
2009-01-19 17:20:32.751 Connected to database 'mythconverg' at host: localhost
2009-01-19 17:20:32.754 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 17:20:32.755 Enabled verbose msgs:  important general
2009-01-19 17:20:33.394 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 17:20:33.396 Primary screen 0.
2009-01-19 17:20:33.397 Using screen 0, 1280x1024 at 0,0
2009-01-19 17:20:33.398 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 17:20:33.398 Switching to square mode (G.A.N.T)
2009-01-19 17:20:33.437 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-19 17:20:33.438 lirc_init failed for mythtv, see preceding messages
2009-01-19 17:20:33.439 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2009-01-19 17:20:35.929 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-19 17:20:36.060 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-19 17:20:36.115 Registering Internal as a media playback plugin.
2009-01-19 17:20:36.241 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-19 17:20:36.344 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-19 17:20:36.345 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-19 17:20:36.419 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-19 17:20:36.562 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 17:20:45.586 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-19 17:20:45.589 Using protocol version 40
2009-01-19 17:20:45.603 TV: Attempting to change from None to WatchingLiveTV
2009-01-19 17:20:45.606 Using protocol version 40
2009-01-19 17:20:45.744 GetEntryAt(-1) failed.
2009-01-19 17:20:45.745 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-19 17:20:45.745 TV Error: LiveTV not successfully started
2009-01-19 17:20:45.746 TV Error: LiveTV not successfully started
2009-01-19 17:20:45.835 TV: Deleting TV Chain in destructor
2009-01-19 17:20:45.941 DPMS Deactivated 
2009-01-19 17:20:45.943 DPMS Reactivated.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.mythbuntu-log-grabber: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
e" is not supported and will be ignored.mythfrontend.real: Fatal IO error: client killed
Starting mythfrontend.real..
2009-01-19 18:28:53.580 New DB connection, total: 2
2009-01-19 18:28:53.580 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:28:53.584 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 18:28:53.584 Enabled verbose msgs:  important general
2009-01-19 18:28:54.278 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 18:28:54.281 Primary screen 0.
2009-01-19 18:28:54.282 Using screen 0, 1280x1024 at 0,0
2009-01-19 18:28:54.283 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 18:28:54.285 Switching to square mode (G.A.N.T)
2009-01-19 18:28:54.336 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-19 18:28:54.338 lirc_init failed for mythtv, see preceding messages
2009-01-19 18:28:54.338 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2009-01-19 18:28:56.974 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-19 18:28:57.112 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-19 18:28:57.171 Registering Internal as a media playback plugin.
2009-01-19 18:28:57.317 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-19 18:28:57.437 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-19 18:28:57.438 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-19 18:28:57.525 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-19 18:28:57.680 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 18:29:03.846 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-19 18:29:03.848 Using protocol version 40
2009-01-19 18:29:03.863 TV: Attempting to change from None to WatchingLiveTV
2009-01-19 18:29:03.865 Using protocol version 40
2009-01-19 18:29:03.908 GetEntryAt(-1) failed.
2009-01-19 18:29:03.909 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-19 18:29:03.909 TV Error: LiveTV not successfully started
2009-01-19 18:29:03.909 TV Error: LiveTV not successfully started
2009-01-19 18:29:03.999 TV: Deleting TV Chain in destructor
2009-01-19 18:29:04.415 DPMS Deactivated 
2009-01-19 18:29:04.417 DPMS Reactivated.
2009-01-19 18:29:36.692 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
2009-01-19 18:32:04.983 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/movies-ui.xml
2009-01-19 18:32:05.336 New DB connection, total: 3
2009-01-19 18:32:05.336 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:32:05.338 Movie Data Has Expired. Refreshing.
2009-01-19 18:32:05.341 MythMovies Data Grabber: Executing '/usr/bin/ignyte --zip 20110 --radius 5'
2009-01-19 18:32:07.958 Grabber Finished. Processing Data.
2009-01-19 18:34:12.919 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-01-19 18:34:20.540 found script /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan.pl
2009-01-19 18:34:21.537 found script /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan_animaps.pl
2009-01-19 18:34:21.817 found script /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl
2009-01-19 18:34:22.041 found script /usr/share/mythtv/mythweather/scripts/uk_bbc/bbcthreedayxml.pl
2009-01-19 18:34:23.023 found script /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl
2009-01-19 18:34:23.894 found script /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl
2009-01-19 18:34:25.234 found script /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl
2009-01-19 18:34:26.356 found script /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl
2009-01-19 18:34:27.169 found script /usr/share/mythtv/mythweather/scripts/us_nws/nws-alert.pl
2009-01-19 18:34:27.649 found script /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl
2009-01-19 18:34:27.674 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-01-19 18:34:40.907 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-01-19 18:36:26.901 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2009-01-19 18:37:03.987 Starting update of NWS-XML
2009-01-19 18:37:04.008 Starting update of NDFD-6_day
2009-01-19 18:37:04.729 Container startup has NULL area, bad theme.
2009-01-19 18:37:04.861 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/dad/.mythtv/MythWeather/NWS-XML KHEF has exited
2009-01-19 18:37:08.684 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/dad/.mythtv/MythWeather/NDFD-6_day +38.43,-077.31 has exited
2009-01-19 18:38:03.429 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-19 18:38:03.457 Failed to open DVD device at /dev/dvd
2009-01-19 18:38:18.394 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-19 18:38:18.411 Failed to open DVD device at /dev/dvd
2009-01-19 18:38:23.776 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/dvd-ui.xml
Destroying SipFsm object 
2009-01-19 18:39:21.108 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-19 18:43:01.812 New DB connection, total: 2
2009-01-19 18:43:01.812 Connected to database 'mythconverg' at host: localhost
2009-01-19 18:43:01.817 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-19 18:43:01.817 Enabled verbose msgs:  important general
2009-01-19 18:43:02.537 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 18:43:02.539 Primary screen 0.
2009-01-19 18:43:02.540 Using screen 0, 1280x1024 at 0,0
2009-01-19 18:43:02.540 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 18:43:02.541 Switching to square mode (G.A.N.T)
2009-01-19 18:43:02.586 Using the Qt painter
2009-01-19 18:43:02.586 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-19 18:43:02.587 lirc_init failed for mythtv, see preceding messages
2009-01-19 18:43:05.256 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-19 18:43:05.404 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-19 18:43:05.467 Registering Internal as a media playback plugin.
2009-01-19 18:43:05.604 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-19 18:43:05.724 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-19 18:43:05.724 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-19 18:43:05.822 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-19 18:43:05.976 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-19 18:43:10.409 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-19 18:43:10.411 Using protocol version 40
Destroying SipFsm object 
2009-01-19 18:43:13.397 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-20 08:55:21.309 New DB connection, total: 2
2009-01-20 08:55:21.310 Connected to database 'mythconverg' at host: localhost
2009-01-20 08:55:21.324 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 08:55:21.324 Enabled verbose msgs:  important general
2009-01-20 08:55:22.742 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 08:55:22.744 Primary screen 0.
2009-01-20 08:55:22.745 Using screen 0, 1280x1024 at 0,0
2009-01-20 08:55:22.745 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 08:55:22.746 Switching to square mode (G.A.N.T)
2009-01-20 08:55:22.804 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-20 08:55:22.806 lirc_init failed for mythtv, see preceding messages
2009-01-20 08:55:22.806 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2009-01-20 08:55:25.380 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-20 08:55:25.611 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-20 08:55:25.687 Registering Internal as a media playback plugin.
2009-01-20 08:55:26.020 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-20 08:55:26.458 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-20 08:55:26.458 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-20 08:55:26.526 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-20 08:55:26.903 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 08:55:48.253 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-20 08:55:48.255 Using protocol version 40
2009-01-20 08:55:48.265 TV: Attempting to change from None to WatchingLiveTV
2009-01-20 08:55:48.269 Using protocol version 40
2009-01-20 08:55:48.303 GetEntryAt(-1) failed.
2009-01-20 08:55:48.304 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-20 08:55:48.305 TV Error: LiveTV not successfully started
2009-01-20 08:55:48.305 TV Error: LiveTV not successfully started
2009-01-20 08:55:48.402 TV: Deleting TV Chain in destructor
2009-01-20 08:55:48.507 DPMS Deactivated 
2009-01-20 08:55:48.509 DPMS Reactivated.
2009-01-20 08:55:53.359 TV: Attempting to change from None to WatchingLiveTV
2009-01-20 08:55:53.362 Using protocol version 40
2009-01-20 08:55:53.407 GetEntryAt(-1) failed.
2009-01-20 08:55:53.408 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-20 08:55:53.408 TV Error: LiveTV not successfully started
2009-01-20 08:55:53.409 TV Error: LiveTV not successfully started
2009-01-20 08:55:53.505 TV: Deleting TV Chain in destructor
2009-01-20 08:55:53.515 DPMS Deactivated 
2009-01-20 08:55:53.515 DPMS Reactivated.
2009-01-20 08:56:33.530 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml
2009-01-20 08:56:34.552 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-20 08:56:34.553 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-20 08:56:54.732 Received a remote 'Clear Cache' request
2009-01-20 08:57:05.240 Received a remote 'Clear Cache' request
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Starting mythfrontend.real..
2009-01-20 09:03:24.687 New DB connection, total: 2
2009-01-20 09:03:24.688 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:03:24.690 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 09:03:24.691 Enabled verbose msgs:  important general
2009-01-20 09:03:26.638 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:03:26.640 Primary screen 0.
2009-01-20 09:03:26.641 Using screen 0, 1280x1024 at 0,0
2009-01-20 09:03:26.642 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:03:26.642 Switching to square mode (G.A.N.T)
2009-01-20 09:03:26.715 Using the Qt painter
2009-01-20 09:03:26.716 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-20 09:03:26.716 lirc_init failed for mythtv, see preceding messages
2009-01-20 09:03:29.449 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-20 09:03:29.616 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-20 09:03:29.762 Registering Internal as a media playback plugin.
2009-01-20 09:03:30.083 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-20 09:03:30.624 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-20 09:03:30.624 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-20 09:03:30.765 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-20 09:03:31.193 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:03:37.460 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-20 09:03:37.462 Using protocol version 40
2009-01-20 09:03:37.490 TV: Attempting to change from None to WatchingLiveTV
2009-01-20 09:03:37.492 Using protocol version 40
2009-01-20 09:03:37.558 GetEntryAt(-1) failed.
2009-01-20 09:03:37.559 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-01-20 09:03:37.560 TV Error: LiveTV not successfully started
2009-01-20 09:03:37.560 TV Error: LiveTV not successfully started
2009-01-20 09:03:37.630 TV: Deleting TV Chain in destructor
2009-01-20 09:03:37.735 DPMS Deactivated 
2009-01-20 09:03:37.737 DPMS Reactivated.
Destroying SipFsm object 
2009-01-20 09:03:47.959 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-20 09:13:27.234 New DB connection, total: 2
2009-01-20 09:13:27.234 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:13:27.238 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 09:13:27.238 Enabled verbose msgs:  important general
2009-01-20 09:13:27.858 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:13:27.860 Primary screen 0.
2009-01-20 09:13:27.860 Using screen 0, 1280x1024 at 0,0
2009-01-20 09:13:27.861 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:13:27.861 Switching to square mode (G.A.N.T)
2009-01-20 09:13:27.900 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-20 09:13:27.901 lirc_init failed for mythtv, see preceding messages
2009-01-20 09:13:27.902 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
2009-01-20 09:13:30.296 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-20 09:13:30.427 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-20 09:13:30.482 Registering Internal as a media playback plugin.
2009-01-20 09:13:30.608 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-20 09:13:30.720 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-20 09:13:30.721 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-20 09:13:30.802 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-20 09:13:30.941 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:13:36.585 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-20 09:13:36.587 Using protocol version 40
Destroying SipFsm object 
2009-01-20 09:13:46.373 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-20 09:44:32.453 New DB connection, total: 2
2009-01-20 09:44:32.453 Connected to database 'mythconverg' at host: localhost
2009-01-20 09:44:32.457 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-20 09:44:32.457 Enabled verbose msgs:  important general
2009-01-20 09:44:33.082 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:44:33.084 Primary screen 0.
2009-01-20 09:44:33.085 Using screen 0, 1280x1024 at 0,0
2009-01-20 09:44:33.085 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:44:33.086 Switching to square mode (G.A.N.T)
2009-01-20 09:44:33.128 Using the Qt painter
2009-01-20 09:44:33.128 JoystickMenuClient Error: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-20 09:44:33.129 lirc_init failed for mythtv, see preceding messages
2009-01-20 09:44:35.960 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-20 09:44:36.091 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-20 09:44:36.146 Registering Internal as a media playback plugin.
2009-01-20 09:44:36.274 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-20 09:44:36.377 MythMusic adding CD-Writer: 1,0,0 -- DVD RW DRU-842A 
2009-01-20 09:44:36.377 MythMusic adding CD-Writer: 1,1,0 -- COMBO LTC-48161H
2009-01-20 09:44:36.448 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.101:5060 NAT address 192.168.1.101
SIP: Cannot register; proxy, username or password not set
2009-01-20 09:44:36.588 No theme dir: /home/dad/.mythtv/themes/G.A.N.T
2009-01-20 09:45:10.335 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-20 09:45:10.336 Using protocol version 40
Destroying SipFsm object 
2009-01-20 09:45:13.020 Deleting UPnP client...

dmesg
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5ff00000:9ed00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389267
[    0.000000] Kernel command line: root=UUID=e045261b-9e4e-4819-8e30-4cd022e4c6b1 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2992.484 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1542268k/1571264k available (2572k kernel code, 27740k reserved, 1160k data, 424k init, 653760k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.96 BogoMIPS (lpj=11969936)
[    0.004045] Security Framework initialized
[    0.004061] SELinux:  Disabled at boot.
[    0.004093] AppArmor: AppArmor initialized
[    0.004110] Mount-cache hash table entries: 512
[    0.004385] Initializing cgroup subsys ns
[    0.004392] Initializing cgroup subsys cpuacct
[    0.004395] Initializing cgroup subsys memory
[    0.004418] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004422] CPU: L2 cache: 512K
[    0.004425] CPU: Physical Processor ID: 0
[    0.004444] Checking 'hlt' instruction... OK.
[    0.022217] ACPI: Core revision 20080609
[    0.034199] ACPI: Checking initramfs for custom DSDT
[    0.369307] ENABLING IO-APIC IRQs
[    0.369498] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.409190] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.412025] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5985.33 BogoMIPS (lpj=11970679)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.496220] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[    0.496246] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.500071] Brought up 2 CPUs
[    0.500077] Total of 2 processors activated (11970.30 BogoMIPS).
[    0.500102] CPU0 attaching sched-domain:
[    0.500106]  domain 0: span 0-1 level SIBLING
[    0.500110]   groups: 0 1
[    0.500116]   domain 1: span 0-1 level CPU
[    0.500120]    groups: 0-1
[    0.500127] CPU1 attaching sched-domain:
[    0.500129]  domain 0: span 0-1 level SIBLING
[    0.500133]   groups: 1 0
[    0.500138]   domain 1: span 0-1 level CPU
[    0.500142]    groups: 0-1
[    0.500270] net_namespace: 840 bytes
[    0.500270] Booting paravirtualized kernel on bare hardware
[    0.500408] Time: 14:01:17  Date: 01/20/09
[    0.500453] NET: Registered protocol family 16
[    0.500494] EISA bus registered
[    0.500494] ACPI: bus type pci registered
[    0.500494] PCI: PCI BIOS revision 2.10 entry at 0xfbb15, last bus=1
[    0.500494] PCI: Using configuration type 1 for base access
[    0.504682] ACPI: EC: Look up EC in DSDT
[    0.534785] ACPI: Interpreter enabled
[    0.534791] ACPI: (supports S0 S1 S3 S4 S5)
[    0.534816] ACPI: Using IOAPIC for interrupt routing
[    0.564282] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.564282] PCI: 0000:00:00.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.564282] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.564282] PCI: 0000:00:02.0 reg 14 32bit mmio: [feb80000, febfffff]
[    0.564282] PCI: 0000:00:02.0 reg 18 io port: [ed98, ed9f]
[    0.564282] PCI: 0000:00:1d.0 reg 20 io port: [ff80, ff9f]
[    0.564295] PCI: 0000:00:1d.1 reg 20 io port: [ff60, ff7f]
[    0.564348] PCI: 0000:00:1d.2 reg 20 io port: [ff40, ff5f]
[    0.564401] PCI: 0000:00:1d.3 reg 20 io port: [ff20, ff3f]
[    0.564464] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa80800, ffa80bff]
[    0.564519] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.564526] pci 0000:00:1d.7: PME# disabled
[    0.564605] pci 0000:00:1f.0: HPET at 0xfed00000
[    0.564613] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.564617] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.564638] PCI: 0000:00:1f.1 reg 10 io port: [1f0, 1f7]
[    0.564646] PCI: 0000:00:1f.1 reg 14 io port: [3f4, 3f7]
[    0.564654] PCI: 0000:00:1f.1 reg 18 io port: [170, 177]
[    0.564662] PCI: 0000:00:1f.1 reg 1c io port: [374, 377]
[    0.564669] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
[    0.564677] PCI: 0000:00:1f.1 reg 24 32bit mmio: [feb7fc00, feb7ffff]
[    0.564706] PCI: 0000:00:1f.2 reg 10 io port: [fe00, fe07]
[    0.564713] PCI: 0000:00:1f.2 reg 14 io port: [fe10, fe13]
[    0.564720] PCI: 0000:00:1f.2 reg 18 io port: [fe20, fe27]
[    0.564727] PCI: 0000:00:1f.2 reg 1c io port: [fe30, fe33]
[    0.564734] PCI: 0000:00:1f.2 reg 20 io port: [fea0, feaf]
[    0.564785] PCI: 0000:00:1f.3 reg 20 io port: [eda0, edbf]
[    0.564829] PCI: 0000:00:1f.5 reg 10 io port: [ee00, eeff]
[    0.564836] PCI: 0000:00:1f.5 reg 14 io port: [edc0, edff]
[    0.564843] PCI: 0000:00:1f.5 reg 18 32bit mmio: [feb7fa00, feb7fbff]
[    0.564851] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [feb7f900, feb7f9ff]
[    0.564878] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.564883] pci 0000:00:1f.5: PME# disabled
[    0.564928] PCI: 0000:01:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.564994] PCI: 0000:01:00.1 reg 10 32bit mmio: [fb000000, fbffffff]
[    0.565058] PCI: 0000:01:00.2 reg 10 32bit mmio: [fc000000, fcffffff]
[    0.565124] PCI: 0000:01:00.4 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.565195] PCI: 0000:01:01.0 reg 10 32bit mmio: [feafe000, feafefff]
[    0.565203] PCI: 0000:01:01.0 reg 14 io port: [de00, deff]
[    0.565244] pci 0000:01:01.0: PME# supported from D0 D3hot D3cold
[    0.565249] pci 0000:01:01.0: PME# disabled
[    0.565284] PCI: 0000:01:08.0 reg 10 32bit mmio: [feaff000, feafffff]
[    0.565291] PCI: 0000:01:08.0 reg 14 io port: [ddc0, ddff]
[    0.565327] pci 0000:01:08.0: supports D1
[    0.565329] pci 0000:01:08.0: supports D2
[    0.565332] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.565337] pci 0000:01:08.0: PME# disabled
[    0.568037] pci 0000:00:1e.0: transparent bridge
[    0.568043] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[    0.568048] PCI: bridge 0000:00:1e.0 32bit mmio: [fa000000, feafffff]
[    0.568060] bus 00 -> node 0
[    0.568071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.568647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.684870] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.684870] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.685009] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.685346] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.685683] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.686018] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.686355] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.688236] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.688358] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.688358] pnp: PnP ACPI init
[    0.688358] ACPI: bus type pnp registered
[    0.712224] pnp 00:0b: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.712229] pnp 00:0b: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.712777] pnp: PnP ACPI: found 12 devices
[    0.712780] ACPI: ACPI bus type pnp unregistered
[    0.712786] PnPBIOS: Disabled by ACPI PNP
[    0.712820] PCI: Using ACPI for IRQ routing
[    0.720048] NET: Registered protocol family 8
[    0.720052] NET: Registered protocol family 20
[    0.720082] NetLabel: Initializing
[    0.720082] NetLabel:  domain hash size = 128
[    0.720082] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.720088] NetLabel:  unlabeled traffic allowed by default
[    0.720179] hpet clockevent registered
[    0.720184] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.720192] hpet0: 3 64-bit timers, 14318180 Hz
[    0.722644] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.722647]    actual entries 65620
[    0.722884] AppArmor: AppArmor Filesystem Enabled
[    0.722908] ACPI: RTC can wake from S4
[    0.728077] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.728082] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.728086] system 00:00: iomem range 0x1000000-0x5fe6ffff could not be reserved
[    0.728090] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    0.728094] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.728098] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.728102] system 00:00: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.728105] system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
[    0.728109] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.728113] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.728136] system 00:0b: ioport range 0xc00-0xc7f has been reserved
[    0.763766] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.763771] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.763778] pci 0000:00:1e.0:   MEM window: 0xfa000000-0xfeafffff
[    0.763784] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.763802] pci 0000:00:1e.0: setting latency timer to 64
[    0.763808] bus: 00 index 0 io port: [0, ffff]
[    0.763810] bus: 00 index 1 mmio: [0, ffffffff]
[    0.763813] bus: 01 index 0 io port: [d000, dfff]
[    0.763816] bus: 01 index 1 mmio: [fa000000, feafffff]
[    0.763818] bus: 01 index 2 mmio: [0, 0]
[    0.763821] bus: 01 index 3 io port: [0, ffff]
[    0.763824] bus: 01 index 4 mmio: [0, ffffffff]
[    0.763841] NET: Registered protocol family 2
[    0.776124] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.776590] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.777752] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.778492] TCP: Hash tables configured (established 131072 bind 65536)
[    0.778499] TCP reno registered
[    0.784221] NET: Registered protocol family 1
[    0.784404] checking if image is initramfs... it is
[    1.220306] Switched to high resolution mode on CPU 1
[    1.224062] Switched to high resolution mode on CPU 0
[    1.458509] Freeing initrd memory: 8005k freed
[    1.458847] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    1.458853] Simple Boot Flag at 0x7a set to 0x1
[    1.460068] audit: initializing netlink socket (disabled)
[    1.460090] type=2000 audit(1232460077.460:1): initialized
[    1.464636] highmem bounce pool size: 64 pages
[    1.464647] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.468625] VFS: Disk quotas dquot_6.5.1
[    1.468798] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.468976] msgmni has been set to 1752
[    1.469207] io scheduler noop registered
[    1.469212] io scheduler anticipatory registered
[    1.469215] io scheduler deadline registered
[    1.469240] io scheduler cfq registered (default)
[    1.469260] pci 0000:00:02.0: Boot video device
[    1.469370] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.470067] isapnp: Scanning for PnP cards...
[    1.823764] isapnp: No Plug & Play device found
[    1.896407] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.896593] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.897940] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.898259] serial 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.899138] 0000:01:01.0: ttyS1 at I/O 0xde08 (irq = 22) is a 16450
[    1.899623] 0000:01:01.0: ttyS2 at I/O 0xde10 (irq = 22) is a 8250
[    1.900143] 0000:01:01.0: ttyS3 at I/O 0xde18 (irq = 22) is a 16450
[    1.900306] Couldn't register serial port 0000:01:01.0: -28
[    1.903444] brd: module loaded
[    1.903570] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.903801] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.906805] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.906815] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.908256] mice: PS/2 mouse device common for all mice
[    1.908549] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.908576] rtc0: alarms up to one day, hpet irqs
[    1.908849] EISA: Probing bus 0 at eisa.0
[    1.908891] EISA: Detected 0 cards.
[    1.908896] cpuidle: using governor ladder
[    1.908899] cpuidle: using governor menu
[    1.909698] TCP cubic registered
[    1.909740] Using IPI No-Shortcut mode
[    1.910195] registered taskstats version 1
[    1.910390]   Magic number: 9:915:30
[    1.910408] tty ttydd: hash matches
[    1.910560] rtc_cmos 00:05: setting system clock to 2009-01-20 14:01:18 UTC (1232460078)
[    1.910565] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.910567] EDD information not available.
[    1.911128] Freeing unused kernel memory: 424k freed
[    1.911197] Write protecting the kernel text: 2576k
[    1.911237] Write protecting the kernel read-only data: 936k
[    1.932124] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.140692] fuse init (API version 7.9)
[    2.304667] processor ACPI0007:00: registered as cooling_device0
[    2.308604] processor ACPI0007:01: registered as cooling_device1
[    3.016783] usbcore: registered new interface driver usbfs
[    3.016868] usbcore: registered new interface driver hub
[    3.029212] usbcore: registered new device driver usb
[    3.036535] USB Universal Host Controller Interface driver v3.0
[    3.036616] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.036632] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.036638] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.036732] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.036773] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    3.037049] usb usb1: configuration #1 chosen from 1 choice
[    3.037102] hub 1-0:1.0: USB hub found
[    3.037117] hub 1-0:1.0: 2 ports detected
[    3.164173] No dock devices found.
[    3.236722] SCSI subsystem initialized
[    3.275427] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.275443] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.275450] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.275501] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.275544] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    3.275738] usb usb2: configuration #1 chosen from 1 choice
[    3.275796] hub 2-0:1.0: USB hub found
[    3.275814] hub 2-0:1.0: 2 ports detected
[    3.313526] libata version 3.00 loaded.
[    3.352919] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    3.352925] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.376991] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.377007] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.377013] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.377076] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.377118] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    3.377328] usb usb3: configuration #1 chosen from 1 choice
[    3.377386] hub 3-0:1.0: USB hub found
[    3.377402] hub 3-0:1.0: 2 ports detected
[    3.388600] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.481505] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.481528] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.481536] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.481612] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.481657] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[    3.481991] usb usb4: configuration #1 chosen from 1 choice
[    3.482057] hub 4-0:1.0: USB hub found
[    3.482088] hub 4-0:1.0: 2 ports detected
[    3.551436] usb 1-2: configuration #1 chosen from 1 choice
[    3.585642] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.585677] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.585687] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.585769] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.589740] ehci_hcd 0000:00:1d.7: debug port 1
[    3.589757] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.589799] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    3.604610] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.605223] usb usb5: configuration #1 chosen from 1 choice
[    3.605324] hub 5-0:1.0: USB hub found
[    3.605359] hub 5-0:1.0: 8 ports detected
[    3.624694] usb 1-2: USB disconnect, address 2
[    3.815213] ata_piix 0000:00:1f.1: version 2.12
[    3.815242] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.815341] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.816193] scsi0 : ata_piix
[    3.816576] scsi1 : ata_piix
[    3.816670] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.816677] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.924821] usb 5-2: new high speed USB device using ehci_hcd and address 2
[    4.044619] ata1.00: ATA-6: ST340014A, 3.16, max UDMA/100
[    4.044627] ata1.00: 78125000 sectors, multi 8: LBA48 
[    4.058858] usb 5-2: configuration #1 chosen from 1 choice
[    4.060516] ata1.00: configured for UDMA/100
[    4.348463] ata2.00: ATAPI: SONY    DVD RW DRU-842A, 1.60, max UDMA/66
[    4.348495] ata2.01: ATAPI: LITE-ON COMBO LTC-48161H, KPH9, max UDMA/33
[    4.348518] ata2.00: limited to UDMA/33 due to 40-wire cable
[    4.364356] ata2.00: configured for UDMA/33
[    4.380331] ata2.01: configured for UDMA/33
[    4.380592] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.16 PQ: 0 ANSI: 5
[    4.382637] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-842A  1.60 PQ: 0 ANSI: 5
[    4.383480] scsi 1:0:1:0: CD-ROM            LITE-ON  COMBO LTC-48161H KPH9 PQ: 0 ANSI: 5
[    4.383735] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.383746] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.383836] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.384080] scsi2 : ata_piix
[    4.399804] scsi3 : ata_piix
[    4.399967] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
[    4.399974] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
[    5.508212] usbcore: registered new interface driver libusual
[    5.546124] Initializing USB Mass Storage driver...
[    5.549604] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.550160] usbcore: registered new interface driver usb-storage
[    5.550197] USB Mass Storage support registered.
[    5.550581] usb-storage: device found at 2
[    5.550587] usb-storage: waiting for device to settle before scanning
[    8.040537] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.063156] e100 0000:01:08.0: PME# disabled
[    8.072929] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:0c:f1:e9:ee:26
[    8.102472] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    8.102626] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    8.102758] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    8.184965] Driver 'sd' needs updating - please use bus_type methods
[    8.185461] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[    8.185552] sd 0:0:0:0: [sda] Write Protect is off
[    8.185571] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.185737] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.186053] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors (40000 MB)
[    8.186125] sd 0:0:0:0: [sda] Write Protect is off
[    8.186132] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.186318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.186340]  sda: sda1 sda2 < sda5 >
[    8.216336] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.221301] Driver 'sr' needs updating - please use bus_type methods
[    8.233733] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.233752] Uniform CD-ROM driver Revision: 3.20
[    8.234213] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.240342] sr1: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[    8.240793] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    8.750345] PM: Starting manual resume from disk
[    8.750351] PM: Resume from partition 8:5
[    8.750354] PM: Checking hibernation image.
[    8.750614] PM: Resume from disk failed.
[    8.856593] kjournald starting.  Commit interval 5 seconds
[    8.856671] EXT3-fs: mounted filesystem with ordered data mode.
[   10.548828] usb-storage: device scan complete
[   10.549436] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
[   10.550955] sd 4:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[   10.551550] sd 4:0:0:0: [sdb] Write Protect is off
[   10.551554] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[   10.551559] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   10.552292] sd 4:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[   10.552924] sd 4:0:0:0: [sdb] Write Protect is off
[   10.552928] sd 4:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[   10.552930] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   10.552935]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 > sdb3
[   10.574932] sd 4:0:0:0: [sdb] Attached SCSI disk
[   10.575127] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   15.408581] udevd version 124 started
[   16.290778] Linux agpgart interface v0.103
[   16.347186] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   16.347386] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[   16.377113] intel_rng: Firmware space is locked read-only. If you can't or
[   16.377117] intel_rng: don't want to disable this in firmware setup, and if
[   16.377121] intel_rng: you are certain that your system has a functional
[   16.377124] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   16.460412] iTCO_vendor_support: vendor-support=0
[   16.466346] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   16.484621] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   16.485617] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   16.485835] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.524981] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.594787] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.649444] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.680993] ACPI: Power Button (FF) [PWRF]
[   16.681180] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   16.692094] ACPI: Power Button (CM) [VBTN]
[   17.398696] parport_pc 00:0a: reported by Plug and Play ACPI
[   17.398756] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   17.839921] Linux video capture interface: v2.00
[   17.940692] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   17.940763] cx8800 0000:01:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.941655] cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected]
[   17.941662] cx88[0]: TV tuner type 64, Radio tuner type -1
[   17.949038] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   18.319669] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[   18.415232] cx2388x alsa driver version 0.0.6 loaded
[   18.485043] tda9887 0-0043: creating new instance
[   18.485050] tda9887 0-0043: tda988[5/6/7] found
[   18.488472] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[   18.806379] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   18.845085] tuner-simple 0-0061: creating new instance
[   18.845094] tuner-simple 0-0061: type set to 64 (LG TDVS-H06xF)
[   18.848281] cx88[0]/0: found at 0000:01:00.0, rev: 5, irq: 21, latency: 64, mmio: 0xfa000000
[   18.848740] cx88[0]/0: registered device video0 [v4l2]
[   18.849367] cx88[0]/0: registered device vbi0
[   18.854247] cx88[0]/2: cx2388x 8802 Driver Manager
[   18.854277] cx88-mpeg driver manager 0000:01:00.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.854296] cx88[0]/2: found at 0000:01:00.2, rev: 5, irq: 21, latency: 64, mmio: 0xfc000000
[   18.854558] cx88_audio 0000:01:00.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.854647] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   19.108314] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   19.108322] cx88/2: registering cx8802 driver, type: dvb access: shared
[   19.108333] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[   19.108369] cx88[0]/2: cx2388x based DVB/ATSC card
[   19.510473] tuner-simple 0-0061: attaching existing instance
[   19.510481] tuner-simple 0-0061: type set to 64 (LG TDVS-H06xF)
[   19.510639] tda9887 0-0043: attaching existing instance
[   19.511424] DVB: registering new adapter (cx88[0])
[   19.511431] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   19.679718] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.679748] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.691926] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   19.749453] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.104067] intel8x0_measure_ac97_clock: measured 55932 usecs
[   20.104077] intel8x0: clocking to 48000
[   22.236560] lp0: using parport0 (interrupt-driven).
[   22.418672] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   22.715724] EXT3 FS on sda1, internal journal
[   23.389562] type=1505 audit(1232460100.294:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4122
[   23.583356] type=1505 audit(1232460100.486:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4127
[   23.583740] type=1505 audit(1232460100.486:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4127
[   23.640323] type=1505 audit(1232460100.546:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4131
[   23.840390] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by scary_jeff on 2009-01-20
I can't tell from the logs you posted, but I had the same kind of problem on my first try, and the reason was that I had only set up the capture cards in the backend setup. After setting up the video source and input connection, and performing a channel scan, TV worked properly.

---

### Post by buddylind on 2009-01-20
Thanks for your reply scary_jeff. I think I am going to remove everything i have done and start over. Thanks again.

---

### Post by UltramaticOrange on 2009-01-20
I had similar problems for a variety of reasons all at different points of setting things up:

- Didn't have the proper firmware installed for my TV Tuner card.
- permissions on my 'recordings' directory were not set correctly.
- I did not go through ALL the settings on the backend setup. (I've experience doing video capturing before using MythTV and a lot of the settings still took a few tries before I understood what they're all for. It doesn't help that they're not well named, imo.)
- Default channel to tune was set to a channel that I don't get (no signal).
- My channel change script (to change channels on my cable box) took too long to run. 

If I think of more causes of this problem, I'll post.

Edit: It looks like from your logs that you're using a USB hard drive for recordings. Is that correct? If so, it might be possible that a USB hard drive won't have enough throughput to record to. Also, I'm confused about what TV tuner card you're using. Is it a PcHDTV HD-5500 or a Hauppauge?

---

### Post by buddylind on 2009-01-21
Thanks for your reply. The tuner card is in fact a PcHDTV HD-5500, sorry for the confusion. I'm going to look at all the things you mentioned. This sure did sound like any easy project when I read about it. :)

---

### Post by dwfallin on 2009-01-28
i've got the exact same problem!! please post back if you figure it out!
UltimateOrange - what did you change the permissions to? (ug+rwx and myth user owned)

---

### Post by rupert80 on 2009-01-31
I have a similar problem.  The tuner works as I can watch live tv using me-tv, but mythtv doesn't work.  Here is a snippet from my mythfrontend log:

2009-01-31 20:46:45.581 Connecting to backend server: 192.168.19.100:6543 (try 1 of 5)
2009-01-31 20:46:45.581 Using protocol version 40
2009-01-31 20:46:45.591 TV: Attempting to change from None to WatchingLiveTV
2009-01-31 20:46:45.592 Using protocol version 40
2009-01-31 20:46:45.765 GetEntryAt(-1) failed.
2009-01-31 20:46:45.765 EntryToProgram(0@Thu Jan 1 08:00:00 1970) failed to get pginfo
2009-01-31 20:46:45.765 TV Error: LiveTV not successfully started
2009-01-31 20:46:45.766 TV Error: LiveTV not successfully started
2009-01-31 20:46:45.792 TV: Deleting TV Chain in destructor
2009-01-31 20:46:45.796 DPMS Deactivated
2009-01-31 20:46:45.797 DPMS Reactivated.

I've crawled all over the backend setup.  Setup the card, input, source, etc.  It is able to scan for channels Ok and I set the default starting channel to one I know has reception.

Definitely weird!

---

