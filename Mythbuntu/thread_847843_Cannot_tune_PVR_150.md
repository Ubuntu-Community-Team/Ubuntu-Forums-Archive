---
title: "Cannot tune PVR 150"
date: 2008-07-02
forum: Mythbuntu
---

### Post by MikeB23930 on 2008-07-02
I installed Mythbuntu on an amdX64 system with a Hauppauge PVR 150 card.  Scan for channels works fine, but when I try to watch Live TV, Mythtv seems to stall with a black screen for perhaps 30 seconds and then drops me back to the main frontend screen.  I have also tried two Hauppauge dvb-t cards, an HVR 950 and an HVR 1250, with the same result.  

Any help getting any of these cards to work would be greatly appreciated.

Thanks

Mike

---

### Post by tgm4883 on 2008-07-03
> **MikeB23930 said:**
> I installed Mythbuntu on an amdX64 system with a Hauppauge PVR 150 card.  Scan for channels works fine, but when I try to watch Live TV, Mythtv seems to stall with a black screen for perhaps 30 seconds and then drops me back to the main frontend screen.  I have also tried two Hauppauge dvb-t cards, an HVR 950 and an HVR 1250, with the same result.  

Any help getting any of these cards to work would be greatly appreciated.

Thanks

Mike

Please post your backend log located at /var/log/mythtv/mythbackend.log

---

### Post by MikeB23930 on 2008-07-03
> **tgm4883 said:**
> Please post your backend log located at /var/log/mythtv/mythbackend.log

tgm4883,

Here is my mythbackend.log with only Hauppuage PVR 150 installed:

