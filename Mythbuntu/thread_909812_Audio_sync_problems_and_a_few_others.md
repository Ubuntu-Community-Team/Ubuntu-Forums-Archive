---
title: "Audio sync problems and a few others"
date: 2008-09-03
forum: Mythbuntu
---

### Post by rubrboots on 2008-09-03
I have a master mythbox running as a backend/frontend and two remote frontends. Most things are working well now with the exception of the recording playback. Many recorded shows will begin playing in sync, but several minutes later the audio will garble for a second, then the audio will be out of sync for rest of the recording

Also (not sure if this is related), many times the frontend will just go to a black screen and freeze when a recording is selected to play. None of these problems are present when videos are played, so I have to assume that this is a problem with the backend. 

I have checked out the backend and frontend log on the master mythbox, but I am not sure what I am looking for. Here are some portions of the backend log that look suspicious to me.

Any advice would be greatly appreciated

```
008-09-02 19:00:00.366 Finished recording News Hour: channel 1008
2008-09-02 19:00:01.717 Using runtime prefix = /usr
2008-09-02 19:00:01.771 Empty LocalHostName.
2008-09-02 19:00:01.773 Using localhost value of mythbe
2008-09-02 19:00:01.878 New DB connection, total: 1
2008-09-02 19:00:01.897 Connected to database 'mythconverg' at host: localhost
2008-09-02 19:00:01.899 Closing DB connection named 'DBManager0'
2008-09-02 19:00:01.901 Connected to database 'mythconverg' at host: localhost
2008-09-02 19:00:01.904 New DB connection, total: 2
2008-09-02 19:00:01.906 Connected to database 'mythconverg' at host: localhost
2008-09-02 19:00:01.922 Current Schema Version: 1214
2008-09-02 19:00:02.845 TVRec(1): Changing from None to RecordingOnly
2008-09-02 19:00:02.953 TVRec(1): HW Tuner: 1->1
2008-09-02 19:00:04.141 ret_pid(0) child(7840) status(0x0)
2008-09-02 19:00:05.069 AFD: Opened codec 0x829d7e0, id(MPEG2VIDEO) type(Video)
2008-09-02 19:00:05.072 AFD: codec MP2 has 2 channels
2008-09-02 19:00:05.073 AFD: Opened codec 0x829dc60, id(MP2) type(Audio)
2008-09-02 19:00:05.163 ret_pid(7840) child(7840) status(0x0)
2008-09-02 19:00:05.172 External Tuning program exited with no error
[COLOR="Red"]2008-09-02 19:00:05.286 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.[/COLOR]
2008-09-02 19:00:05.416 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-09-02 19:00:05.462 Started recording: The First 48 "In Cold Blood; Red Handed": channel 1025 on cardid 1, sourceid 1
2008-09-02 19:00:06.505 Reschedule requested for id 0.
2008-09-02 19:00:06.890 Preview: Grabbed preview '/var/lib/mythtv/recordings/1008_20080902180000.mpg' 720x480@64s
2008-09-02 19:00:07.189 Scheduled 122 items in 0.7 = 0.04 match + 0.64 place
2008-09-02 19:00:07.360 MainServer::HandleAnnounce Monitor
2008-09-02 19:00:07.390 adding: mythbe as a client (events: 0)
[COLOR="Red"]2008-09-02 19:00:19.720 [mpeg2video @ 0xb73a8a88]ac-tex damaged at 15 8
2008-09-02 19:00:19.730 [mpeg2video @ 0xb73a8a88]Warning MVs not available[/COLOR]
2008-09-02 19:00:20.691 Using runtime prefix = /usr
2008-09-02 19:00:20.699 Empty LocalHostName.
2008-09-02 19:00:20.700 Using localhost value of mythbe
```


it also seems to repeat this command alot

```
2008-09-02 19:00:43.178 UPnpMedia: BuildMediaMap Done. Found 127 objects
2008-09-02 19:10:05.444 MainServer::HandleAnnounce Monitor
2008-09-02 19:10:05.485 adding: mythbe as a client (events: 0)
2008-09-02 19:15:41.504 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-09-02 19:20:04.103 MainServer::HandleAnnounce Monitor
2008-09-02 19:20:04.135 adding: mythbe as a client (events: 0)
2008-09-02 19:23:47.446 MainServer::HandleAnnounce Playback
2008-09-02 19:23:47.557 adding: mythbe as a client (events: 0)
2008-09-02 19:23:47.563 MainServer::HandleAnnounce FileTransfer
2008-09-02 19:23:47.565 adding: mythbe as a remote file transfer
2008-09-02 19:23:50.209 MainServer::HandleAnnounce Playback
2008-09-02 19:23:50.227 adding: mythbe as a client (events: 0)
2008-09-02 19:23:50.229 MainServer::HandleAnnounce FileTransfer
2008-09-02 19:23:50.230 adding: mythbe as a remote file transfer
2008-09-02 19:24:44.553 MainServer::HandleAnnounce Playback
2008-09-02 19:24:44.575 adding: mythbe as a client (events: 0)
2008-09-02 19:24:44.577 MainServer::HandleAnnounce FileTransfer
2008-09-02 19:24:44.578 adding: mythbe as a remote file transfer
2008-09-02 19:24:46.133 MainServer::HandleAnnounce Playback
2008-09-02 19:24:46.142 adding: mythbe as a client (events: 0)
2008-09-02 19:24:46.144 MainServer::HandleAnnounce FileTransfer
2008-09-02 19:24:46.146 adding: mythbe as a remote file transfer
2008-09-02 19:24:48.117 MainServer::HandleAnnounce Playback
2008-09-02 19:24:48.126 adding: mythbe as a client (events: 0)
2008-09-02 19:24:48.128 MainServer::HandleAnnounce FileTransfer
2008-09-02 19:24:48.129 adding: mythbe as a remote file transfer
2008-09-02 19:30:04.837 MainServer::HandleAnnounce Monitor
2008-09-02 19:30:04.868 adding: mythbe as a client (events: 0)
2008-09-02 19:30:41.775 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-09-02 19:30:46.254 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
```

---

