---
title: "Not connecting to master backend"
date: 2008-03-21
forum: Mythbuntu
---

### Post by cross157 on 2008-03-21
Edit: I believe I solved this...and boy do I feel stupid. I figured out that I've been attempting to switch to channels that I don't receive on my cable box. I went through all my channels using a regular tv and double checked that the channels I don't get are deleted from the mysql database. Using this mysql guide: [http://www.ilikelinux.com/tips-and-howtos/tips-for-using-mysql-with-mythtv/](http://www.ilikelinux.com/tips-and-howtos/tips-for-using-mysql-with-mythtv/)

Maybe this will help someone else.


Original Post:
Help! I can't watch live tv through Mythtv. I don't know what is going on. I've had my frontend/backend/desktop setup going for many months now, but I don't watch live tv often just recordings. Today when I tried I get this error: "The connection to the master backend server has gone away for some reason.. Is it running?"

I haven't changed my setup or settings, but I do remember a recent update through Update Manager for mysql. Did anyone else experience a problem with Myth TV after that?

Here's my latest log file, I don't know enough to make sense of it:

```
2008-03-21 07:35:58.399 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-03-21 07:35:59.855 TFW, Error: Write() -- IOBOUND end
2008-03-21 07:36:33.388 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-03-21 07:36:34.743 TFW, Error: Write() -- IOBOUND end
2008-03-21 07:37:53.466 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-03-21 07:37:54.928 TFW, Error: Write() -- IOBOUND end
2008-03-21 07:38:33.508 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-03-21 07:38:33.681 TFW, Error: Write() -- IOBOUND end
2008-03-21 07:47:16.122 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 08:00:00.383 TVRec(1): Changing from RecordingOnly to None
2008-03-21 08:00:00.480 Finished recording Billiards "2004 WPBA Classic Tour - Florida Classic, Second Semifinal": channel 1407
2008-03-21 08:00:00.542 Reschedule requested for id 0.
2008-03-21 08:00:00.661 Finished recording Billiards "2004 WPBA Classic Tour - Florida Classic, Second Semifinal": channel 1407
2008-03-21 08:00:03.882 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 08:00:04.117 Empty LocalHostName.
2008-03-21 08:00:04.169 Using localhost value of cross157-desktop
2008-03-21 08:00:04.544 New DB connection, total: 1
2008-03-21 08:00:04.689 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 08:00:04.800 Closing DB connection named 'DBManager0'
2008-03-21 08:00:04.840 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 08:00:04.920 New DB connection, total: 2
2008-03-21 08:00:04.949 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 08:00:05.049 Current Schema Version: 1214
2008-03-21 08:00:08.502 AFD: Opened codec 0x82a3b00, id(MPEG2VIDEO) type(Video)
2008-03-21 08:00:08.511 AFD: codec MP2 has 2 channels
2008-03-21 08:00:08.519 AFD: Opened codec 0x82a3f70, id(MP2) type(Audio)
2008-03-21 08:00:09.237 Scheduled 395 items in 8.7 = 0.02 match + 8.67 place
2008-03-21 08:00:09.276 Preview: Grabbed preview '/var/lib/mythtv/recordings/1407_20080321070000.mpg' 480x480@64s
2008-03-21 08:00:20.874 [mpeg2video @ 0xb7425148]ac-tex damaged at 25 27
2008-03-21 08:00:20.877 [mpeg2video @ 0xb7425148]Warning MVs not available
2008-03-21 08:00:22.128 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 08:00:22.138 Empty LocalHostName.
2008-03-21 08:00:22.140 Using localhost value of cross157-desktop
2008-03-21 08:00:22.169 New DB connection, total: 1
2008-03-21 08:00:22.180 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 08:00:22.185 Closing DB connection named 'DBManager0'
2008-03-21 08:00:22.188 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 08:00:22.193 New DB connection, total: 2
2008-03-21 08:00:22.195 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 08:00:22.201 Current Schema Version: 1214
2008-03-21 08:00:24.917 AFD: Opened codec 0x82a3b40, id(MPEG2VIDEO) type(Video)
2008-03-21 08:00:24.919 AFD: codec MP2 has 2 channels
2008-03-21 08:00:24.921 AFD: Opened codec 0x82a3fb0, id(MP2) type(Audio)
2008-03-21 08:00:25.162 Preview: Grabbed preview '/var/lib/mythtv/recordings/1407_20080321070000.mpg' 480x480@64s
2008-03-21 08:02:16.471 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 08:14:42.631 MainServer::HandleAnnounce Playback
2008-03-21 08:14:42.653 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:14:42.704 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:14:42.706 adding: cross157-desktop as a remote file transfer
2008-03-21 08:14:45.841 MythSocket(8c033e8:-1): writeStringList: Error, socket went unconnected.
2008-03-21 08:14:48.337 Reschedule requested for id 0.
2008-03-21 08:14:51.657 Scheduled 395 items in 3.3 = 0.04 match + 3.27 place
2008-03-21 08:15:15.239 MainServer::HandleAnnounce Playback
2008-03-21 08:15:15.243 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:15:15.246 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:15:15.251 adding: cross157-desktop as a remote file transfer
2008-03-21 08:15:16.943 MainServer::HandleAnnounce Playback
2008-03-21 08:15:16.948 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:15:16.950 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:15:16.954 adding: cross157-desktop as a remote file transfer
2008-03-21 08:15:20.752 Reschedule requested for id 0.
2008-03-21 08:15:22.895 MainServer::HandleAnnounce Playback
2008-03-21 08:15:23.012 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:15:23.014 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:15:23.018 adding: cross157-desktop as a remote file transfer
2008-03-21 08:15:24.072 Scheduled 395 items in 3.3 = 0.01 match + 3.30 place
2008-03-21 08:15:32.779 MainServer::HandleAnnounce Playback
2008-03-21 08:15:32.783 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:15:32.823 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:15:32.858 adding: cross157-desktop as a remote file transfer
2008-03-21 08:15:34.263 MainServer::HandleAnnounce Playback
2008-03-21 08:15:34.265 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:15:34.267 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:15:34.271 adding: cross157-desktop as a remote file transfer
2008-03-21 08:17:16.772 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 08:32:17.781 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 08:32:22.378 MainServer::HandleAnnounce Playback
2008-03-21 08:32:22.381 adding: cross157-desktop as a client (events: 0)
2008-03-21 08:32:22.384 MainServer::HandleAnnounce FileTransfer
2008-03-21 08:32:22.386 adding: cross157-desktop as a remote file transfer
2008-03-21 08:47:19.228 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 09:02:21.049 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 09:17:22.001 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 09:32:22.981 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 09:47:23.975 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 10:02:24.944 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 10:17:25.894 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 10:32:26.876 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 10:47:28.457 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 11:02:29.378 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 11:17:30.362 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 11:32:31.314 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 11:47:32.296 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:02:36.461 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:11:42.767 MainServer::HandleAnnounce Playback
2008-03-21 12:11:42.796 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:11:42.861 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:11:42.890 TVRec(1): HW Tuner: 1->1
407
2008-03-21 12:11:44.331 ret_pid(10703) child(10703) status(0x0)
2008-03-21 12:11:44.336 External Tuning program exited with no error
2008-03-21 12:11:46.560 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:11:46.566 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:14:16.946 TVRec(1): HW Tuner: 1->1
2008-03-21 12:14:18.297 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:19.305 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:20.309 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:21.313 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:22.317 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:23.321 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:24.325 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:25.329 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:26.333 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:27.337 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:28.341 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:29.345 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:30.349 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:31.353 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:32.357 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:33.361 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:34.365 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:35.232 MainServer::HandleAnnounce Monitor
2008-03-21 12:14:35.234 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:14:35.369 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:36.377 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:37.381 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:38.385 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:39.389 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:40.393 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:41.397 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:42.401 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:43.405 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:44.409 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:45.378 MainServer::HandleAnnounce Monitor
2008-03-21 12:14:45.382 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:14:45.421 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:46.445 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:47.449 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:48.453 ret_pid(0) child(10737) status(0x0)
2008-03-21 12:14:48.454 External Tuning program timed out, killing
2008-03-21 12:14:48.457 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 12:14:48.471 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:14:48.484 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:14:48 2008) endts(Fri Mar 21 12:14:48 2008)
             recstartts(Fri Mar 21 12:14:48 2008) recendts(Fri Mar 21 12:14:48 2008)
             title()
2008-03-21 12:14:49.698 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:14:50.057 TVRec(1): RingBufferChanged()
2008-03-21 12:14:50.073 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:14:50.100 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:14:50.210 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:14:51.114 Finished recording : channel 4294967295
2008-03-21 12:14:51.267 MythSocket(8da4bd0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:14:51.267 MythSocket(aeb96308:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:14:52.168 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:14:52.301 Empty LocalHostName.
2008-03-21 12:14:52.302 Using localhost value of cross157-desktop
2008-03-21 12:14:52.663 New DB connection, total: 1
2008-03-21 12:14:52.792 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:14:52.796 Closing DB connection named 'DBManager0'
2008-03-21 12:14:52.799 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:14:52.818 New DB connection, total: 2
2008-03-21 12:14:52.820 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:14:52.828 Current Schema Version: 1214
2008-03-21 12:14:55.775 AFD: Opened codec 0x82a3880, id(MPEG2VIDEO) type(Video)
2008-03-21 12:14:55.777 AFD: codec MP2 has 2 channels
2008-03-21 12:14:55.778 AFD: Opened codec 0x82a3cf0, id(MP2) type(Audio)
2008-03-21 12:14:56.085 Preview: Grabbed preview '/var/lib/mythtv/recordings/1407_20080321121145.mpg' 720x480@64s
Communication failed after 5 tries
407
2008-03-21 12:16:21.842 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:16:22.577 Empty LocalHostName.
2008-03-21 12:16:22.580 Using localhost value of cross157-desktop
2008-03-21 12:16:22.619 New DB connection, total: 1
2008-03-21 12:16:22.645 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:16:22.649 Closing DB connection named 'DBManager0'
2008-03-21 12:16:22.652 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:16:22.657 New DB connection, total: 2
2008-03-21 12:16:22.659 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:16:22.667 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 12:16:22.785 New DB connection, total: 3
2008-03-21 12:16:22.788 Connected to database 'mythconverg' at host: 127.0.0.1
407
2008-03-21 12:16:24.222 ret_pid(10819) child(10819) status(0x0)
2008-03-21 12:16:24.227 External Tuning program exited with no error
2008-03-21 12:16:24.291 New DB scheduler connection
2008-03-21 12:16:24.293 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:16:24.359 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 12:16:24.360 Main::Registering HttpStatus Extension
2008-03-21 12:16:24.361 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 12:16:24.362 Enabled verbose msgs:  important general
2008-03-21 12:16:24.369 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:16:27.379 Reschedule requested for id -1.
2008-03-21 12:16:38.873 Scheduled 395 items in 11.5 = 9.16 match + 2.33 place
2008-03-21 12:16:38.893 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
2008-03-21 12:16:44.481 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:14:48 2008 => 
2008-03-21 12:17:44.894 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:26:50.459 MainServer::HandleAnnounce Monitor
2008-03-21 12:26:51.886 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:26:51.896 MainServer::HandleAnnounce Monitor
2008-03-21 12:26:51.941 adding: cross157-desktop as a client (events: 1)
2008-03-21 12:26:52.037 MythSocket(83e1058:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:26:52.038 Reschedule requested for id -1.
2008-03-21 12:26:58.130 Scheduled 395 items in 6.1 = 1.42 match + 4.66 place
2008-03-21 12:32:46.524 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:35:48.585 MainServer::HandleAnnounce Monitor
2008-03-21 12:35:48.589 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:35:48.591 MainServer::HandleAnnounce Monitor
2008-03-21 12:35:48.596 adding: cross157-desktop as a client (events: 1)
2008-03-21 12:35:48.611 MainServer::HandleAnnounce Playback
2008-03-21 12:35:48.614 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:35:48.620 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:35:48.637 TVRec(1): HW Tuner: 1->1
407
2008-03-21 12:35:50.055 ret_pid(11034) child(11034) status(0x0)
2008-03-21 12:35:50.060 External Tuning program exited with no error
2008-03-21 12:35:51.591 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:35:51.619 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:36:57.964 TVRec(1): HW Tuner: 1->1
2008-03-21 12:36:59.324 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:00.332 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:01.336 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:02.340 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:03.344 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:04.348 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:05.352 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:06.356 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:07.360 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:08.364 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:09.368 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:10.376 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:11.380 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:12.384 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:13.388 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:14.392 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:15.396 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:16.079 MainServer::HandleAnnounce Monitor
2008-03-21 12:37:16.082 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:37:16.400 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:17.408 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:18.412 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:19.416 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:20.420 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:21.424 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:22.428 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:23.432 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:24.437 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:25.441 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:26.445 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:27.449 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:28.434 MainServer::HandleAnnounce Monitor
2008-03-21 12:37:28.438 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:37:28.453 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:29.461 ret_pid(0) child(11046) status(0x0)
2008-03-21 12:37:29.462 External Tuning program timed out, killing
2008-03-21 12:37:29.465 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 12:37:29.499 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:37:29.523 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:37:29 2008) endts(Fri Mar 21 12:37:29 2008)
             recstartts(Fri Mar 21 12:37:29 2008) recendts(Fri Mar 21 12:37:29 2008)
             title()
2008-03-21 12:37:30.658 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:37:31.048 TVRec(1): RingBufferChanged()
2008-03-21 12:37:31.064 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:37:31.094 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:37:31.177 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:37:31.206 Empty LocalHostName.
2008-03-21 12:37:31.209 Using localhost value of cross157-desktop
2008-03-21 12:37:31.229 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:37:31.386 New DB connection, total: 1
2008-03-21 12:37:31.456 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:37:31.460 Closing DB connection named 'DBManager0'
2008-03-21 12:37:31.463 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:37:31.471 New DB connection, total: 2
2008-03-21 12:37:31.473 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:37:31.481 Current Schema Version: 1214
2008-03-21 12:37:32.059 Finished recording : channel 4294967295
2008-03-21 12:37:32.074 MythSocket(84f8618:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:37:32.074 MythSocket(8256a88:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:37:34.420 AFD: Opened codec 0x82a3880, id(MPEG2VIDEO) type(Video)
2008-03-21 12:37:34.426 AFD: codec MP2 has 2 channels
2008-03-21 12:37:34.427 AFD: Opened codec 0x82a3cf0, id(MP2) type(Audio)
2008-03-21 12:37:34.611 Preview: Grabbed preview '/var/lib/mythtv/recordings/1407_20080321123550.mpg' 720x480@64s
Communication failed after 5 tries
407
2008-03-21 12:38:57.605 MainServer::HandleAnnounce Monitor
2008-03-21 12:38:57.607 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:38:57.610 MainServer::HandleAnnounce Monitor
2008-03-21 12:38:57.615 adding: cross157-desktop as a client (events: 1)
2008-03-21 12:38:57.632 MainServer::HandleAnnounce Playback
2008-03-21 12:38:57.634 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:38:57.639 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:38:57.654 TVRec(1): HW Tuner: 1->1
407
2008-03-21 12:38:59.050 ret_pid(11101) child(11101) status(0x0)
2008-03-21 12:38:59.054 External Tuning program exited with no error
2008-03-21 12:39:00.264 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:39:00.270 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:39:07.998 TVRec(1): HW Tuner: 1->1
2008-03-21 12:39:09.338 ret_pid(0) child(11119) status(0x0)
2008-03-21 12:39:10.350 ret_pid(0) child(11119) status(0x0)
2008-03-21 12:39:11.358 ret_pid(0) child(11119) status(0x0)
63
2008-03-21 12:39:12.366 ret_pid(11119) child(11119) status(0x0)
2008-03-21 12:39:12.371 External Tuning program exited with no error
2008-03-21 12:39:12.417 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:39:13.676 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:39:13.754 TVRec(1): RingBufferChanged()
2008-03-21 12:39:13.773 Finished recording Who's Number 1? "Greatest Performances": channel 1407
2008-03-21 12:39:13.848 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:39:14.344 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:39:14.349 Empty LocalHostName.
2008-03-21 12:39:14.351 Using localhost value of cross157-desktop
2008-03-21 12:39:14.380 New DB connection, total: 1
2008-03-21 12:39:14.393 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:39:14.396 Closing DB connection named 'DBManager0'
2008-03-21 12:39:14.400 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:39:14.404 New DB connection, total: 2
2008-03-21 12:39:14.407 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:39:14.421 Current Schema Version: 1214
2008-03-21 12:39:17.740 AFD: Opened codec 0x82a3880, id(MPEG2VIDEO) type(Video)
2008-03-21 12:39:17.774 AFD: codec MP2 has 2 channels
2008-03-21 12:39:17.893 AFD: Opened codec 0x82a3cf0, id(MP2) type(Audio)
2008-03-21 12:39:19.057 Preview: Grabbed preview '/var/lib/mythtv/recordings/1407_20080321123859.mpg' 720x480@64s
2008-03-21 12:39:31.970 TVRec(1): HW Tuner: 1->1
2008-03-21 12:39:33.306 ret_pid(0) child(11126) status(0x0)
2008-03-21 12:39:34.318 ret_pid(0) child(11126) status(0x0)
2008-03-21 12:39:35.326 ret_pid(0) child(11126) status(0x0)
501
2008-03-21 12:39:36.334 ret_pid(11126) child(11126) status(0x0)
2008-03-21 12:39:36.339 External Tuning program exited with no error
2008-03-21 12:39:36.401 Finished recording MADtv: channel 1063
2008-03-21 12:39:37.545 Finished recording MADtv: channel 1063
2008-03-21 12:39:37.662 TVRec(1): RingBufferChanged()
2008-03-21 12:39:37.677 Finished recording MADtv: channel 1063
2008-03-21 12:39:37.740 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:39:38.113 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:39:38.117 Empty LocalHostName.
2008-03-21 12:39:38.119 Using localhost value of cross157-desktop
2008-03-21 12:39:38.148 New DB connection, total: 1
2008-03-21 12:39:38.167 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:39:38.171 Closing DB connection named 'DBManager0'
2008-03-21 12:39:38.174 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:39:38.179 New DB connection, total: 2
2008-03-21 12:39:38.181 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:39:38.188 Current Schema Version: 1214
2008-03-21 12:39:45.942 AFD: Opened codec 0x82a3b20, id(MPEG2VIDEO) type(Video)
2008-03-21 12:39:46.107 AFD: codec MP2 has 2 channels
2008-03-21 12:39:46.385 AFD: Opened codec 0x82a3f90, id(MP2) type(Audio)
2008-03-21 12:39:47.553 Preview: Grabbed preview '/var/lib/mythtv/recordings/1063_20080321123912.mpg' 720x480@64s
2008-03-21 12:39:52.487 TVRec(1): HW Tuner: 1->1
2008-03-21 12:39:53.818 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:39:54.826 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:39:55.834 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:39:56.842 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:39:57.850 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:39:58.858 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:39:59.866 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:00.874 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:01.878 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:02.882 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:03.886 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:04.890 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:05.894 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:06.898 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:07.902 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:08.906 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:09.372 MainServer::HandleAnnounce Monitor
2008-03-21 12:40:09.381 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:40:09.910 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:10.918 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:11.922 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:12.926 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:13.930 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:14.939 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:16.039 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:17.043 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:18.046 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:19.050 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:20.054 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:21.059 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:22.062 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:23.067 ret_pid(0) child(11135) status(0x0)
2008-03-21 12:40:23.068 External Tuning program timed out, killing
2008-03-21 12:40:23.071 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 12:40:23.116 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:40:23.133 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:40:23 2008) endts(Fri Mar 21 12:40:23 2008)
             recstartts(Fri Mar 21 12:40:23 2008) recendts(Fri Mar 21 12:40:23 2008)
             title()
2008-03-21 12:40:24.247 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:40:24.383 TVRec(1): RingBufferChanged()
2008-03-21 12:40:24.398 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:40:24.441 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:40:24.571 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:40:24.723 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:40:24.729 Empty LocalHostName.
2008-03-21 12:40:24.730 Using localhost value of cross157-desktop
2008-03-21 12:40:24.772 New DB connection, total: 1
2008-03-21 12:40:24.783 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:40:24.787 Closing DB connection named 'DBManager0'
2008-03-21 12:40:24.790 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:40:24.795 New DB connection, total: 2
2008-03-21 12:40:24.797 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:40:24.805 Current Schema Version: 1214
2008-03-21 12:40:25.416 Finished recording : channel 4294967295
2008-03-21 12:40:25.439 MythSocket(830a3e0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:40:25.439 MythSocket(8355ce0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:40:27.598 AFD: Opened codec 0x82a3c50, id(MPEG2VIDEO) type(Video)
2008-03-21 12:40:27.600 AFD: codec MP2 has 2 channels
2008-03-21 12:40:27.601 AFD: Opened codec 0x82a40c0, id(MP2) type(Audio)
2008-03-21 12:40:27.788 Preview: Grabbed preview '/var/lib/mythtv/recordings/1501_20080321123936.mpg' 720x480@64s
2008-03-21 12:40:46.793 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:37:29 2008 => 
2008-03-21 12:40:46.796 Expiring 12 MBytes for 1407 @ Fri Mar 21 12:00:00 2008 => Who's Number 1? "Greatest Performances"
Communication failed after 5 tries
501
2008-03-21 12:41:09.120 MainServer::HandleAnnounce Monitor
2008-03-21 12:41:09.129 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:41:10.234 MainServer::HandleAnnounce Playback
2008-03-21 12:41:10.237 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:41:10.242 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:41:10.254 TVRec(1): HW Tuner: 1->1
501
2008-03-21 12:41:11.671 ret_pid(11151) child(11151) status(0x0)
2008-03-21 12:41:11.676 External Tuning program exited with no error
2008-03-21 12:41:13.077 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:41:13.119 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:41:23.864 TVRec(1): HW Tuner: 1->1
2008-03-21 12:41:25.167 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:26.175 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:27.183 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:28.207 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:29.255 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:30.287 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:31.295 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:32.315 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:33.319 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:34.329 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:35.339 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:36.343 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:37.347 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:38.351 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:39.355 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:39.906 MainServer::HandleAnnounce Monitor
2008-03-21 12:41:39.909 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:41:40.359 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:41.367 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:42.371 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:43.375 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:44.379 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:45.383 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:46.387 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:47.391 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:48.395 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:49.399 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:50.404 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:51.407 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:52.411 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:53.415 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:54.420 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:55.424 ret_pid(0) child(11160) status(0x0)
2008-03-21 12:41:55.448 External Tuning program timed out, killing
2008-03-21 12:41:55.452 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 12:41:55.684 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:41:55.697 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:41:55 2008) endts(Fri Mar 21 12:41:55 2008)
             recstartts(Fri Mar 21 12:41:55 2008) recendts(Fri Mar 21 12:41:55 2008)
             title()
2008-03-21 12:41:56.989 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:41:57.147 TVRec(1): RingBufferChanged()
2008-03-21 12:41:57.166 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:41:57.258 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:41:57.440 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:41:58.102 Finished recording : channel 4294967295
2008-03-21 12:41:58.116 MythSocket(84171f8:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:41:58.124 MythSocket(83c34d0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:41:58.919 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:41:59.325 Empty LocalHostName.
2008-03-21 12:41:59.425 Using localhost value of cross157-desktop
2008-03-21 12:41:59.475 New DB connection, total: 1
2008-03-21 12:41:59.551 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:41:59.695 Closing DB connection named 'DBManager0'
2008-03-21 12:41:59.810 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:42:00.038 New DB connection, total: 2
2008-03-21 12:42:00.098 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:42:00.863 Current Schema Version: 1214
2008-03-21 12:42:04.958 AFD: Opened codec 0x82a3d60, id(MPEG2VIDEO) type(Video)
2008-03-21 12:42:05.060 AFD: codec MP2 has 2 channels
2008-03-21 12:42:05.155 AFD: Opened codec 0x82a4310, id(MP2) type(Audio)
2008-03-21 12:42:05.830 Preview: Grabbed preview '/var/lib/mythtv/recordings/1501_20080321124111.mpg' 720x480@64s
Communication failed after 5 tries
501
2008-03-21 12:42:46.867 Expiring 33 MBytes for 1063 @ Fri Mar 21 12:30:00 2008 => MADtv
2008-03-21 12:42:46.870 Expiring 27 MBytes for 1501 @ Fri Mar 21 12:30:00 2008 => The Fabulous Dorseys
2008-03-21 12:42:46.887 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:40:23 2008 => 
2008-03-21 12:44:34.714 MainServer::HandleAnnounce Monitor
2008-03-21 12:44:34.719 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:44:35.883 MainServer::HandleAnnounce Playback
2008-03-21 12:44:35.887 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:44:35.891 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:44:35.903 TVRec(1): HW Tuner: 1->1
501
2008-03-21 12:44:37.305 ret_pid(11191) child(11191) status(0x0)
2008-03-21 12:44:37.311 External Tuning program exited with no error
2008-03-21 12:44:38.655 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:44:38.898 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:44:46.467 TVRec(1): HW Tuner: 1->1
2008-03-21 12:44:46.959 Expiring 15 MBytes for 1501 @ Fri Mar 21 12:30:00 2008 => The Fabulous Dorseys
2008-03-21 12:44:46.964 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:41:55 2008 => 
2008-03-21 12:44:47.782 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:48.789 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:49.797 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:50.805 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:51.814 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:52.821 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:53.829 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:54.838 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:55.845 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:56.850 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:57.854 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:58.858 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:44:59.862 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:00.866 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:01.870 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:02.874 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:03.878 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:04.882 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:05.886 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:06.890 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:07.894 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:08.898 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:09.902 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:10.910 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:11.914 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:12.930 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:13.934 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:14.942 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:16.006 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:17.042 ret_pid(0) child(11200) status(0x0)
2008-03-21 12:45:17.044 External Tuning program timed out, killing
2008-03-21 12:45:17.046 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 12:45:17.064 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:45:17.078 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:45:17 2008) endts(Fri Mar 21 12:45:17 2008)
             recstartts(Fri Mar 21 12:45:17 2008) recendts(Fri Mar 21 12:45:17 2008)
             title()
2008-03-21 12:45:18.190 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:45:18.265 TVRec(1): RingBufferChanged()
2008-03-21 12:45:18.280 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:45:18.438 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:45:18.634 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:45:18.642 Empty LocalHostName.
2008-03-21 12:45:18.644 Using localhost value of cross157-desktop
2008-03-21 12:45:18.672 New DB connection, total: 1
2008-03-21 12:45:18.684 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:45:18.688 Closing DB connection named 'DBManager0'
2008-03-21 12:45:18.691 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:45:18.695 New DB connection, total: 2
2008-03-21 12:45:18.697 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:45:18.705 Current Schema Version: 1214
2008-03-21 12:45:19.251 Finished recording : channel 4294967295
2008-03-21 12:45:19.262 MythSocket(83cde40:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:45:19.265 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:45:21.472 AFD: Opened codec 0x82a3c50, id(MPEG2VIDEO) type(Video)
2008-03-21 12:45:21.477 AFD: codec MP2 has 2 channels
2008-03-21 12:45:21.478 AFD: Opened codec 0x82a40c0, id(MP2) type(Audio)
2008-03-21 12:45:21.665 Preview: Grabbed preview '/var/lib/mythtv/recordings/1501_20080321124437.mpg' 720x480@64s
2008-03-21 12:45:29.381 MainServer::HandleAnnounce Playback
2008-03-21 12:45:29.384 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:45:29.488 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:45:29.502 TVRec(1): HW Tuner: 1->1
2008-03-21 12:45:29.510 New DB connection, total: 4
2008-03-21 12:45:29.513 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:45:30.934 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:31.938 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:32.942 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:33.946 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:34.950 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:35.954 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:36.958 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:37.962 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:38.966 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:39.970 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:40.974 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:41.978 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:42.982 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:43.986 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:44.990 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:45.994 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:46.998 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:48.002 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:49.006 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:50.010 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:51.014 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:52.018 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:53.022 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:54.026 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:55.030 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:56.034 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:57.038 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:58.042 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:45:59.046 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:46:00.050 ret_pid(0) child(11213) status(0x0)
2008-03-21 12:46:00.052 External Tuning program timed out, killing
2008-03-21 12:46:00.054 TVRec(1) Error: Failed to set channel to 501.
2008-03-21 12:46:00.156 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:46:00 2008) endts(Fri Mar 21 12:46:00 2008)
             recstartts(Fri Mar 21 12:46:00 2008) recendts(Fri Mar 21 12:46:00 2008)
             title()
2008-03-21 12:46:01.327 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:46:01.336 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:46:01.478 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:46:02.304 Finished recording : channel 4294967295
Communication failed after 5 tries
501
2008-03-21 12:46:02.319 MythSocket(83bcaa0:-1): writeStringList: Error, socket went unconnected.
501
2008-03-21 12:46:47.874 Expiring 13 MBytes for 1501 @ Fri Mar 21 12:30:00 2008 => The Fabulous Dorseys
2008-03-21 12:46:47.888 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:45:17 2008 => 
2008-03-21 12:47:47.905 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 12:48:47.956 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:46:00 2008 => 
2008-03-21 12:51:06.391 MainServer::HandleAnnounce Monitor
2008-03-21 12:51:06.395 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:51:06.397 MainServer::HandleAnnounce Monitor
2008-03-21 12:51:06.399 adding: cross157-desktop as a client (events: 1)
2008-03-21 12:51:06.424 MainServer::HandleAnnounce Playback
2008-03-21 12:51:06.426 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:51:06.432 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:51:06.444 TVRec(1): HW Tuner: 1->1
501
2008-03-21 12:51:07.850 ret_pid(11299) child(11299) status(0x0)
2008-03-21 12:51:07.855 External Tuning program exited with no error
2008-03-21 12:51:09.147 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:51:09.176 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:51:15.263 TVRec(1): HW Tuner: 1->1
2008-03-21 12:51:16.578 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:17.586 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:18.590 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:19.598 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:20.606 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:21.610 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:22.614 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:23.618 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:24.622 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:25.626 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:26.630 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:27.638 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:28.678 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:29.690 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:30.698 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:31.702 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:32.712 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:33.714 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:34.718 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:35.722 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:36.345 MainServer::HandleAnnounce Monitor
2008-03-21 12:51:36.351 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:51:36.726 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:37.734 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:38.782 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:39.786 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:40.790 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:41.794 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:42.798 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:43.802 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:44.806 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:45.810 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:46.687 MainServer::HandleAnnounce Monitor
2008-03-21 12:51:46.692 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:51:46.814 ret_pid(0) child(11308) status(0x0)
2008-03-21 12:51:46.834 External Tuning program timed out, killing
2008-03-21 12:51:46.846 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 12:51:46.859 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:51:46.874 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 12:51:46 2008) endts(Fri Mar 21 12:51:46 2008)
             recstartts(Fri Mar 21 12:51:46 2008) recendts(Fri Mar 21 12:51:46 2008)
             title()
2008-03-21 12:51:48.010 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:51:48.156 TVRec(1): RingBufferChanged()
2008-03-21 12:51:48.174 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 12:51:48.220 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 12:51:48.355 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 12:51:48.528 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 12:51:48.533 Empty LocalHostName.
2008-03-21 12:51:48.534 Using localhost value of cross157-desktop
2008-03-21 12:51:48.573 New DB connection, total: 1
2008-03-21 12:51:48.614 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:51:48.617 Closing DB connection named 'DBManager0'
2008-03-21 12:51:48.621 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:51:48.626 New DB connection, total: 2
2008-03-21 12:51:48.628 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 12:51:48.636 Current Schema Version: 1214
2008-03-21 12:51:49.614 Finished recording : channel 4294967295
2008-03-21 12:51:49.656 MythSocket(83ba6e0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:51:50.101 MythSocket(8286f20:-1): writeStringList: Error, socket went unconnected.
2008-03-21 12:51:53.879 AFD: Opened codec 0x82a3d30, id(MPEG2VIDEO) type(Video)
2008-03-21 12:51:53.891 AFD: codec MP2 has 2 channels
2008-03-21 12:51:53.893 AFD: Opened codec 0x82a41a0, id(MP2) type(Audio)
2008-03-21 12:51:54.212 Preview: Grabbed preview '/var/lib/mythtv/recordings/1501_20080321125107.mpg' 720x480@64s
Communication failed after 5 tries
501
2008-03-21 12:54:48.082 Expiring 10 MBytes for 1501 @ Fri Mar 21 12:30:00 2008 => The Fabulous Dorseys
2008-03-21 12:54:48.086 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 12:51:46 2008 => 
2008-03-21 12:59:39.147 MainServer::HandleAnnounce Playback
2008-03-21 12:59:39.148 adding: cross157-desktop as a client (events: 0)
2008-03-21 12:59:39.154 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 12:59:39.171 TVRec(1): HW Tuner: 1->1
501
2008-03-21 12:59:40.600 ret_pid(11359) child(11359) status(0x0)
2008-03-21 12:59:40.604 External Tuning program exited with no error
2008-03-21 12:59:41.935 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 12:59:41.946 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:00:02.911 TVRec(1): HW Tuner: 1->1
2008-03-21 13:00:04.248 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:05.256 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:06.260 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:07.264 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:08.268 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:09.272 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:10.280 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:11.284 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:12.288 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:13.292 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:14.296 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:15.300 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:16.304 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:17.309 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:18.316 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:19.320 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:20.324 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:21.328 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:22.332 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:23.336 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:24.340 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:25.344 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:26.348 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:27.352 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:28.356 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:29.360 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:30.364 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:31.368 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:32.372 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:33.376 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:34.380 ret_pid(0) child(11368) status(0x0)
2008-03-21 13:00:34.387 External Tuning program timed out, killing
2008-03-21 13:00:34.401 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:00:34.422 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 13:00:34.458 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:00:34 2008) endts(Fri Mar 21 13:00:34 2008)
             recstartts(Fri Mar 21 13:00:34 2008) recendts(Fri Mar 21 13:00:34 2008)
             title()
2008-03-21 13:00:35.563 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 13:00:35.670 TVRec(1): RingBufferChanged()
2008-03-21 13:00:35.684 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 13:00:35.726 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:00:35.842 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:00:36.283 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 13:00:36.287 Empty LocalHostName.
2008-03-21 13:00:36.288 Using localhost value of cross157-desktop
2008-03-21 13:00:36.321 New DB connection, total: 1
2008-03-21 13:00:36.333 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:00:36.337 Closing DB connection named 'DBManager0'
2008-03-21 13:00:36.340 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:00:36.346 New DB connection, total: 2
2008-03-21 13:00:36.348 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:00:36.357 Current Schema Version: 1214
2008-03-21 13:00:36.708 Finished recording : channel 4294967295
2008-03-21 13:00:36.728 MythSocket(84171f8:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:00:39.527 AFD: Opened codec 0x82a3cd0, id(MPEG2VIDEO) type(Video)
2008-03-21 13:00:39.531 AFD: codec MP2 has 2 channels
2008-03-21 13:00:39.532 AFD: Opened codec 0x82a4140, id(MP2) type(Audio)
2008-03-21 13:00:39.728 Preview: Grabbed preview '/var/lib/mythtv/recordings/1501_20080321125940.mpg' 720x480@64s
Communication failed after 5 tries
501
2008-03-21 13:02:48.453 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 13:02:48.831 Expiring 39 MBytes for 1501 @ Fri Mar 21 12:30:00 2008 => The Fabulous Dorseys
2008-03-21 13:02:48.869 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 13:00:34 2008 => 
2008-03-21 13:06:36.186 MainServer::HandleAnnounce Playback
2008-03-21 13:06:36.237 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:06:36.243 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 13:06:36.261 TVRec(1): HW Tuner: 1->1
501
2008-03-21 13:06:37.672 ret_pid(0) child(11437) status(0x0)
2008-03-21 13:06:38.724 ret_pid(11437) child(11437) status(0x0)
2008-03-21 13:06:38.725 External Tuning program exited with no error
2008-03-21 13:06:40.103 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 13:06:40.112 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:06:45.028 TVRec(1): HW Tuner: 1->1
2008-03-21 13:06:46.350 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:47.356 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:48.364 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:49.372 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:50.380 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:51.388 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:52.396 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:53.404 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:54.408 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:55.415 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:56.428 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:57.432 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:58.436 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:06:59.440 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:00.444 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:01.448 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:02.452 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:03.456 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:04.460 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:05.464 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:06.468 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:07.472 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:08.476 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:09.484 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:10.488 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:11.492 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:12.496 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:13.504 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:14.508 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:15.564 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:16.568 ret_pid(0) child(11446) status(0x0)
2008-03-21 13:07:16.570 External Tuning program timed out, killing
2008-03-21 13:07:16.572 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:07:16.584 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 13:07:16.595 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:07:16 2008) endts(Fri Mar 21 13:07:16 2008)
             recstartts(Fri Mar 21 13:07:16 2008) recendts(Fri Mar 21 13:07:16 2008)
             title()
2008-03-21 13:07:17.702 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 13:07:17.833 TVRec(1): RingBufferChanged()
2008-03-21 13:07:17.848 Finished recording The Fabulous Dorseys: channel 1501
2008-03-21 13:07:17.876 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:07:18.005 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:07:18.808 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 13:07:18.844 Empty LocalHostName.
2008-03-21 13:07:18.898 Using localhost value of cross157-desktop
2008-03-21 13:07:18.959 New DB connection, total: 1
2008-03-21 13:07:18.991 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:07:19.012 Closing DB connection named 'DBManager0'
2008-03-21 13:07:19.078 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:07:19.123 New DB connection, total: 2
2008-03-21 13:07:19.127 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:07:19.136 Current Schema Version: 1214
2008-03-21 13:07:23.425 AFD: Opened codec 0x82a3cb0, id(MPEG2VIDEO) type(Video)
2008-03-21 13:07:23.573 AFD: codec MP2 has 2 channels
2008-03-21 13:07:23.725 AFD: Opened codec 0x82a4120, id(MP2) type(Audio)
2008-03-21 13:07:24.396 Preview: Grabbed preview '/var/lib/mythtv/recordings/1501_20080321130638.mpg' 720x480@64s
Communication failed after 5 tries
501
2008-03-21 13:19:59.500 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 13:19:59.534 Empty LocalHostName.
2008-03-21 13:19:59.535 Using localhost value of cross157-desktop
2008-03-21 13:19:59.682 New DB connection, total: 1
2008-03-21 13:19:59.702 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:19:59.706 Closing DB connection named 'DBManager0'
2008-03-21 13:19:59.709 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:19:59.714 New DB connection, total: 2
2008-03-21 13:19:59.732 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:19:59.741 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 13:19:59.769 New DB connection, total: 3
2008-03-21 13:19:59.772 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:20:01.762 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:02.793 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:03.798 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:04.801 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:05.809 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:06.817 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:07.821 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:08.833 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:09.838 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:10.847 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:11.850 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:12.853 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:13.858 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:14.861 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:15.865 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:16.870 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:17.873 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:18.877 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:19.881 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:20.885 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:21.889 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:22.894 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:23.897 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:24.901 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:25.906 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:26.909 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:27.913 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:28.918 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:29.921 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:30.925 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:31.930 ret_pid(0) child(11573) status(0x0)
2008-03-21 13:20:31.932 External Tuning program timed out, killing
2008-03-21 13:20:31.976 New DB scheduler connection
2008-03-21 13:20:31.979 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:20:32.186 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 13:20:32.204 Main::Registering HttpStatus Extension
2008-03-21 13:20:32.226 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 13:20:32.227 Enabled verbose msgs:  important general
2008-03-21 13:20:32.232 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 13:20:35.366 Reschedule requested for id -1.
2008-03-21 13:20:38.966 Scheduled 395 items in 3.6 = 0.27 match + 3.32 place
2008-03-21 13:20:39.109 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
2008-03-21 13:20:44.893 MainServer::HandleAnnounce Monitor
2008-03-21 13:20:44.894 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:20:44.897 MainServer::HandleAnnounce Monitor
2008-03-21 13:20:44.898 adding: cross157-desktop as a client (events: 1)
2008-03-21 13:20:44.919 MainServer::HandleAnnounce Playback
2008-03-21 13:20:44.920 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:20:44.925 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 13:20:44.938 TVRec(1): HW Tuner: 1->1
2008-03-21 13:20:46.337 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:47.342 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:48.346 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:49.350 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:50.354 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:51.358 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:52.121 Expiring 7 MBytes for 1501 @ Fri Mar 21 12:30:00 2008 => The Fabulous Dorseys
2008-03-21 13:20:52.362 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:53.370 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:54.374 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:55.378 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:56.382 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:57.386 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:58.390 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:20:59.394 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:00.398 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:01.402 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:02.406 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:03.410 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:04.414 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:05.418 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:06.422 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:07.426 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:08.430 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:09.438 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:10.442 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:11.446 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:12.450 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:13.454 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:14.458 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:15.462 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:16.466 ret_pid(0) child(11630) status(0x0)
2008-03-21 13:21:16.468 External Tuning program timed out, killing
2008-03-21 13:21:16.470 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:21:16.559 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:21:16 2008) endts(Fri Mar 21 13:21:16 2008)
             recstartts(Fri Mar 21 13:21:16 2008) recendts(Fri Mar 21 13:21:16 2008)
             title()
Communication failed after 5 tries
501
2008-03-21 13:21:17.760 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 13:21:17.772 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:21:18.254 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:21:19.117 Finished recording : channel 4294967295
2008-03-21 13:21:19.130 MythSocket(831c548:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:21:19.142 MythSocket(8373720:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:21:19.151 Unknown socket closing
2008-03-21 13:21:19.153 MainServer::HandleAnnounce Monitor
2008-03-21 13:21:19.156 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:21:19.157 MythSocket(8337be8:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:21:22.631 MainServer::HandleAnnounce Playback
2008-03-21 13:21:22.634 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:21:22.639 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 13:21:22.652 TVRec(1): HW Tuner: 1->1
2008-03-21 13:21:24.126 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:25.130 ret_pid(0) child(11638) status(0x0)

2008-03-21 13:21:26.134 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:27.138 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:28.142 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:29.146 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:30.150 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:31.158 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:32.166 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:33.170 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:34.174 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:35.178 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:36.182 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:37.186 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:38.190 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:39.196 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:40.198 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:41.202 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:42.206 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:43.210 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:44.214 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:45.218 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:46.222 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:47.226 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:47.957 MainServer::HandleAnnounce Monitor
2008-03-21 13:21:47.995 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:21:48.230 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:49.238 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:50.242 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:51.246 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:52.250 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:53.258 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:54.262 ret_pid(0) child(11638) status(0x0)
2008-03-21 13:21:54.264 External Tuning program timed out, killing
2008-03-21 13:21:54.266 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:21:54.359 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:21:54 2008) endts(Fri Mar 21 13:21:54 2008)
             recstartts(Fri Mar 21 13:21:54 2008) recendts(Fri Mar 21 13:21:54 2008)
             title()
2008-03-21 13:21:55.528 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 13:21:55.675 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:21:55.679 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 13:21:55.680 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 13:21:56.521 Finished recording : channel 4294967295
2008-03-21 13:21:56.538 MythSocket(8365870:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:21:56.539 MythSocket(834dd30:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:21:56.550 MainServer::HandleAnnounce Monitor
2008-03-21 13:21:56.561 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:21:59.768 MainServer::HandleAnnounce Playback
2008-03-21 13:21:59.771 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:21:59.777 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 13:21:59.790 TVRec(1): HW Tuner: 1->1
2008-03-21 13:22:01.182 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:02.186 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:03.190 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:04.194 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:05.198 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:06.202 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:07.206 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:08.210 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:09.218 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:10.222 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:11.226 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:12.230 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:13.234 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:14.239 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:15.242 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:15.722 MainServer::HandleAnnounce Monitor
2008-03-21 13:22:15.728 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:22:16.246 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:17.254 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:18.259 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:19.263 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:20.267 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:21.271 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:22.275 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:23.279 ret_pid(0) child(11648) status(0x0)
channel: /dev/ttyS0: Resource temporarily unavailable
2008-03-21 13:22:24.283 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:25.291 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:26.299 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:27.303 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:28.307 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:29.311 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:30.315 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:31.319 ret_pid(0) child(11648) status(0x0)
2008-03-21 13:22:31.320 External Tuning program timed out, killing
2008-03-21 13:22:31.323 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:22:31.406 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:22:31 2008) endts(Fri Mar 21 13:22:31 2008)
             recstartts(Fri Mar 21 13:22:31 2008) recendts(Fri Mar 21 13:22:31 2008)
             title()
2008-03-21 13:22:32.538 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 13:22:32.547 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:22:32.715 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:22:33.584 Finished recording : channel 4294967295
2008-03-21 13:22:33.600 MythSocket(82939c0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:22:33.607 MythSocket(83502e8:-1): writeStringList: Error, socket went unconnected.
Communication failed after 5 tries
501
2008-03-21 13:22:55.812 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 13:21:16 2008 => 
2008-03-21 13:22:56.390 MainServer::HandleAnnounce Monitor
2008-03-21 13:22:56.419 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:23:23.872 Reschedule requested for id 0.
2008-03-21 13:23:25.894 Scheduled 395 items in 2.0 = 0.02 match + 2.00 place
2008-03-21 13:23:28.351 Reschedule requested for id 0.
2008-03-21 13:23:30.655 Scheduled 395 items in 2.3 = 0.01 match + 2.29 place
2008-03-21 13:23:30.894 MainServer::HandleAnnounce Playback
2008-03-21 13:23:30.896 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:23:30.898 MainServer::HandleAnnounce FileTransfer
2008-03-21 13:23:30.900 adding: cross157-desktop as a remote file transfer
2008-03-21 13:23:30.909 New DB connection, total: 4
2008-03-21 13:23:30.911 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:23:35.870 Reschedule requested for id 0.
2008-03-21 13:23:39.317 Scheduled 395 items in 3.4 = 0.01 match + 3.43 place
2008-03-21 13:23:40.865 MainServer::HandleAnnounce Playback
2008-03-21 13:23:40.869 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:23:40.871 MainServer::HandleAnnounce FileTransfer
2008-03-21 13:23:40.872 adding: cross157-desktop as a remote file transfer
2008-03-21 13:23:46.771 Reschedule requested for id 0.
2008-03-21 13:23:47.282 MainServer::HandleAnnounce Playback
2008-03-21 13:23:47.296 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:23:47.306 MainServer::HandleAnnounce FileTransfer
2008-03-21 13:23:47.320 adding: cross157-desktop as a remote file transfer
2008-03-21 13:23:47.335 New DB connection, total: 5
2008-03-21 13:23:47.911 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 13:23:49.173 Scheduled 395 items in 2.4 = 0.05 match + 2.35 place
2008-03-21 13:23:51.052 Reschedule requested for id 0.
Communication failed after 5 tries
501
2008-03-21 13:23:53.916 Scheduled 395 items in 2.9 = 0.01 match + 2.84 place
2008-03-21 13:24:00.762 MainServer::HandleAnnounce Playback
2008-03-21 13:24:00.765 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:24:00.770 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 13:24:00.782 TVRec(1): HW Tuner: 1->1
2008-03-21 13:24:02.188 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:03.192 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:04.196 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:05.200 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:06.204 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:07.216 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:08.236 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:09.244 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:10.248 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:11.260 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:12.272 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:13.276 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:14.285 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:15.300 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:16.308 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:17.324 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:18.328 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:19.332 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:20.336 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:21.340 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:22.352 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:23.360 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:24.372 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:25.376 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:26.380 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:27.384 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:28.388 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:29.396 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:30.412 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:31.424 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:32.428 ret_pid(0) child(11709) status(0x0)
2008-03-21 13:24:32.430 External Tuning program timed out, killing
2008-03-21 13:24:32.432 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:24:32.527 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:24:32 2008) endts(Fri Mar 21 13:24:32 2008)
             recstartts(Fri Mar 21 13:24:32 2008) recendts(Fri Mar 21 13:24:32 2008)
             title()
2008-03-21 13:24:33.743 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:24:33.751 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 13:24:33.899 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:24:34.742 Finished recording : channel 4294967295
2008-03-21 13:24:34.781 MythSocket(8330518:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:24:55.870 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 13:21:54 2008 => 
2008-03-21 13:24:55.874 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 13:22:31 2008 => 
Communication failed after 5 tries
501
2008-03-21 13:26:55.911 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 13:24:32 2008 => 
2008-03-21 13:26:58.989 MainServer::HandleAnnounce Playback
2008-03-21 13:26:58.993 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:26:58.999 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 13:26:59.015 TVRec(1): HW Tuner: 1->1
2008-03-21 13:27:00.414 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:01.418 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:02.422 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:03.426 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:04.430 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:05.434 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:06.438 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:07.442 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:08.446 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:09.454 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:10.474 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:11.478 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:12.482 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:13.486 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:14.490 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:15.494 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:16.165 MainServer::HandleAnnounce Monitor
2008-03-21 13:27:16.167 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:27:16.498 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:17.506 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:18.510 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:19.514 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:20.518 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:21.522 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:22.526 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:23.530 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:24.570 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:25.577 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:26.590 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:27.602 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:27.703 MainServer::HandleAnnounce Monitor
2008-03-21 13:27:27.707 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:27:28.606 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:29.618 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:30.622 ret_pid(0) child(11726) status(0x0)
2008-03-21 13:27:30.626 External Tuning program timed out, killing
2008-03-21 13:27:30.638 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 13:27:30.784 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 13:27:30 2008) endts(Fri Mar 21 13:27:30 2008)
             recstartts(Fri Mar 21 13:27:30 2008) recendts(Fri Mar 21 13:27:30 2008)
             title()
2008-03-21 13:27:31.904 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 13:27:32.529 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 13:27:32.729 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 13:27:33.579 Finished recording : channel 4294967295
2008-03-21 13:27:33.595 MythSocket(85405c0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:27:33.595 MythSocket(8365870:-1): writeStringList: Error, socket went unconnected.
2008-03-21 13:27:39.024 MainServer::HandleAnnounce Playback
2008-03-21 13:27:39.027 adding: cross157-desktop as a client (events: 0)
2008-03-21 13:27:39.029 MainServer::HandleAnnounce FileTransfer
2008-03-21 13:27:39.030 adding: cross157-desktop as a remote file transfer
Communication failed after 5 tries
501
2008-03-21 13:30:56.071 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 13:27:30 2008 => 
2008-03-21 13:36:56.271 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 13:51:56.857 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:06:57.380 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:17:17.055 MainServer::HandleAnnounce Playback
2008-03-21 14:17:17.057 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:17:17.061 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 14:17:17.076 TVRec(1): HW Tuner: 1->1
2008-03-21 14:17:18.487 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:19.491 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:20.495 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:21.499 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:22.503 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:23.507 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:24.511 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:25.515 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:26.519 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:27.523 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:28.531 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:29.536 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:30.539 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:31.543 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:32.548 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:33.176 MainServer::HandleAnnounce Monitor
2008-03-21 14:17:33.181 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:17:33.551 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:34.560 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:35.564 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:36.568 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:37.572 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:38.576 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:39.580 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:40.584 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:41.588 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:42.592 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:43.598 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:44.612 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:45.616 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:46.624 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:47.672 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:48.676 ret_pid(0) child(11846) status(0x0)
2008-03-21 14:17:48.678 External Tuning program timed out, killing
2008-03-21 14:17:48.680 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 14:17:48.785 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 14:17:48 2008) endts(Fri Mar 21 14:17:48 2008)
             recstartts(Fri Mar 21 14:17:48 2008) recendts(Fri Mar 21 14:17:48 2008)
             title()
2008-03-21 14:17:50.059 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 14:17:50.067 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 14:17:50.244 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 14:17:51.118 Finished recording : channel 4294967295
2008-03-21 14:17:51.165 MythSocket(85405c0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 14:17:51.165 MythSocket(8528a38:-1): writeStringList: Error, socket went unconnected.
Communication failed after 5 tries
501
2008-03-21 14:19:24.607 MainServer::HandleAnnounce Monitor
2008-03-21 14:19:24.622 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:20:57.907 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 14:17:48 2008 => 
2008-03-21 14:21:57.989 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:24:23.411 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 14:24:26.465 Empty LocalHostName.
2008-03-21 14:24:26.874 Using localhost value of cross157-desktop
2008-03-21 14:24:31.270 New DB connection, total: 1
2008-03-21 14:24:31.341 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:24:31.344 Closing DB connection named 'DBManager0'
2008-03-21 14:24:31.347 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:24:31.354 New DB connection, total: 2
2008-03-21 14:24:31.356 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:24:31.365 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 14:24:31.397 New DB connection, total: 3
2008-03-21 14:24:31.400 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:24:32.789 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:33.792 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:34.796 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:35.832 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:36.836 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:37.841 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:38.984 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:39.988 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:40.993 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:41.996 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:43.001 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:44.007 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:45.009 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:46.012 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:47.016 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:48.021 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:49.024 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:50.034 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:51.036 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:52.061 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:53.065 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:54.068 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:55.100 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:56.105 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:57.109 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:24:59.281 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:25:00.290 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:25:01.293 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:25:02.297 ret_pid(0) child(11906) status(0x0)
2008-03-21 14:25:02.298 External Tuning program timed out, killing
2008-03-21 14:25:02.374 New DB scheduler connection
2008-03-21 14:25:02.377 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:25:02.446 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 14:25:02.450 Main::Registering HttpStatus Extension
2008-03-21 14:25:02.451 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 14:25:02.452 Enabled verbose msgs:  important general
2008-03-21 14:25:02.462 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:25:05.477 Reschedule requested for id -1.
2008-03-21 14:25:07.745 Scheduled 395 items in 2.3 = 0.05 match + 2.21 place
2008-03-21 14:25:07.761 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
Communication failed after 5 tries
501
2008-03-21 14:26:22.428 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:26:55.621 MainServer::HandleAnnounce Monitor
2008-03-21 14:26:55.623 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:26:55.626 MainServer::HandleAnnounce Monitor
2008-03-21 14:26:55.632 adding: cross157-desktop as a client (events: 1)
2008-03-21 14:26:55.652 MainServer::HandleAnnounce Playback
2008-03-21 14:26:55.655 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:26:55.660 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 14:26:55.672 TVRec(1): HW Tuner: 1->1
2008-03-21 14:26:57.074 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:26:58.078 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:26:59.082 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:00.086 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:01.098 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:02.102 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:03.106 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:04.110 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:05.114 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:06.118 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:07.122 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:08.126 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:09.130 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:10.134 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:11.146 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:12.154 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:12.169 MainServer::HandleAnnounce Monitor
2008-03-21 14:27:12.171 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:27:13.158 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:14.166 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:15.170 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:16.174 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:17.178 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:18.182 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:19.189 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:20.198 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:21.181 MainServer::HandleAnnounce Monitor
2008-03-21 14:27:21.183 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:27:21.207 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:22.218 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:23.222 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:24.226 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:25.230 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:26.234 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:27.238 ret_pid(0) child(11967) status(0x0)
2008-03-21 14:27:27.239 External Tuning program timed out, killing
2008-03-21 14:27:27.242 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 14:27:27.343 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 14:27:27 2008) endts(Fri Mar 21 14:27:27 2008)
             recstartts(Fri Mar 21 14:27:27 2008) recendts(Fri Mar 21 14:27:27 2008)
             title()
2008-03-21 14:27:28.517 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 14:27:28.526 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 14:27:28.668 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 14:27:29.556 Finished recording : channel 4294967295
2008-03-21 14:27:29.580 MythSocket(83a7ad0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 14:27:29.581 MythSocket(83bab60:-1): writeStringList: Error, socket went unconnected.
2008-03-21 14:27:32.925 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 14:27:32.955 Empty LocalHostName.
2008-03-21 14:27:32.956 Using localhost value of cross157-desktop
2008-03-21 14:27:33.018 New DB connection, total: 1
2008-03-21 14:27:33.030 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:27:33.069 Closing DB connection named 'DBManager0'
2008-03-21 14:27:33.072 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:27:33.077 New DB connection, total: 2
2008-03-21 14:27:33.079 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:27:33.088 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 14:27:33.124 New DB connection, total: 3
2008-03-21 14:27:33.128 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:27:34.522 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:35.526 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:36.531 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:37.535 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:38.539 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:39.543 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:40.991 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:43.434 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:44.439 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:45.442 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:46.447 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:47.451 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:48.455 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:49.458 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:50.463 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:51.466 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:52.470 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:53.476 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:54.478 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:55.482 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:56.488 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:57.490 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:58.495 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:27:59.499 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:28:00.503 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:28:01.507 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:28:02.512 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:28:03.515 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:28:04.520 ret_pid(0) child(11998) status(0x0)
2008-03-21 14:28:04.521 External Tuning program timed out, killing
2008-03-21 14:28:04.561 New DB scheduler connection
2008-03-21 14:28:04.564 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:28:04.607 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 14:28:04.609 Main::Registering HttpStatus Extension
2008-03-21 14:28:04.610 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 14:28:04.611 Enabled verbose msgs:  important general
2008-03-21 14:28:04.617 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:28:07.637 Reschedule requested for id -1.
2008-03-21 14:28:10.227 Scheduled 395 items in 2.6 = 0.07 match + 2.52 place
2008-03-21 14:28:10.250 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
Communication failed after 5 tries
501
Communication failed after 5 tries
501
2008-03-21 14:29:43.241 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 14:29:44.024 Empty LocalHostName.
2008-03-21 14:29:44.025 Using localhost value of cross157-desktop
2008-03-21 14:29:44.072 New DB connection, total: 1
2008-03-21 14:29:44.086 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:29:44.090 Closing DB connection named 'DBManager0'
2008-03-21 14:29:44.095 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:29:44.099 New DB connection, total: 2
2008-03-21 14:29:44.101 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:29:44.127 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 14:29:44.163 New DB connection, total: 3
2008-03-21 14:29:44.165 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:29:45.987 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:46.996 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:48.004 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:49.008 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:50.012 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:51.016 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:52.057 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:53.092 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:54.100 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:55.104 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:56.108 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:57.122 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:58.129 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:29:59.132 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:00.136 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:01.141 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:02.144 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:03.148 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:04.152 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:05.156 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:06.160 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:07.164 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:08.168 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:09.172 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:10.220 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:11.232 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:12.237 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:13.241 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:14.249 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:15.257 ret_pid(0) child(12068) status(0x0)
2008-03-21 14:30:15.260 External Tuning program timed out, killing
2008-03-21 14:30:15.803 New DB scheduler connection
2008-03-21 14:30:15.806 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:30:15.960 MediaServer:: Loopback address specified - 127.0.1.1. Disabling UPnP
2008-03-21 14:30:15.961 Main::Registering HttpStatus Extension
2008-03-21 14:30:15.962 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 14:30:15.963 Enabled verbose msgs:  important general
2008-03-21 14:30:15.969 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:30:19.144 Reschedule requested for id -1.
2008-03-21 14:30:25.861 Scheduled 395 items in 6.7 = 2.03 match + 4.69 place
2008-03-21 14:30:26.131 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
2008-03-21 14:30:35.820 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 14:27:27 2008 => 
Communication failed after 5 tries
501
2008-03-21 14:31:35.860 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:38:49.228 MainServer::HandleAnnounce Monitor
2008-03-21 14:38:49.237 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:38:49.240 MainServer::HandleAnnounce Monitor
2008-03-21 14:38:49.242 adding: cross157-desktop as a client (events: 1)
2008-03-21 14:38:49.281 Reschedule requested for id -1.
2008-03-21 14:38:49.282 MythSocket(82c0cc0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 14:38:51.534 Scheduled 395 items in 2.2 = 0.05 match + 2.20 place
2008-03-21 14:40:35.435 MainServer::HandleAnnounce Monitor
2008-03-21 14:40:35.440 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:40:35.442 MainServer::HandleAnnounce Monitor
2008-03-21 14:40:35.444 adding: cross157-desktop as a client (events: 1)
2008-03-21 14:40:35.467 MainServer::HandleAnnounce Playback
2008-03-21 14:40:35.473 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:40:35.477 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 14:40:35.490 TVRec(1): HW Tuner: 1->1
2008-03-21 14:40:36.907 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:37.911 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:38.915 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:39.919 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:40.923 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:41.927 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:42.931 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:43.935 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:44.939 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:45.943 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:46.947 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:47.951 ret_pid(0) child(12206) status(0x0)
2008-03-21 14:40:52.160 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 14:40:52.171 Empty LocalHostName.
2008-03-21 14:40:52.172 Using localhost value of cross157-desktop
2008-03-21 14:40:52.214 New DB connection, total: 1
2008-03-21 14:40:52.225 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:40:52.229 Closing DB connection named 'DBManager0'
2008-03-21 14:40:52.232 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:40:52.237 New DB connection, total: 2
2008-03-21 14:40:52.239 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:40:52.247 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 14:40:52.277 New DB connection, total: 3
2008-03-21 14:40:52.280 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:40:53.680 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:40:54.683 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:40:55.688 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:40:56.695 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:40:57.704 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:40:58.712 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:40:59.716 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:00.719 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:01.723 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:02.728 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:03.731 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:04.736 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:05.739 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:06.744 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:07.748 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:08.751 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:09.756 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:10.759 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:11.768 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:12.771 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:13.776 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:14.779 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:15.784 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:16.787 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:17.792 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:18.796 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:19.799 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:20.804 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:21.807 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:22.812 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:23.817 ret_pid(0) child(12233) status(0x0)
2008-03-21 14:41:23.819 External Tuning program timed out, killing
2008-03-21 14:41:23.863 New DB scheduler connection
2008-03-21 14:41:23.866 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:41:23.966 MediaServer:: Loopback address specified - 127.0.1.1. Disabling UPnP
2008-03-21 14:41:23.977 Main::Registering HttpStatus Extension
2008-03-21 14:41:23.978 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 14:41:23.979 Enabled verbose msgs:  important general
2008-03-21 14:41:23.985 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:41:27.080 Reschedule requested for id -1.
2008-03-21 14:41:32.582 Scheduled 395 items in 5.5 = 0.26 match + 5.24 place
2008-03-21 14:41:33.068 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
Communication failed after 5 tries
501
2008-03-21 14:42:43.887 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
Communication failed after 5 tries
501
2008-03-21 14:52:24.727 MainServer::HandleAnnounce Monitor
2008-03-21 14:52:24.733 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:52:24.735 MainServer::HandleAnnounce Monitor
2008-03-21 14:52:24.740 adding: cross157-desktop as a client (events: 1)
2008-03-21 14:52:24.760 MainServer::HandleAnnounce Playback
2008-03-21 14:52:24.761 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:52:24.768 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 14:52:24.783 TVRec(1): HW Tuner: 1->1
2008-03-21 14:52:26.187 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:27.193 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:28.195 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:29.199 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:30.203 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:31.207 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:32.211 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:33.215 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:34.219 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:35.223 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:36.228 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:37.232 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:38.235 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:39.239 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:40.243 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:41.257 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:42.259 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:43.263 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:44.268 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:45.271 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:45.538 MainServer::HandleAnnounce Monitor
2008-03-21 14:52:45.540 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:52:46.275 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:47.283 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:48.287 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:49.292 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:50.295 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:51.299 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:52.303 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:53.307 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:54.313 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:54.787 MainServer::HandleAnnounce Monitor
2008-03-21 14:52:54.792 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:52:55.316 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:56.323 ret_pid(0) child(12307) status(0x0)
2008-03-21 14:52:56.324 External Tuning program timed out, killing
2008-03-21 14:52:56.329 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 14:52:56.428 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 14:52:56 2008) endts(Fri Mar 21 14:52:56 2008)
             recstartts(Fri Mar 21 14:52:56 2008) recendts(Fri Mar 21 14:52:56 2008)
             title()
2008-03-21 14:52:57.639 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 14:52:57.654 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 14:52:57.803 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 14:52:58.626 Finished recording : channel 4294967295
2008-03-21 14:52:58.639 MythSocket(83a7a88:-1): writeStringList: Error, socket went unconnected.
2008-03-21 14:52:58.642 MythSocket(83bab10:-1): writeStringList: Error, socket went unconnected.
Communication failed after 5 tries
501
2008-03-21 14:55:42.948 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 14:55:43.207 Empty LocalHostName.
2008-03-21 14:55:43.249 Using localhost value of cross157-desktop
2008-03-21 14:55:43.445 New DB connection, total: 1
2008-03-21 14:55:43.518 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:55:43.537 Closing DB connection named 'DBManager0'
2008-03-21 14:55:43.541 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:55:43.602 New DB connection, total: 2
2008-03-21 14:55:43.607 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:55:43.638 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 14:55:43.900 New DB connection, total: 3
2008-03-21 14:55:43.920 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:55:45.441 ret_pid(0) child(5526) status(0x0)
2008-03-21 14:55:46.586 ret_pid(0) child(5526) status(0x0)
2008-03-21 14:55:48.160 ret_pid(0) child(5526) status(0x0)
2008-03-21 14:56:19.737 ret_pid(0) child(5526) status(0x0)
2008-03-21 14:56:19.841 External Tuning program timed out, killing
2008-03-21 14:56:20.022 New DB scheduler connection
2008-03-21 14:56:20.086 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 14:56:20.375 MediaServer:: Loopback address specified - 127.0.1.1. Disabling UPnP
2008-03-21 14:56:20.421 Main::Registering HttpStatus Extension
2008-03-21 14:56:20.585 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 14:56:20.619 Enabled verbose msgs:  important general
2008-03-21 14:56:20.809 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:56:23.345 Reschedule requested for id -1.
2008-03-21 14:56:33.610 Scheduled 395 items in 10.3 = 5.91 match + 4.35 place
2008-03-21 14:56:33.625 AUTO-Startup assumed
/dev/video0: 61.250 MHz  (Signal Detected)
2008-03-21 14:56:40.144 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 14:52:56 2008 => 
Communication failed after 5 tries
501
2008-03-21 14:57:40.157 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 14:59:00.459 Reschedule requested for id 0.
2008-03-21 14:59:02.837 Scheduled 395 items in 2.4 = 0.49 match + 1.88 place
2008-03-21 14:59:03.387 MainServer::HandleAnnounce Monitor
2008-03-21 14:59:03.400 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:59:03.402 MainServer::HandleAnnounce Monitor
2008-03-21 14:59:03.403 adding: cross157-desktop as a client (events: 1)
2008-03-21 14:59:03.454 MainServer::HandleAnnounce Playback
2008-03-21 14:59:03.483 adding: cross157-desktop as a client (events: 0)
2008-03-21 14:59:03.528 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 14:59:03.542 TVRec(1): HW Tuner: 1->1
2008-03-21 14:59:04.939 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:05.943 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:06.947 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:07.951 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:08.955 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:09.959 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:10.963 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:11.967 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:12.971 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:13.975 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:14.979 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:15.991 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:16.995 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:17.999 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:19.003 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:20.007 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:21.011 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:22.015 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:23.019 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:24.023 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:25.027 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:26.031 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:27.037 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:28.039 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:29.043 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:30.047 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:31.052 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:32.056 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:33.060 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:34.064 ret_pid(0) child(6287) status(0x0)
2008-03-21 14:59:34.065 External Tuning program timed out, killing
2008-03-21 14:59:34.068 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 14:59:34.293 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 14:59:34 2008) endts(Fri Mar 21 14:59:34 2008)
             recstartts(Fri Mar 21 14:59:34 2008) recendts(Fri Mar 21 14:59:34 2008)
             title()
2008-03-21 14:59:35.623 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 14:59:35.631 AutoExpire: CalcParams(): Max required Free Space: 26.0 GB w/freq: 15 min
2008-03-21 14:59:35.759 TVRec(1): ASK_RECORDING 1 29 0 0
2008-03-21 14:59:35.761 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 14:59:36.596 Finished recording : channel 4294967295
2008-03-21 14:59:36.613 MythSocket(84efb20:-1): writeStringList: Error, socket went unconnected.
2008-03-21 15:00:02.362 TVRec(1): Changing from None to RecordingOnly
2008-03-21 15:00:02.373 TVRec(1): HW Tuner: 1->1
2008-03-21 15:00:03.769 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:04.773 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:05.777 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:06.781 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:07.785 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:08.789 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:09.793 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:10.797 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:11.801 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:12.805 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:13.809 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:14.813 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:15.817 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:16.821 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:17.825 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:18.829 ret_pid(0) child(6293) status(0x0)
Communication failed after 5 tries
501
2008-03-21 15:00:19.833 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:20.841 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:21.845 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:22.849 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:23.853 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:24.857 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:25.861 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:26.866 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:27.870 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:28.874 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:29.878 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:30.882 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:31.886 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:32.890 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:33.894 ret_pid(0) child(6293) status(0x0)
2008-03-21 15:00:33.895 External Tuning program timed out, killing
2008-03-21 15:00:33.898 TVRec(1) Error: Failed to set channel to 63. Reverting to kState_None
2008-03-21 15:00:33.899 TVRec(1): Changing from RecordingOnly to None
2008-03-21 15:00:33.936 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:00:33.947 Canceled recording (Recorder Failed): Scrubs "Her Story II": channel 1063 on cardid 1, sourceid 1
2008-03-21 15:00:34.951 Reschedule requested for id 0.
2008-03-21 15:00:36.693 Scheduled 395 items in 1.7 = 0.00 match + 1.73 place
2008-03-21 15:00:37.000 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/cross157-desktop/1063_20080321150000.mpg' could not open 
			eno: No such file or directory (2)
2008-03-21 15:00:37.003 Delete Error '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/cross157-desktop/1063_20080321150000.mpg'
			eno: No such file or directory (2)
2008-03-21 15:00:41.018 Reschedule requested for id 0.
2008-03-21 15:00:42.760 Scheduled 395 items in 1.7 = 0.00 match + 1.73 place
63
2008-03-21 15:02:40.317 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 14:59:34 2008 => 
2008-03-21 15:06:19.932 MainServer::HandleAnnounce Playback
2008-03-21 15:06:19.937 adding: cross157-desktop as a client (events: 0)
2008-03-21 15:06:19.941 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 15:06:19.953 TVRec(1): HW Tuner: 1->1
2008-03-21 15:06:21.346 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:22.350 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:23.354 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:24.358 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:25.363 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:26.367 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:27.371 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:28.375 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:29.379 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:30.383 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:31.387 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:32.391 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:33.639 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:34.659 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:35.695 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:36.783 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:37.795 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:38.871 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:39.883 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:40.895 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:42.143 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:43.151 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:44.159 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:45.171 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:46.175 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:47.179 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:48.211 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:49.239 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:50.247 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:51.251 ret_pid(0) child(6315) status(0x0)
2008-03-21 15:06:51.253 External Tuning program timed out, killing
2008-03-21 15:06:51.255 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 15:06:51.363 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 15:06:51 2008) endts(Fri Mar 21 15:06:51 2008)
             recstartts(Fri Mar 21 15:06:51 2008) recendts(Fri Mar 21 15:06:51 2008)
             title()
Communication failed after 5 tries
63
2008-03-21 15:09:34.931 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 15:09:35.293 Empty LocalHostName.
2008-03-21 15:09:35.295 Using localhost value of cross157-desktop
2008-03-21 15:09:35.326 New DB connection, total: 1
2008-03-21 15:09:35.339 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:09:35.342 Closing DB connection named 'DBManager0'
2008-03-21 15:09:35.345 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:09:35.350 New DB connection, total: 2
2008-03-21 15:09:35.352 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:09:35.362 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 15:09:35.393 New DB connection, total: 3
2008-03-21 15:09:35.395 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:09:36.831 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:37.936 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:38.942 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:40.231 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:41.234 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:42.238 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:43.243 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:44.246 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:45.250 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:46.311 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:47.318 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:48.322 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:49.338 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:50.351 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:51.540 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:54.138 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:55.145 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:56.150 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:57.154 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:58.335 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:09:59.340 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:00.402 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:01.406 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:03.195 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:04.238 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:05.243 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:06.247 ret_pid(0) child(6421) status(0x0)
2008-03-21 15:10:06.249 External Tuning program timed out, killing
2008-03-21 15:10:06.367 New DB scheduler connection
2008-03-21 15:10:06.372 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:10:06.594 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 15:10:06.596 Main::Registering HttpStatus Extension
2008-03-21 15:10:06.597 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 15:10:06.598 Enabled verbose msgs:  important general
2008-03-21 15:10:06.604 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:10:09.656 Reschedule requested for id -1.
2008-03-21 15:10:17.499 Scheduled 395 items in 7.8 = 0.27 match + 7.57 place
2008-03-21 15:10:17.827 Seem to be woken up by USER
/dev/video0: 61.250 MHz  (Signal Detected)
Communication failed after 5 tries
63
2008-03-21 15:11:26.396 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:21:36.446 MainServer::HandleAnnounce Monitor
2008-03-21 15:21:36.453 adding: cross157-desktop as a client (events: 0)
2008-03-21 15:21:36.456 MainServer::HandleAnnounce Monitor
2008-03-21 15:21:36.457 adding: cross157-desktop as a client (events: 1)
2008-03-21 15:23:50.959 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 15:23:51.616 Empty LocalHostName.
2008-03-21 15:23:51.617 Using localhost value of cross157-desktop
2008-03-21 15:23:51.645 New DB connection, total: 1
2008-03-21 15:23:51.658 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:23:51.661 Closing DB connection named 'DBManager0'
2008-03-21 15:23:51.664 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:23:51.668 New DB connection, total: 2
2008-03-21 15:23:51.670 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:23:51.678 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 15:23:51.708 New DB connection, total: 3
2008-03-21 15:23:51.712 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:23:53.206 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:23:54.209 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:23:55.213 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:23:56.217 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:23:57.221 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:23:58.231 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:23:59.233 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:00.237 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:01.242 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:02.245 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:03.250 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:04.253 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:05.257 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:06.262 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:07.265 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:08.271 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:09.275 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:10.277 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:11.283 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:12.286 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:13.291 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:14.294 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:15.298 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:16.301 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:17.305 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:18.309 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:19.314 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:20.730 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:21.864 ret_pid(0) child(6639) status(0x0)
2008-03-21 15:24:23.922 External Tuning program timed out, killing
2008-03-21 15:24:24.203 New DB scheduler connection
2008-03-21 15:24:24.324 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:24:25.970 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 15:24:25.971 Main::Registering HttpStatus Extension
2008-03-21 15:24:25.972 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 15:24:25.973 Enabled verbose msgs:  important general
2008-03-21 15:24:25.980 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:24:29.003 Reschedule requested for id -1.
2008-03-21 15:24:30.903 Scheduled 395 items in 1.9 = 0.05 match + 1.85 place
2008-03-21 15:24:30.918 AUTO-Startup assumed
/dev/video0: 61.250 MHz  (Signal Detected)
Communication failed after 5 tries
63
2008-03-21 15:25:46.299 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:28:01.132 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-21 15:28:01.152 Empty LocalHostName.
2008-03-21 15:28:01.153 Using localhost value of cross157-desktop
2008-03-21 15:28:01.184 New DB connection, total: 1
2008-03-21 15:28:01.196 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:28:01.199 Closing DB connection named 'DBManager0'
2008-03-21 15:28:01.202 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:28:01.207 New DB connection, total: 2
2008-03-21 15:28:01.209 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:28:01.215 Current Schema Version: 1214
Starting up as the master server.
2008-03-21 15:28:01.236 New DB connection, total: 3
2008-03-21 15:28:01.239 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:28:02.622 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:03.626 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:04.634 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:05.793 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:06.799 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:07.802 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:08.807 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:09.814 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:10.818 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:11.822 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:12.826 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:13.830 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:14.835 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:15.882 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:16.887 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:17.890 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:18.894 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:19.898 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:20.904 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:21.906 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:22.910 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:23.915 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:24.919 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:25.923 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:26.926 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:27.930 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:28.935 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:29.939 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:30.943 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:31.947 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:32.951 ret_pid(0) child(6816) status(0x0)
2008-03-21 15:28:32.952 External Tuning program timed out, killing
2008-03-21 15:28:32.993 New DB scheduler connection
2008-03-21 15:28:32.996 Connected to database 'mythconverg' at host: 127.0.0.1
2008-03-21 15:28:33.044 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-03-21 15:28:33.045 Main::Registering HttpStatus Extension
2008-03-21 15:28:33.046 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-03-21 15:28:33.046 Enabled verbose msgs:  important general
2008-03-21 15:28:33.053 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:28:36.032 Reschedule requested for id -1.
2008-03-21 15:28:38.002 Scheduled 395 items in 2.0 = 0.05 match + 1.92 place
2008-03-21 15:28:38.016 AUTO-Startup assumed
/dev/video0: 61.250 MHz  (Signal Detected)
Communication failed after 5 tries
63
2008-03-21 15:29:30.425 TVRec(1): ASK_RECORDING 1 28 0 0
2008-03-21 15:29:37.450 MainServer::HandleAnnounce Monitor
2008-03-21 15:29:37.456 adding: cross157-desktop as a client (events: 0)
2008-03-21 15:29:37.458 MainServer::HandleAnnounce Monitor
2008-03-21 15:29:37.462 adding: cross157-desktop as a client (events: 1)
2008-03-21 15:29:37.482 MainServer::HandleAnnounce Playback
2008-03-21 15:29:37.483 adding: cross157-desktop as a client (events: 0)
2008-03-21 15:29:37.488 TVRec(1): Changing from None to WatchingLiveTV
2008-03-21 15:29:37.500 TVRec(1): HW Tuner: 1->1
2008-03-21 15:29:38.901 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:39.906 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:40.909 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:41.913 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:42.917 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:43.933 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:44.938 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:45.941 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:46.949 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:47.953 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:48.957 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:49.962 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:50.970 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:51.974 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:52.877 MainServer::HandleAnnounce Monitor
2008-03-21 15:29:52.882 adding: cross157-desktop as a client (events: 0)
2008-03-21 15:29:52.978 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:53.986 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:54.990 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:55.994 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:56.998 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:58.002 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:29:59.006 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:00.010 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:01.014 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:02.018 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:03.022 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:04.026 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:05.030 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:06.034 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:07.038 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:08.042 ret_pid(0) child(6876) status(0x0)
2008-03-21 15:30:08.043 External Tuning program timed out, killing
2008-03-21 15:30:08.046 TVRec(1) Error: Failed to set channel to 405.
2008-03-21 15:30:08.170 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Fri Mar 21 15:30:08 2008) endts(Fri Mar 21 15:30:08 2008)
             recstartts(Fri Mar 21 15:30:08 2008) recendts(Fri Mar 21 15:30:08 2008)
             title()
2008-03-21 15:30:09.368 MPEGRec(/dev/video0) Warning: Stream type 'DVD-Special 2'
			is not supported by ivtv driver, using 'DVD' instead.
2008-03-21 15:30:09.377 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:30:09.559 TVRec(1): Changing from WatchingLiveTV to None
2008-03-21 15:30:10.392 Finished recording : channel 4294967295
2008-03-21 15:30:10.402 MythSocket(83e0cf0:-1): writeStringList: Error, socket went unconnected.
2008-03-21 15:30:10.403 MythSocket(834de00:-1): writeStringList: Error, socket went unconnected.
2008-03-21 15:30:10.549 TVRec(1): Changing from None to RecordingOnly
2008-03-21 15:30:10.559 TVRec(1): HW Tuner: 1->1
2008-03-21 15:30:11.950 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:12.954 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:13.966 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:14.974 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:15.978 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:16.982 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:17.986 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:18.993 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:19.999 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:21.003 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:22.007 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:23.011 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:24.015 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:25.019 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:26.023 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:27.027 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:28.031 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:29.035 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:30.039 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:31.043 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:32.047 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:33.051 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:34.055 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:35.059 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:36.063 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:37.067 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:38.071 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:39.075 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:40.079 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:41.083 ret_pid(0) child(6882) status(0x0)
2008-03-21 15:30:41.084 External Tuning program timed out, killing
2008-03-21 15:30:41.087 TVRec(1) Error: Failed to set channel to 63. Reverting to kState_None
2008-03-21 15:30:41.089 TVRec(1): Changing from RecordingOnly to None
2008-03-21 15:30:41.109 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:30:41.118 Canceled recording (Recorder Failed): Scrubs "My Buddy's Booty": channel 1063 on cardid 1, sourceid 1
2008-03-21 15:30:41.124 AutoExpire: CalcParams(): Max required Free Space: 25.0 GB w/freq: 15 min
2008-03-21 15:30:42.129 Reschedule requested for id 0.
2008-03-21 15:30:44.100 Scheduled 394 items in 2.0 = 0.00 match + 1.96 place
2008-03-21 15:30:44.198 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/cross157-desktop/1063_20080321153000.mpg' could not open 
			eno: No such file or directory (2)
2008-03-21 15:30:44.200 Delete Error '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/cross157-desktop/1063_20080321153000.mpg'
			eno: No such file or directory (2)
2008-03-21 15:30:48.215 Reschedule requested for id 0.
2008-03-21 15:30:50.110 Scheduled 394 items in 1.9 = 0.00 match + 1.89 place
Communication failed after 5 tries
63
63
2008-03-21 15:32:09.443 Expiring 0 MBytes for 4294967295 @ Fri Mar 21 15:30:08 2008 => 
```