2008-07-02 22:29:26.936 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-02 22:29:27.144 Empty LocalHostName.
2008-07-02 22:29:27.271 Using localhost value of Mythbntu804
2008-07-02 22:29:27.861 New DB connection, total: 1
2008-07-02 22:29:27.908 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:27.918 Closing DB connection named 'DBManager0'
2008-07-02 22:29:28.185 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:28.719 New DB connection, total: 2
2008-07-02 22:29:28.767 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:28.806 Current Schema Version: 1214
Starting up as the master server.
2008-07-02 22:29:35.451 New DB connection, total: 3
2008-07-02 22:29:35.788 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:35.968 New DB scheduler connection
2008-07-02 22:29:35.985 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:36.247 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-02 22:29:36.274 Main::Registering HttpStatus Extension
2008-07-02 22:29:36.358 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-02 22:29:36.396 Enabled verbose msgs:  important general
2008-07-02 22:29:36.527 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 22:29:39.248 Reschedule requested for id -1.
2008-07-02 22:29:40.090 Scheduled 0 items in 0.9 = 0.66 match + 0.23 place
2008-07-02 22:29:40.759 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-07-02 22:30:56.120 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 22:32:05.729 MainServer::HandleAnnounce Monitor
2008-07-02 22:32:05.748 adding: Mythbntu804 as a client (events: 0)
2008-07-02 22:32:05.758 MainServer::HandleAnnounce Monitor
2008-07-02 22:32:05.768 adding: Mythbntu804 as a client (events: 1)
2008-07-02 22:32:05.786 MainServer::HandleAnnounce Playback
2008-07-02 22:32:05.828 adding: Mythbntu804 as a client (events: 0)
2008-07-02 22:32:05.842 TVRec(1): Changing from None to WatchingLiveTV
2008-07-02 22:32:05.860 TVRec(1): HW Tuner: 1->1
2008-07-02 22:32:06.127 New DB connection, total: 4
2008-07-02 22:32:06.146 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:32:07.567 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-02 22:32:07.635 NVR(/dev/video0) Error: Unknown audio codec
2008-07-02 22:32:07.694 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-02 22:32:07.709 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-02 22:32:47.791 TVRec(1): Changing from WatchingLiveTV to None
2008-07-02 22:32:47.831 Finished recording Unknown: channel 1006
2008-07-02 22:33:03.459 MainServer::HandleAnnounce Playback
2008-07-02 22:33:03.476 adding: Mythbntu804 as a client (events: 0)
2008-07-02 22:33:03.495 TVRec(1): Changing from None to WatchingLiveTV
2008-07-02 22:33:03.517 TVRec(1): HW Tuner: 1->1
2008-07-02 22:33:04.651 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-02 22:33:04.709 NVR(/dev/video0) Error: Unknown audio codec
2008-07-02 22:33:04.752 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-02 22:33:04.755 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-02 22:33:44.766 TVRec(1): Changing from WatchingLiveTV to None
2008-07-02 22:33:44.794 Finished recording Unknown: channel 1006
2008-07-02 22:33:44.855 MythSocket(8894e0:-1): writeStringList: Error, socket went unconnected.
2008-07-02 23:09:09.665 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-02 23:09:09.839 Empty LocalHostName.
2008-07-02 23:09:10.091 Using localhost value of Mythbntu804
2008-07-02 23:09:10.536 New DB connection, total: 1
2008-07-02 23:09:10.579 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:10.590 Closing DB connection named 'DBManager0'
2008-07-02 23:09:10.600 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:10.668 New DB connection, total: 2
2008-07-02 23:09:10.834 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:11.021 Current Schema Version: 1214
Starting up as the master server.
2008-07-02 23:09:16.556 New DB connection, total: 3
2008-07-02 23:09:16.701 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:16.862 New DB scheduler connection
2008-07-02 23:09:17.113 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:17.710 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-02 23:09:17.772 Main::Registering HttpStatus Extension
2008-07-02 23:09:17.781 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-02 23:09:17.900 Enabled verbose msgs:  important general
2008-07-02 23:09:17.975 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 23:09:20.275 Reschedule requested for id -1.
2008-07-02 23:09:21.087 Scheduled 0 items in 0.8 = 0.45 match + 0.37 place
2008-07-02 23:09:21.397 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-07-02 23:10:37.949 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 23:10:38.034 Expiring 0 MBytes for 1006 @ Wed Jul 2 22:32:05 2008 => Unknown
2008-07-02 23:10:38.090 Expiring 0 MBytes for 1006 @ Wed Jul 2 22:33:03 2008 => Unknown
2008-07-02 23:10:43.493 MainServer::HandleAnnounce Monitor
2008-07-02 23:10:43.525 adding: Mythbntu804 as a client (events: 0)
2008-07-02 23:10:43.536 MainServer::HandleAnnounce Monitor
2008-07-02 23:10:43.546 adding: Mythbntu804 as a client (events: 1)
2008-07-03 08:28:34.343 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 08:28:34.500 Empty LocalHostName.
2008-07-03 08:28:34.847 Using localhost value of Mythbntu804
2008-07-03 08:28:35.389 New DB connection, total: 1
2008-07-03 08:28:35.427 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:35.770 Closing DB connection named 'DBManager0'
2008-07-03 08:28:36.049 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:36.127 New DB connection, total: 2
2008-07-03 08:28:36.139 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:36.318 Current Schema Version: 1214
Starting up as the master server.
2008-07-03 08:28:42.709 New DB connection, total: 3
2008-07-03 08:28:42.756 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:42.935 New DB scheduler connection
2008-07-03 08:28:42.985 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:43.163 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-03 08:28:43.173 Main::Registering HttpStatus Extension
2008-07-03 08:28:43.182 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-03 08:28:43.192 Enabled verbose msgs:  important general
2008-07-03 08:28:43.330 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 08:28:46.105 Reschedule requested for id -1.
2008-07-03 08:28:46.940 Scheduled 0 items in 0.8 = 0.68 match + 0.15 place
2008-07-03 08:28:48.078 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-07-03 08:30:05.006 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 08:31:23.460 MainServer::HandleAnnounce Monitor
2008-07-03 08:31:23.486 adding: Mythbntu804 as a client (events: 0)
2008-07-03 08:31:23.496 MainServer::HandleAnnounce Monitor
2008-07-03 08:31:23.506 adding: Mythbntu804 as a client (events: 1)
QDateTime::fromString: Parameter out of range
2008-07-03 08:45:05.899 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-07-03 08:56:40.899 MainServer::HandleAnnounce Monitor
2008-07-03 08:56:40.921 adding: Mythbntu804 as a client (events: 0)
2008-07-03 08:56:40.932 MainServer::HandleAnnounce Monitor
2008-07-03 08:56:40.942 adding: Mythbntu804 as a client (events: 1)
2008-07-03 08:56:40.959 MainServer::HandleAnnounce Playback
2008-07-03 08:56:40.986 adding: Mythbntu804 as a client (events: 0)
2008-07-03 08:56:41.010 TVRec(1): Changing from None to WatchingLiveTV
2008-07-03 08:56:41.029 TVRec(1): HW Tuner: 1->1
2008-07-03 08:56:41.285 New DB connection, total: 4
2008-07-03 08:56:41.302 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:56:42.704 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-03 08:56:42.769 NVR(/dev/video0) Error: Unknown audio codec
2008-07-03 08:56:42.814 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-03 08:56:42.817 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-03 08:57:22.830 TVRec(1): Changing from WatchingLiveTV to None
2008-07-03 08:57:22.853 Finished recording Unknown: channel 1006
2008-07-03 08:57:22.895 MythSocket(884cd0:-1): writeStringList: Error, socket went unconnected.
2008-07-03 08:58:08.193 Expiring 0 MBytes for 1006 @ Thu Jul 3 08:56:41 2008 => Unknown

---

### Post by tgm4883 on 2008-07-03
In mythtv-setup, what kind of tuner did you set the PVR-150 up as?

---

### Post by MikeB23930 on 2008-07-03
> **tgm4883 said:**
> In mythtv-setup, what kind of tuner did you set the PVR-150 up as?

tgm4883,

First off, thanks for your help.  I had left the Capture Cards/Card Type set to V4L.  I have now set it to MPEG-2 encoder card with the result that I get a poor quality picture that looks like a slide show with broken but understandable audio.  

Can you help with this problem?  In case you need it here is the mythbackend.log with Card Type set to MPEG-2:

2008-07-02 22:29:26.936 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-02 22:29:27.144 Empty LocalHostName.
2008-07-02 22:29:27.271 Using localhost value of Mythbntu804
2008-07-02 22:29:27.861 New DB connection, total: 1
2008-07-02 22:29:27.908 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:27.918 Closing DB connection named 'DBManager0'
2008-07-02 22:29:28.185 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:28.719 New DB connection, total: 2
2008-07-02 22:29:28.767 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:28.806 Current Schema Version: 1214
Starting up as the master server.
2008-07-02 22:29:35.451 New DB connection, total: 3
2008-07-02 22:29:35.788 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:35.968 New DB scheduler connection
2008-07-02 22:29:35.985 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:29:36.247 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-02 22:29:36.274 Main::Registering HttpStatus Extension
2008-07-02 22:29:36.358 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-02 22:29:36.396 Enabled verbose msgs:  important general
2008-07-02 22:29:36.527 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 22:29:39.248 Reschedule requested for id -1.
2008-07-02 22:29:40.090 Scheduled 0 items in 0.9 = 0.66 match + 0.23 place
2008-07-02 22:29:40.759 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-07-02 22:30:56.120 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 22:32:05.729 MainServer::HandleAnnounce Monitor
2008-07-02 22:32:05.748 adding: Mythbntu804 as a client (events: 0)
2008-07-02 22:32:05.758 MainServer::HandleAnnounce Monitor
2008-07-02 22:32:05.768 adding: Mythbntu804 as a client (events: 1)
2008-07-02 22:32:05.786 MainServer::HandleAnnounce Playback
2008-07-02 22:32:05.828 adding: Mythbntu804 as a client (events: 0)
2008-07-02 22:32:05.842 TVRec(1): Changing from None to WatchingLiveTV
2008-07-02 22:32:05.860 TVRec(1): HW Tuner: 1->1
2008-07-02 22:32:06.127 New DB connection, total: 4
2008-07-02 22:32:06.146 Connected to database 'mythconverg' at host: localhost
2008-07-02 22:32:07.567 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-02 22:32:07.635 NVR(/dev/video0) Error: Unknown audio codec
2008-07-02 22:32:07.694 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-02 22:32:07.709 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-02 22:32:47.791 TVRec(1): Changing from WatchingLiveTV to None
2008-07-02 22:32:47.831 Finished recording Unknown: channel 1006
2008-07-02 22:33:03.459 MainServer::HandleAnnounce Playback
2008-07-02 22:33:03.476 adding: Mythbntu804 as a client (events: 0)
2008-07-02 22:33:03.495 TVRec(1): Changing from None to WatchingLiveTV
2008-07-02 22:33:03.517 TVRec(1): HW Tuner: 1->1
2008-07-02 22:33:04.651 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-02 22:33:04.709 NVR(/dev/video0) Error: Unknown audio codec
2008-07-02 22:33:04.752 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-02 22:33:04.755 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-02 22:33:44.766 TVRec(1): Changing from WatchingLiveTV to None
2008-07-02 22:33:44.794 Finished recording Unknown: channel 1006
2008-07-02 22:33:44.855 MythSocket(8894e0:-1): writeStringList: Error, socket went unconnected.
2008-07-02 23:09:09.665 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-02 23:09:09.839 Empty LocalHostName.
2008-07-02 23:09:10.091 Using localhost value of Mythbntu804
2008-07-02 23:09:10.536 New DB connection, total: 1
2008-07-02 23:09:10.579 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:10.590 Closing DB connection named 'DBManager0'
2008-07-02 23:09:10.600 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:10.668 New DB connection, total: 2
2008-07-02 23:09:10.834 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:11.021 Current Schema Version: 1214
Starting up as the master server.
2008-07-02 23:09:16.556 New DB connection, total: 3
2008-07-02 23:09:16.701 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:16.862 New DB scheduler connection
2008-07-02 23:09:17.113 Connected to database 'mythconverg' at host: localhost
2008-07-02 23:09:17.710 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-02 23:09:17.772 Main::Registering HttpStatus Extension
2008-07-02 23:09:17.781 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-02 23:09:17.900 Enabled verbose msgs:  important general
2008-07-02 23:09:17.975 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 23:09:20.275 Reschedule requested for id -1.
2008-07-02 23:09:21.087 Scheduled 0 items in 0.8 = 0.45 match + 0.37 place
2008-07-02 23:09:21.397 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-07-02 23:10:37.949 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-02 23:10:38.034 Expiring 0 MBytes for 1006 @ Wed Jul 2 22:32:05 2008 => Unknown
2008-07-02 23:10:38.090 Expiring 0 MBytes for 1006 @ Wed Jul 2 22:33:03 2008 => Unknown
2008-07-02 23:10:43.493 MainServer::HandleAnnounce Monitor
2008-07-02 23:10:43.525 adding: Mythbntu804 as a client (events: 0)
2008-07-02 23:10:43.536 MainServer::HandleAnnounce Monitor
2008-07-02 23:10:43.546 adding: Mythbntu804 as a client (events: 1)
2008-07-03 08:28:34.343 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 08:28:34.500 Empty LocalHostName.
2008-07-03 08:28:34.847 Using localhost value of Mythbntu804
2008-07-03 08:28:35.389 New DB connection, total: 1
2008-07-03 08:28:35.427 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:35.770 Closing DB connection named 'DBManager0'
2008-07-03 08:28:36.049 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:36.127 New DB connection, total: 2
2008-07-03 08:28:36.139 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:36.318 Current Schema Version: 1214
Starting up as the master server.
2008-07-03 08:28:42.709 New DB connection, total: 3
2008-07-03 08:28:42.756 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:42.935 New DB scheduler connection
2008-07-03 08:28:42.985 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:28:43.163 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-03 08:28:43.173 Main::Registering HttpStatus Extension
2008-07-03 08:28:43.182 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-03 08:28:43.192 Enabled verbose msgs:  important general
2008-07-03 08:28:43.330 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 08:28:46.105 Reschedule requested for id -1.
2008-07-03 08:28:46.940 Scheduled 0 items in 0.8 = 0.68 match + 0.15 place
2008-07-03 08:28:48.078 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-07-03 08:30:05.006 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 08:31:23.460 MainServer::HandleAnnounce Monitor
2008-07-03 08:31:23.486 adding: Mythbntu804 as a client (events: 0)
2008-07-03 08:31:23.496 MainServer::HandleAnnounce Monitor
2008-07-03 08:31:23.506 adding: Mythbntu804 as a client (events: 1)
QDateTime::fromString: Parameter out of range
2008-07-03 08:45:05.899 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-07-03 08:56:40.899 MainServer::HandleAnnounce Monitor
2008-07-03 08:56:40.921 adding: Mythbntu804 as a client (events: 0)
2008-07-03 08:56:40.932 MainServer::HandleAnnounce Monitor
2008-07-03 08:56:40.942 adding: Mythbntu804 as a client (events: 1)
2008-07-03 08:56:40.959 MainServer::HandleAnnounce Playback
2008-07-03 08:56:40.986 adding: Mythbntu804 as a client (events: 0)
2008-07-03 08:56:41.010 TVRec(1): Changing from None to WatchingLiveTV
2008-07-03 08:56:41.029 TVRec(1): HW Tuner: 1->1
2008-07-03 08:56:41.285 New DB connection, total: 4
2008-07-03 08:56:41.302 Connected to database 'mythconverg' at host: localhost
2008-07-03 08:56:42.704 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-07-03 08:56:42.769 NVR(/dev/video0) Error: Unknown audio codec
2008-07-03 08:56:42.814 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-03 08:56:42.817 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-07-03 08:57:22.830 TVRec(1): Changing from WatchingLiveTV to None
2008-07-03 08:57:22.853 Finished recording Unknown: channel 1006
2008-07-03 08:57:22.895 MythSocket(884cd0:-1): writeStringList: Error, socket went unconnected.
2008-07-03 08:58:08.193 Expiring 0 MBytes for 1006 @ Thu Jul 3 08:56:41 2008 => Unknown
QDateTime::fromString: Parameter out of range
2008-07-03 09:00:08.228 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 17:11:56.697 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 17:11:56.871 Empty LocalHostName.
2008-07-03 17:11:57.235 Using localhost value of Mythbntu804
2008-07-03 17:11:57.716 New DB connection, total: 1
2008-07-03 17:11:57.729 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:11:57.888 Closing DB connection named 'DBManager0'
2008-07-03 17:11:58.078 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:11:58.134 New DB connection, total: 2
2008-07-03 17:11:58.353 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:11:58.499 Current Schema Version: 1214
Starting up as the master server.
2008-07-03 17:12:04.674 New DB connection, total: 3
2008-07-03 17:12:04.751 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:12:05.065 New DB scheduler connection
2008-07-03 17:12:05.085 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:12:05.293 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-03 17:12:05.302 Main::Registering HttpStatus Extension
2008-07-03 17:12:05.312 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-03 17:12:05.321 Enabled verbose msgs:  important general
2008-07-03 17:12:05.507 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 17:12:08.195 Reschedule requested for id -1.
2008-07-03 17:12:09.686 Scheduled 0 items in 1.5 = 1.22 match + 0.27 place
2008-07-03 17:12:10.004 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
2008-07-03 17:13:27.236 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 17:17:17.278 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 17:17:17.301 Empty LocalHostName.
2008-07-03 17:17:17.350 Using localhost value of Mythbntu804
2008-07-03 17:17:17.376 New DB connection, total: 1
2008-07-03 17:17:17.405 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:17:17.416 Closing DB connection named 'DBManager0'
2008-07-03 17:17:17.427 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:17:17.440 New DB connection, total: 2
2008-07-03 17:17:17.450 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:17:17.464 Current Schema Version: 1214
Starting up as the master server.
2008-07-03 17:17:17.499 New DB connection, total: 3
2008-07-03 17:17:17.512 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:17:17.677 New DB scheduler connection
2008-07-03 17:17:17.688 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:17:17.730 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-03 17:17:17.742 Main::Registering HttpStatus Extension
2008-07-03 17:17:17.753 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-03 17:17:17.764 Enabled verbose msgs:  important general
2008-07-03 17:17:17.777 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 17:17:20.710 Reschedule requested for id -1.
2008-07-03 17:17:20.757 Scheduled 0 items in 0.0 = 0.02 match + 0.03 place
2008-07-03 17:17:20.793 Seem to be woken up by USER
2008-07-03 17:18:43.137 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 17:18:43.153 Empty LocalHostName.
2008-07-03 17:18:43.191 Using localhost value of Mythbntu804
2008-07-03 17:18:43.222 New DB connection, total: 1
2008-07-03 17:18:43.239 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:18:43.250 Closing DB connection named 'DBManager0'
2008-07-03 17:18:43.261 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:18:43.273 New DB connection, total: 2
2008-07-03 17:18:43.284 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:18:43.297 Current Schema Version: 1214
Starting up as the master server.
2008-07-03 17:18:43.332 New DB connection, total: 3
2008-07-03 17:18:43.343 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:18:43.504 New DB scheduler connection
2008-07-03 17:18:43.515 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:18:43.560 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-03 17:18:43.572 Main::Registering HttpStatus Extension
2008-07-03 17:18:43.584 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-07-03 17:18:43.594 Enabled verbose msgs:  important general
2008-07-03 17:18:43.608 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-03 17:18:46.530 Reschedule requested for id -1.
2008-07-03 17:18:46.577 Scheduled 0 items in 0.0 = 0.02 match + 0.03 place
2008-07-03 17:18:46.614 Seem to be woken up by USER
2008-07-03 17:19:10.250 MainServer::HandleAnnounce Monitor
2008-07-03 17:19:10.269 adding: Mythbntu804 as a client (events: 0)
2008-07-03 17:19:10.279 MainServer::HandleAnnounce Monitor
2008-07-03 17:19:10.289 adding: Mythbntu804 as a client (events: 1)
2008-07-03 17:19:10.305 MainServer::HandleAnnounce Playback
2008-07-03 17:19:10.337 adding: Mythbntu804 as a client (events: 0)
2008-07-03 17:19:10.357 TVRec(1): Changing from None to WatchingLiveTV
2008-07-03 17:19:10.377 TVRec(1): HW Tuner: 1->1
2008-07-03 17:19:10.639 New DB connection, total: 4
2008-07-03 17:19:10.653 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:19:11.840 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-07-03 17:19:11.846 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-07-03 17:20:03.544 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-03 17:21:06.314 TVRec(1): HW Tuner: 1->1
2008-07-03 17:21:06.581 Finished recording Unknown: channel 1006
2008-07-03 17:21:07.635 Finished recording Unknown: channel 1006
2008-07-03 17:21:07.763 TVRec(1): RingBufferChanged()
2008-07-03 17:21:07.780 Finished recording Unknown: channel 1006
2008-07-03 17:21:07.808 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-03 17:21:07.815 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 17:21:07.860 Empty LocalHostName.
2008-07-03 17:21:07.869 Using localhost value of Mythbntu804
2008-07-03 17:21:07.885 New DB connection, total: 1
2008-07-03 17:21:07.902 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:21:07.913 Closing DB connection named 'DBManager0'
2008-07-03 17:21:07.924 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:21:07.935 New DB connection, total: 2
2008-07-03 17:21:07.951 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:21:07.970 Current Schema Version: 1214
2008-07-03 17:21:10.518 AFD: Opened codec 0x8d37e0, id(MPEG2VIDEO) type(Video)
2008-07-03 17:21:10.542 AFD: codec MP2 has 2 channels
2008-07-03 17:21:10.647 AFD: Opened codec 0x8d3bc0, id(MP2) type(Audio)
2008-07-03 17:21:10.713 Preview: Grabbed preview '/var/lib/mythtv/recordings/1006_20080703171910.mpg' 720x480@64s
2008-07-03 17:21:42.169 TVRec(1): HW Tuner: 1->1
2008-07-03 17:21:42.325 Finished recording Unknown: channel 1008
2008-07-03 17:21:43.381 Finished recording Unknown: channel 1008
2008-07-03 17:21:43.544 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-03 17:21:43.545 TVRec(1): RingBufferChanged()
2008-07-03 17:21:43.561 Empty LocalHostName.
2008-07-03 17:21:43.583 Using localhost value of Mythbntu804
2008-07-03 17:21:43.598 New DB connection, total: 1
2008-07-03 17:21:43.611 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:21:43.621 Closing DB connection named 'DBManager0'
2008-07-03 17:21:43.635 Finished recording Unknown: channel 1008
2008-07-03 17:21:43.635 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:21:43.672 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-03 17:21:43.702 New DB connection, total: 2
2008-07-03 17:21:43.735 Connected to database 'mythconverg' at host: localhost
2008-07-03 17:21:43.751 Current Schema Version: 1214
2008-07-03 17:21:46.242 AFD: Opened codec 0x8d3820, id(MPEG2VIDEO) type(Video)
2008-07-03 17:21:46.574 AFD: codec MP2 has 2 channels
2008-07-03 17:21:46.707 AFD: Opened codec 0x8d3c00, id(MP2) type(Audio)
2008-07-03 17:21:46.845 Preview: Grabbed preview '/var/lib/mythtv/recordings/1008_20080703172106.mpg' 720x480@64s
2008-07-03 17:22:04.106 Expiring 70 MBytes for 1006 @ Thu Jul 3 17:19:10 2008 => Unknown
2008-07-03 17:22:15.913 TVRec(1): Changing from WatchingLiveTV to None
2008-07-03 17:22:16.459 Finished recording Unknown: channel 1012
2008-07-03 17:24:04.561 Expiring 21 MBytes for 1008 @ Thu Jul 3 17:21:06 2008 => Unknown
2008-07-03 17:24:04.578 Expiring 19 MBytes for 1012 @ Thu Jul 3 17:21:42 2008 => Unknown
QDateTime::fromString: Parameter out of range
2008-07-03 17:32:00.799 MainServer::HandleAnnounce Monitor
2008-07-03 17:32:00.816 adding: Mythbntu804 as a client (events: 0)
2008-07-03 17:32:00.827 MainServer::HandleAnnounce Monitor
2008-07-03 17:32:00.837 adding: Mythbntu804 as a client (events: 1)
2008-07-03 17:32:31.254 MainServer::HandleAnnounce Monitor
2008-07-03 17:32:31.269 adding: Mythbntu804 as a client (events: 0)
2008-07-03 17:32:31.279 MainServer::HandleAnnounce Monitor
2008-07-03 17:32:31.289 adding: Mythbntu804 as a client (events: 1)