My computer is a Dell Dimension 4400 with a P4, nvidia card, running Mythbuntu Gutsy. Thanks in advance.

---

### Post by volkswagner on 2008-03-21
```
2008-03-21 08:00:04.117 Empty LocalHostName.
```

I was getting this until I set up static ip addresses for LAN connected backends and frontends.

[http://ubuntuforums.org/showthread.php?t=730308]("http://ubuntuforums.org/showthread.php?t=730308")

[http://ubuntuforums.org/showthread.php?t=704201]("http://ubuntuforums.org/showthread.php?t=704201")


Not sure if they are related or not.

---

### Post by cross157 on 2008-03-21
My setup is all in one, backend/frontend/desktop, the only IPs I have set are 127.0.0.1.

I'll check out those threads, thanks.

I just tried live tv again and it worked until I changed the channel. Then back to the same error.

---

### Post by kaicrr77 on 2008-03-22
Ever since the latest MYSQL update I've been having problems with this as well.

---

### Post by kaicrr77 on 2008-03-22
I wish I could give you some step by step process that I took to get this working but I can't. I went through my entire setup and the only thing I did was set the DB backend to a static IP Address and make sure my backend type was set correctly. I also found that the backend wasn't started. After a restart I manually started the service since it didn't come up automatically. Once I did this  myth for the most part was back to normal.

---

### Post by cross157 on 2008-03-23
> I wish I could give you some step by step process that I took to get this working but I can't. I went through my entire setup and the only thing I did was set the DB backend to a static IP Address and make sure my backend type was set correctly. I also found that the backend wasn't started. After a restart I manually started the service since it didn't come up automatically. Once I did this myth for the most part was back to normal.

How do I make sure that's mythtv backend is set to a static IP, I thought it was, but now I'm not sure what you guys are doing exactly.

---

### Post by volkswagner on 2008-03-24
First in a terminal verify your LAN ip Address.

```
ifconfig

```

Write down your ip address and subnet mask.


From Mythbuntu desktop >applications >System >Network

Select your wired network connection, >Properties <de-select allow roaming >enter your ip address, subnet, and gateway address.

Your gateway should be the address you access your router, usually 192.168.1.1

For safe measures I would restart the pc and verify your ip is what you set it to 

```
ifconfig
```

You should also run mythbackend-setup to verify your ip addresses are correct for your static setting.

I have assumed you are using a wired connection.

---

### Post by kaicrr77 on 2008-03-24
Just saw your post will have to make sure I don't have any deleted channels as well.

---