---

### Post by tgm4883 on 2008-07-03
Slideshow issues sound like your video card drivers aren't installed.  If the quality of the picture is poor, you probably need to increase the bitrate in the recording profile (in the frontend).  I tend to think it is rather low myself and have set it at 9000kbps

---

### Post by MikeB23930 on 2008-07-03
> **tgm4883 said:**
> Slideshow issues sound like your video card drivers aren't installed.  If the quality of the picture is poor, you probably need to increase the bitrate in the recording profile (in the frontend).  I tend to think it is rather low myself and have set it at 9000kbps

tgm4883,

Setting the recording bitrate for live TV to 9000kbps had no noticeable effect on either the audio or video.

I don't know for sure how to determine if the driver is loaded.  I did determine that lspci identifies the PVR 150 card as

Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

and lsmod | grep cx yields

cx25840                30096  0 
cx2341x                14596  1 ivtv
v4l2_common            21888  6 wm8775,cx25840,tuner,ivtv,cx2341x,videodev
eeprom_93cx6            3840  1 rt61pci
i2c_core               28544  12 wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ivtv,i2c_algo_bit,tveeprom,i2c_piix4

Do you know if the cx2341x entry means the correct driver is loaded?  If not, do you know how I could find out what the correct driver is and how I could determine whether it is loaded?

Thanks very much for all your help.

Mike

---

### Post by tgm4883 on 2008-07-04
Open mythbuntu-control-centre, click "Proprietary Drivers", then click "Launch Restricted Driver Manager".  You should be able to install any drivers you need in there.

Also, the cx drivers aren't for your PVR-150, but I wasn't asking about that anyway.

---

### Post by MikeB23930 on 2008-07-04
> **tgm4883 said:**
> Open mythbuntu-control-centre, click "Proprietary Drivers", then click "Launch Restricted Driver Manager".  You should be able to install any drivers you need in there.

Also, the cx drivers aren't for your PVR-150, but I wasn't asking about that anyway.

tgm4883,

I now have both smooth video and intelligible sound with my PVR150. Thank you very much for your help.

In case you, or others, are interested here is what worked for me.

Context:  My (relevant) hardware:  Asus M3A78-EMH HDMI motherboard with onboard ATI Radeon 3200 HD video card and ATI SBx00 sound card; AMD X2 64 5000+ cpu.

1.  Install and configure mythbuntu 8.04 from scratch choosing to install the fglrx driver during installation.  I chose to install a very simple without any addons so I wouldn't have to chase through so many menu items to try to find things.

2.  Upgrade to the 2.6.24-19 kernel.

3.  Restart with the new kernel and enable the fglrx video driver.

Voila, it worked.

Again, thanks for your help.

Mike

---

