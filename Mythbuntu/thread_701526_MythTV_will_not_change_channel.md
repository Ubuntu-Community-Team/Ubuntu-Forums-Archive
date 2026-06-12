---
title: "MythTV will not change channel"
date: 2008-02-19
forum: Mythbuntu
---

### Post by maybeway36 on 2008-02-19
I am using a Mythbuntu 7.10 combined backend/frontend. MythTV mostly works fine, but when I try to change channels, MythTV acts like it worked but the TV tuner is still tuned to the same channel.
xawtv can change channels just fine. I am using NTSC/us-bcast, and my card is a ATI TV-Wonder/VE.
MythTV has worked with thi card and computer in the past (although then I was using us-cable.)

---

### Post by Trimble Epic on 2008-02-19
Did you inadvertently setup a channel change script?  If you do that, the internal tuner is supposed to stay on one channel, and it sends a channel change command to the IR blaster in hopes of changing channel on the VCR/Dish/DTV box...

---

### Post by maybeway36 on 2008-02-19
I don't think so. I kept the defaults for most options.

---

### Post by maybeway36 on 2008-02-19
Here's a portion of my /var/log/mythtv/mythbackend.log:
```
2008-02-19 11:20:28.144 Using runtime prefix = /usr
2008-02-19 11:20:28.372 New DB connection, total: 1
2008-02-19 11:20:28.414 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:20:28.540 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 11:20:28.775 New DB connection, total: 2
2008-02-19 11:20:28.978 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:20:29.076 EITHelper: localtime offset -6:00:00 
2008-02-19 11:20:29.182 New DB connection, total: 3
2008-02-19 11:20:29.216 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:20:29.315 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:20:29.357 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:20:29.437 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:20:29.515 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:20:29.590 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 11:20:29.717 New DB scheduler connection
2008-02-19 11:20:29.758 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:20:29.942 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-02-19 11:20:30.197 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-02-19 11:20:31.439 Main::Registering HttpStatus Extension
2008-02-19 11:20:31.483 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 11:20:31.513 Enabled verbose msgs:  important general
2008-02-19 11:20:31.534 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-02-19 11:20:31.586 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 11:20:31.659 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 11:20:31.938 Reschedule requested for id -1.
2008-02-19 11:20:32.001 Scheduled 0 items in 0.1 = 0.04 match + 0.02 place
2008-02-19 11:20:32.051 Seem to be woken up by USER
2008-02-19 11:28:10.713 MainServer::HandleAnnounce Monitor
2008-02-19 11:28:10.765 adding: mythical as a client (events: 0)
2008-02-19 11:28:10.799 MainServer::HandleAnnounce Monitor
2008-02-19 11:28:10.828 adding: mythical as a client (events: 1)
2008-02-19 11:28:10.878 MainServer::HandleAnnounce Playback
2008-02-19 11:28:10.937 adding: mythical as a client (events: 0)
2008-02-19 11:28:10.966 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 11:28:11.029 TVRec(1): HW Tuner: 1->1
2008-02-19 11:28:11.083 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:28:11.120 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:28:11.162 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 11:28:11.262 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:28:11 2008) endts(Tue Feb 19 11:28:11 2008)
             recstartts(Tue Feb 19 11:28:11 2008) recendts(Tue Feb 19 11:28:11 2008)
             title()
2008-02-19 11:28:11.480 Unknown video codec
2008-02-19 11:28:11.522 Please go into the TV Settings, Recording Profiles and
2008-02-19 11:28:11.564 setup the four 'Software Encoders' profiles.
2008-02-19 11:28:11.594 Assuming RTjpeg for now.
2008-02-19 11:28:11.622 NVR: Error, unknown audio codec
2008-02-19 11:28:11.689 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 11:28:16.747 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:28:16.787 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:28:16.829 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 11:28:16.863 Finished recording : channel 4294967295
2008-02-19 11:28:16.903 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:28:16 2008) endts(Tue Feb 19 11:28:16 2008)
             recstartts(Tue Feb 19 11:28:16 2008) recendts(Tue Feb 19 11:28:16 2008)
             title()
2008-02-19 11:28:17.018 Finished recording : channel 4294967295
2008-02-19 11:28:17.517 TVRec(1): RingBufferChanged()
2008-02-19 11:28:17.636 Finished recording : channel 4294967295
2008-02-19 11:28:21.387 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:28:21.415 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:28:21.456 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 11:28:21.521 Finished recording : channel 4294967295
2008-02-19 11:28:21.561 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:28:21 2008) endts(Tue Feb 19 11:28:21 2008)
             recstartts(Tue Feb 19 11:28:21 2008) recendts(Tue Feb 19 11:28:21 2008)
             title()
2008-02-19 11:28:21.663 Finished recording : channel 4294967295
2008-02-19 11:28:21.958 TVRec(1): RingBufferChanged()
2008-02-19 11:28:22.038 Finished recording : channel 4294967295
2008-02-19 11:28:34.118 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 11:28:34.550 Finished recording : channel 4294967295
2008-02-19 11:29:51.791 MainServer::HandleAnnounce Monitor
2008-02-19 11:29:51.824 adding: mythical as a client (events: 0)
2008-02-19 11:29:51.854 MainServer::HandleAnnounce Monitor
2008-02-19 11:29:51.895 adding: mythical as a client (events: 1)
2008-02-19 11:29:51.927 MainServer::HandleAnnounce Playback
2008-02-19 11:29:51.965 adding: mythical as a client (events: 0)
2008-02-19 11:29:51.989 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 11:29:52.021 TVRec(1): HW Tuner: 1->1
2008-02-19 11:29:52.062 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:29:52.095 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:29:52.736 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 11:29:52.805 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:29:52 2008) endts(Tue Feb 19 11:29:52 2008)
             recstartts(Tue Feb 19 11:29:52 2008) recendts(Tue Feb 19 11:29:52 2008)
             title()
2008-02-19 11:29:52.888 Unknown video codec
2008-02-19 11:29:52.997 Please go into the TV Settings, Recording Profiles and
2008-02-19 11:29:53.064 setup the four 'Software Encoders' profiles.
2008-02-19 11:29:53.089 Assuming RTjpeg for now.
2008-02-19 11:29:53.130 NVR: Error, unknown audio codec
2008-02-19 11:29:53.177 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 11:30:00.251 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:30:00.412 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:30:00.462 TVRec(1) Error: Failed to set channel to 48.
2008-02-19 11:30:00.501 Finished recording : channel 4294967295
2008-02-19 11:30:00.530 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:30:00 2008) endts(Tue Feb 19 11:30:00 2008)
             recstartts(Tue Feb 19 11:30:00 2008) recendts(Tue Feb 19 11:30:00 2008)
             title()
2008-02-19 11:30:00.626 Finished recording : channel 4294967295
2008-02-19 11:30:00.732 TVRec(1): RingBufferChanged()
2008-02-19 11:30:00.803 Finished recording : channel 4294967295
2008-02-19 11:30:03.251 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:30:03.275 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:30:03.309 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 11:30:03.367 Finished recording : channel 4294967295
2008-02-19 11:30:03.393 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:30:03 2008) endts(Tue Feb 19 11:30:03 2008)
             recstartts(Tue Feb 19 11:30:03 2008) recendts(Tue Feb 19 11:30:03 2008)
             title()
2008-02-19 11:30:03.485 Finished recording : channel 4294967295
2008-02-19 11:30:03.643 TVRec(1): RingBufferChanged()
2008-02-19 11:30:03.750 Finished recording : channel 4294967295
2008-02-19 11:30:06.560 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 11:30:06.915 Finished recording : channel 4294967295
2008-02-19 11:31:09.083 Using runtime prefix = /usr
2008-02-19 11:31:09.140 New DB connection, total: 1
2008-02-19 11:31:09.173 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:31:09.205 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 11:31:09.283 New DB connection, total: 2
2008-02-19 11:31:09.335 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:31:09.362 EITHelper: localtime offset -6:00:00 
2008-02-19 11:31:09.400 New DB connection, total: 3
2008-02-19 11:31:09.447 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:31:09.492 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:31:09.530 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:31:09.567 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:31:09.597 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:31:09.617 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 11:31:09.670 New DB scheduler connection
2008-02-19 11:31:09.697 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:31:11.083 Main::Registering HttpStatus Extension
2008-02-19 11:31:11.120 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 11:31:11.153 Enabled verbose msgs:  important general
2008-02-19 11:31:11.186 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 11:31:11.221 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 11:31:11.763 Reschedule requested for id -1.
2008-02-19 11:31:11.828 Scheduled 0 items in 0.1 = 0.04 match + 0.02 place
2008-02-19 11:31:11.852 Seem to be woken up by USER
2008-02-19 11:32:29.754 Expiring  from Tue Feb 19 11:28:11 2008, 1 MBytes, forced expire (LiveTV recording)
2008-02-19 11:32:29.798 Expiring  from Tue Feb 19 11:28:16 2008, 1 MBytes, forced expire (LiveTV recording)
2008-02-19 11:32:29.826 Expiring  from Tue Feb 19 11:28:21 2008, 5 MBytes, forced expire (LiveTV recording)
2008-02-19 11:32:29.859 Expiring  from Tue Feb 19 11:29:52 2008, 16 MBytes, forced expire (LiveTV recording)
2008-02-19 11:32:29.889 Expiring  from Tue Feb 19 11:30:00 2008, 5 MBytes, forced expire (LiveTV recording)
2008-02-19 11:32:29.918 Expiring  from Tue Feb 19 11:30:03 2008, 6 MBytes, forced expire (LiveTV recording)
2008-02-19 11:36:35.105 MainServer::HandleAnnounce Monitor
2008-02-19 11:36:35.142 adding: banana as a client (events: 0)
2008-02-19 11:36:35.171 MainServer::HandleAnnounce Monitor
2008-02-19 11:36:35.203 adding: banana as a client (events: 1)
2008-02-19 11:36:35.232 MainServer::HandleAnnounce Playback
2008-02-19 11:36:35.276 adding: banana as a client (events: 0)
2008-02-19 11:36:35.305 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 11:36:35.345 TVRec(1): HW Tuner: 1->1
2008-02-19 11:36:35.385 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:36:35.425 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:36:35.467 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 11:36:35.532 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:36:35 2008) endts(Tue Feb 19 11:36:35 2008)
             recstartts(Tue Feb 19 11:36:35 2008) recendts(Tue Feb 19 11:36:35 2008)
             title()
2008-02-19 11:36:35.657 Unknown video codec
2008-02-19 11:36:35.677 Please go into the TV Settings, Recording Profiles and
2008-02-19 11:36:35.719 setup the four 'Software Encoders' profiles.
2008-02-19 11:36:35.761 Assuming RTjpeg for now.
2008-02-19 11:36:35.802 NVR: Error, unknown audio codec
2008-02-19 11:36:35.866 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 11:36:35.895 MainServer::HandleAnnounce Playback
2008-02-19 11:36:35.944 adding: banana as a client (events: 0)
2008-02-19 11:36:36.020 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:36:36.060 adding: banana as a remote file transfer
2008-02-19 11:36:42.682 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:36:42.716 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:36:42.766 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 11:36:42.799 Finished recording : channel 4294967295
2008-02-19 11:36:42.839 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:36:42 2008) endts(Tue Feb 19 11:36:42 2008)
             recstartts(Tue Feb 19 11:36:42 2008) recendts(Tue Feb 19 11:36:42 2008)
             title()
2008-02-19 11:36:42.931 Finished recording : channel 4294967295
2008-02-19 11:36:43.275 TVRec(1): RingBufferChanged()
2008-02-19 11:36:43.389 Finished recording : channel 4294967295
2008-02-19 11:36:43.505 MainServer::HandleAnnounce Playback
2008-02-19 11:36:43.540 adding: banana as a client (events: 0)
2008-02-19 11:36:43.583 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:36:43.656 adding: banana as a remote file transfer
2008-02-19 11:36:48.658 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 11:36:49.039 Finished recording : channel 4294967295
2008-02-19 11:38:29.971 Expiring  from Tue Feb 19 11:36:35 2008, 17 MBytes, forced expire (LiveTV recording)
2008-02-19 11:38:30.013 Expiring  from Tue Feb 19 11:36:42 2008, 13 MBytes, forced expire (LiveTV recording)
2008-02-19 11:55:53.180 Using runtime prefix = /usr
2008-02-19 11:55:53.237 New DB connection, total: 1
2008-02-19 11:55:53.267 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:55:53.308 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 11:55:53.386 New DB connection, total: 2
2008-02-19 11:55:53.420 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:55:53.456 EITHelper: localtime offset -6:00:00 
2008-02-19 11:55:53.495 New DB connection, total: 3
2008-02-19 11:55:53.528 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:55:53.575 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:55:53.611 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:55:53.649 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:55:53.703 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:55:53.736 TVRec(1) Error: Setting start channel '69' failed, 
			and backup '8' failed as well.
2008-02-19 11:55:53.798 New DB scheduler connection
2008-02-19 11:55:53.828 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:55:55.216 Main::Registering HttpStatus Extension
2008-02-19 11:55:55.259 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 11:55:55.293 Enabled verbose msgs:  important general
2008-02-19 11:55:55.334 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 11:55:55.369 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 11:55:55.879 Reschedule requested for id -1.
2008-02-19 11:55:55.943 Scheduled 0 items in 0.1 = 0.04 match + 0.02 place
2008-02-19 11:55:55.971 Seem to be woken up by USER
2008-02-19 11:55:56.882 MainServer::HandleAnnounce Monitor
2008-02-19 11:55:56.915 adding: banana as a client (events: 0)
2008-02-19 11:55:56.941 MainServer::HandleAnnounce Monitor
2008-02-19 11:55:56.973 adding: banana as a client (events: 1)
2008-02-19 11:56:15.683 MainServer::HandleAnnounce Monitor
2008-02-19 11:56:15.715 adding: banana as a client (events: 0)
2008-02-19 11:56:15.749 MainServer::HandleAnnounce Monitor
2008-02-19 11:56:15.781 adding: banana as a client (events: 1)
2008-02-19 11:56:15.812 MainServer::HandleAnnounce Playback
2008-02-19 11:56:15.831 adding: banana as a client (events: 0)
2008-02-19 11:56:15.866 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 11:56:15.890 TVRec(1): HW Tuner: 1->1
2008-02-19 11:56:15.922 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:56:15.956 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:56:15.981 TVRec(1) Error: Failed to set channel to 69.
2008-02-19 11:56:16.053 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:56:16 2008) endts(Tue Feb 19 11:56:16 2008)
             recstartts(Tue Feb 19 11:56:16 2008) recendts(Tue Feb 19 11:56:16 2008)
             title()
2008-02-19 11:56:16.188 Unknown video codec
2008-02-19 11:56:16.222 Please go into the TV Settings, Recording Profiles and
2008-02-19 11:56:16.256 setup the four 'Software Encoders' profiles.
2008-02-19 11:56:16.280 Assuming RTjpeg for now.
2008-02-19 11:56:16.314 NVR: Error, unknown audio codec
2008-02-19 11:56:16.359 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 11:56:16.368 MainServer::HandleAnnounce Playback
2008-02-19 11:56:16.456 adding: banana as a client (events: 0)
2008-02-19 11:56:16.590 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:56:16.647 adding: banana as a remote file transfer
2008-02-19 11:56:21.952 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:56:21.990 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:56:22.040 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 11:56:22.087 Finished recording : channel 4294967295
2008-02-19 11:56:22.127 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:56:22 2008) endts(Tue Feb 19 11:56:22 2008)
             recstartts(Tue Feb 19 11:56:22 2008) recendts(Tue Feb 19 11:56:22 2008)
             title()
2008-02-19 11:56:22.220 Finished recording : channel 4294967295
2008-02-19 11:56:22.525 TVRec(1): RingBufferChanged()
2008-02-19 11:56:22.613 Finished recording : channel 4294967295
2008-02-19 11:56:22.696 MainServer::HandleAnnounce Playback
2008-02-19 11:56:22.730 adding: banana as a client (events: 0)
2008-02-19 11:56:22.764 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:56:22.796 adding: banana as a remote file transfer
2008-02-19 11:56:29.936 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:56:30.037 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:56:30.079 TVRec(1) Error: Failed to set channel to 69.
2008-02-19 11:56:30.133 Finished recording : channel 4294967295
2008-02-19 11:56:30.175 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:56:30 2008) endts(Tue Feb 19 11:56:30 2008)
             recstartts(Tue Feb 19 11:56:30 2008) recendts(Tue Feb 19 11:56:30 2008)
             title()
2008-02-19 11:56:30.267 Finished recording : channel 4294967295
2008-02-19 11:56:30.447 TVRec(1): RingBufferChanged()
2008-02-19 11:56:30.527 Finished recording : channel 4294967295
2008-02-19 11:56:30.747 MainServer::HandleAnnounce Playback
2008-02-19 11:56:30.778 adding: banana as a client (events: 0)
2008-02-19 11:56:30.813 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:56:30.845 adding: banana as a remote file transfer
2008-02-19 11:56:39.235 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:56:39.267 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:56:39.300 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 11:56:39.354 Finished recording : channel 4294967295
2008-02-19 11:56:39.386 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:56:39 2008) endts(Tue Feb 19 11:56:39 2008)
             recstartts(Tue Feb 19 11:56:39 2008) recendts(Tue Feb 19 11:56:39 2008)
             title()
2008-02-19 11:56:39.486 Finished recording : channel 4294967295
2008-02-19 11:56:39.643 TVRec(1): RingBufferChanged()
2008-02-19 11:56:39.731 Finished recording : channel 4294967295
2008-02-19 11:56:39.937 MainServer::HandleAnnounce Playback
2008-02-19 11:56:39.974 adding: banana as a client (events: 0)
2008-02-19 11:56:40.009 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:56:40.031 adding: banana as a remote file transfer
2008-02-19 11:56:41.738 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:56:41.772 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:56:41.805 TVRec(1) Error: Failed to set channel to 8.
2008-02-19 11:56:41.849 Finished recording : channel 4294967295
2008-02-19 11:56:41.891 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 11:56:41 2008) endts(Tue Feb 19 11:56:41 2008)
             recstartts(Tue Feb 19 11:56:41 2008) recendts(Tue Feb 19 11:56:41 2008)
             title()
2008-02-19 11:56:41.975 Finished recording : channel 4294967295
2008-02-19 11:56:42.191 TVRec(1): RingBufferChanged()
2008-02-19 11:56:42.278 Finished recording : channel 4294967295
2008-02-19 11:56:42.621 MainServer::HandleAnnounce Playback
2008-02-19 11:56:42.654 adding: banana as a client (events: 0)
2008-02-19 11:56:42.695 MainServer::HandleAnnounce FileTransfer
2008-02-19 11:56:42.761 adding: banana as a remote file transfer
2008-02-19 11:56:44.372 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 11:56:44.764 Finished recording : channel 4294967295
2008-02-19 11:57:26.812 Using runtime prefix = /usr
2008-02-19 11:57:26.861 New DB connection, total: 1
2008-02-19 11:57:26.890 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:57:26.940 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 11:57:27.026 New DB connection, total: 2
2008-02-19 11:57:27.061 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:57:27.097 EITHelper: localtime offset -6:00:00 
2008-02-19 11:57:27.125 New DB connection, total: 3
2008-02-19 11:57:27.159 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:57:27.199 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:57:27.235 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:57:27.273 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 11:57:27.291 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 11:57:27.333 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 11:57:27.395 New DB scheduler connection
2008-02-19 11:57:27.433 Connected to database 'mythconverg' at host: localhost
2008-02-19 11:57:28.813 Main::Registering HttpStatus Extension
2008-02-19 11:57:28.856 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 11:57:28.897 Enabled verbose msgs:  important general
2008-02-19 11:57:28.931 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 11:57:28.974 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 11:57:29.473 Reschedule requested for id -1.
2008-02-19 11:57:29.558 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2008-02-19 11:57:29.596 Seem to be woken up by USER
2008-02-19 11:58:47.481 Expiring  from Tue Feb 19 11:56:16 2008, 13 MBytes, forced expire (LiveTV recording)
2008-02-19 11:58:47.518 Expiring  from Tue Feb 19 11:56:22 2008, 18 MBytes, forced expire (LiveTV recording)
2008-02-19 11:58:47.548 Expiring  from Tue Feb 19 11:56:30 2008, 21 MBytes, forced expire (LiveTV recording)
2008-02-19 11:58:47.582 Expiring  from Tue Feb 19 11:56:39 2008, 3 MBytes, forced expire (LiveTV recording)
2008-02-19 11:58:47.609 Expiring  from Tue Feb 19 11:56:41 2008, 4 MBytes, forced expire (LiveTV recording)
2008-02-19 12:24:21.299 MainServer::HandleAnnounce Monitor
2008-02-19 12:24:21.330 adding: mythical as a client (events: 0)
2008-02-19 12:24:21.356 MainServer::HandleAnnounce Monitor
2008-02-19 12:24:21.388 adding: mythical as a client (events: 1)
2008-02-19 12:24:21.420 MainServer::HandleAnnounce Playback
2008-02-19 12:24:21.455 adding: mythical as a client (events: 0)
2008-02-19 12:24:21.482 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 12:24:21.523 TVRec(1): HW Tuner: 1->1
2008-02-19 12:24:21.559 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 12:24:21.588 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 12:24:21.621 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 12:24:21.708 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 12:24:21 2008) endts(Tue Feb 19 12:24:21 2008)
             recstartts(Tue Feb 19 12:24:21 2008) recendts(Tue Feb 19 12:24:21 2008)
             title()
2008-02-19 12:24:21.889 Unknown video codec
2008-02-19 12:24:21.921 Please go into the TV Settings, Recording Profiles and
2008-02-19 12:24:21.971 setup the four 'Software Encoders' profiles.
2008-02-19 12:24:22.013 Assuming RTjpeg for now.
2008-02-19 12:24:22.038 NVR: Error, unknown audio codec
2008-02-19 12:24:22.095 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 12:26:01.658 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 12:26:02.132 Finished recording : channel 4294967295
2008-02-19 12:26:37.085 Reschedule requested for id 1.
2008-02-19 12:26:37.165 Scheduled 1 items in 0.1 = 0.06 match + 0.02 place
2008-02-19 12:28:47.818 Expiring  from Tue Feb 19 12:24:21 2008, 308 MBytes, forced expire (LiveTV recording)
QSqlQuery::exec: database not open
2008-02-19 13:14:37.957 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-02-19 13:14:38.135 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
No error type from QSqlError?  Strange...
2008-02-19 13:14:48.011 Unable to connect to database!
2008-02-19 13:14:48.055 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:14:48.213 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-02-19 13:14:48.421 Unable to connect to database!
2008-02-19 13:14:48.479 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:14:48.629 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-02-19 13:15:38.169 Unable to connect to database!
2008-02-19 13:15:38.444 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:15:38.610 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-02-19 13:15:38.777 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
No error type from QSqlError?  Strange...
2008-02-19 13:15:48.780 Unable to connect to database!
2008-02-19 13:15:48.838 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:15:49.054 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-02-19 13:16:38.810 Unable to connect to database!
2008-02-19 13:16:38.842 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:16:38.975 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-02-19 13:16:39.141 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
No error type from QSqlError?  Strange...
2008-02-19 13:27:39.032 Using runtime prefix = /usr
2008-02-19 13:27:39.094 New DB connection, total: 1
2008-02-19 13:27:39.116 Unable to connect to database!
2008-02-19 13:27:39.148 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:27:39.314 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-19 13:27:39.398 Failed to init MythContext, exiting.
2008-02-19 13:27:48.374 Using runtime prefix = /usr
2008-02-19 13:27:48.442 New DB connection, total: 1
2008-02-19 13:27:48.464 Unable to connect to database!
2008-02-19 13:27:48.504 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-19 13:27:48.646 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-19 13:27:48.730 Failed to init MythContext, exiting.
2008-02-19 13:30:38.931 Using runtime prefix = /usr
2008-02-19 13:30:39.147 New DB connection, total: 1
2008-02-19 13:30:39.192 Connected to database 'mythconverg' at host: localhost
2008-02-19 13:30:39.312 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 13:30:39.647 New DB connection, total: 2
2008-02-19 13:30:39.798 Connected to database 'mythconverg' at host: localhost
2008-02-19 13:30:39.981 EITHelper: localtime offset -6:00:00 
2008-02-19 13:30:40.155 New DB connection, total: 3
2008-02-19 13:30:40.186 Connected to database 'mythconverg' at host: localhost
2008-02-19 13:30:40.246 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 13:30:40.310 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 13:30:40.382 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 13:30:40.476 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 13:30:40.538 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 13:30:40.773 New DB scheduler connection
2008-02-19 13:30:40.830 Connected to database 'mythconverg' at host: localhost
2008-02-19 13:30:42.260 Main::Registering HttpStatus Extension
2008-02-19 13:30:42.291 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 13:30:42.316 Enabled verbose msgs:  important general
2008-02-19 13:30:42.367 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 13:30:42.401 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 13:30:42.919 Reschedule requested for id -1.
2008-02-19 13:30:43.030 Scheduled 1 items in 0.1 = 0.07 match + 0.04 place
2008-02-19 13:30:43.070 Recording starts soon, AUTO-Startup assumed
2008-02-19 13:30:43.248 TVRec(1): Changing from None to RecordingOnly
2008-02-19 13:30:43.292 TVRec(1): HW Tuner: 1->1
2008-02-19 13:30:43.327 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 13:30:43.359 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 13:30:43.381 TVRec(1) Error: Failed to set channel to 13. Reverting to kState_None
2008-02-19 13:30:43.406 TVRec(1): Changing from RecordingOnly to None
2008-02-19 13:30:43.515 Canceled recording (Recorder Failed): Family Feud (Manual Record) "Tue Feb 19 13:30:00 2008": channel 1001 on cardid 1, sourceid 1
2008-02-19 13:30:46.590 Error deleting '/var/lib/mythtv/recordings/1001_20080219133100.nuv': No such file or directory
2008-02-19 13:30:49.629 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2008-02-17T13:30:49') OR (status in (304) AND statustime < '2008-02-15T13:30:49')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:49.661 DB Error (HouseKeeper Cleaning Recorded Tables):
Query was:
SELECT DISTINCT p.chanid, p.starttime FROM recordedprogram p LEFT JOIN recorded r ON p.chanid = r.chanid AND p.starttime = r.progstart WHERE r.chanid IS NULL;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:49.733 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:50.918 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:52.630 DB Error (Recorded program delete recordedmarkup):
Query was:
DELETE FROM recordedmarkup WHERE chanid = '1001' AND starttime = '2008-02-19T13:31:00';
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:52.673 DB Error (Recorded program delete recordedseek):
Query was:
DELETE FROM recordedseek WHERE chanid = '1001' AND starttime = '2008-02-19T13:31:00';
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:52.714 Reschedule requested for id 0.
2008-02-19 13:30:52.756 DB Error (CheckTooMany):
Query was:
SELECT recordid,title,maxepisodes,maxnewest FROM record;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:52.807 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.startdate, record.endtime, record.enddate, record.startoffset, record.endoffset, record.title, record.subtitle, record.description, channel.channum, channel.callsign, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.chanid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-02-19 13:30:52.847 Scheduled 0 items in 0.1 = 0.04 match + 0.09 place
2008-02-19 13:30:57.793 MainServer::HandleAnnounce Monitor
2008-02-19 13:30:57.839 adding: mythical as a client (events: 0)
2008-02-19 13:30:59.543 MainServer::HandleAnnounce Monitor
2008-02-19 13:30:59.567 adding: mythical as a client (events: 0)
2008-02-19 13:31:02.477 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:02.521 adding: mythical as a client (events: 0)
2008-02-19 13:31:05.674 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:05.709 adding: mythical as a client (events: 0)
2008-02-19 13:31:05.751 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-02-19 13:31:07.615 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:07.648 adding: mythical as a client (events: 0)
2008-02-19 13:31:09.329 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:09.373 adding: mythical as a client (events: 0)
2008-02-19 13:31:15.960 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:15.997 adding: mythical as a client (events: 0)
2008-02-19 13:31:16.141 Reschedule requested for id 1.
2008-02-19 13:31:16.206 Scheduled 1 items in 0.1 = 0.05 match + 0.01 place
2008-02-19 13:31:17.184 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:17.220 adding: mythical as a client (events: 0)
2008-02-19 13:31:19.904 MainServer::HandleAnnounce Monitor
2008-02-19 13:31:19.941 adding: mythical as a client (events: 0)
2008-02-19 14:00:02.499 TVRec(1): Changing from None to RecordingOnly
2008-02-19 14:00:02.532 TVRec(1): HW Tuner: 1->1
2008-02-19 14:00:02.628 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:00:02.661 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:00:02.687 TVRec(1) Error: Failed to set channel to 13. Reverting to kState_None
2008-02-19 14:00:02.728 TVRec(1): Changing from RecordingOnly to None
2008-02-19 14:00:02.774 Canceled recording (Recorder Failed): Family Feud (Manual Record) "Tue Feb 19 14:00:00 2008": channel 1001 on cardid 1, sourceid 1
2008-02-19 14:00:05.842 Error deleting '/var/lib/mythtv/recordings/1001_20080219140000.nuv': No such file or directory
2008-02-19 14:00:11.897 Reschedule requested for id 0.
2008-02-19 14:00:11.953 Scheduled 1 items in 0.1 = 0.04 match + 0.01 place
2008-02-19 14:09:28.338 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:28.379 adding: mythical as a client (events: 0)
2008-02-19 14:09:30.012 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:30.051 adding: mythical as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-02-19 14:09:35.475 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:35.511 adding: mythical as a client (events: 0)
2008-02-19 14:09:38.638 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:38.673 adding: mythical as a client (events: 0)
2008-02-19 14:09:54.751 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:54.791 adding: mythical as a client (events: 0)
2008-02-19 14:09:54.873 Reschedule requested for id 2.
2008-02-19 14:09:54.937 Scheduled 2 items in 0.1 = 0.05 match + 0.02 place
2008-02-19 14:09:56.010 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:56.048 adding: mythical as a client (events: 0)
2008-02-19 14:09:59.173 MainServer::HandleAnnounce Monitor
2008-02-19 14:09:59.210 adding: mythical as a client (events: 0)
2008-02-19 14:10:00.625 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:00.660 adding: mythical as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-02-19 14:10:09.221 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:09.255 adding: mythical as a client (events: 0)
2008-02-19 14:10:16.468 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:16.505 adding: mythical as a client (events: 0)
2008-02-19 14:10:16.573 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:16.613 adding: mythical as a client (events: 0)
2008-02-19 14:10:21.719 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:21.754 adding: mythical as a client (events: 0)
2008-02-19 14:10:21.824 Reschedule requested for id 1.
2008-02-19 14:10:21.874 Scheduled 1 items in 0.0 = 0.04 match + 0.01 place
2008-02-19 14:10:22.944 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:22.980 adding: mythical as a client (events: 0)
2008-02-19 14:10:24.324 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:24.361 adding: mythical as a client (events: 0)
2008-02-19 14:10:27.820 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:27.854 adding: mythical as a client (events: 0)
2008-02-19 14:10:31.448 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:31.491 adding: mythical as a client (events: 0)
2008-02-19 14:10:32.808 MainServer::HandleAnnounce Monitor
2008-02-19 14:10:32.841 adding: mythical as a client (events: 0)
2008-02-19 14:11:03.032 TVRec(1): Changing from None to RecordingOnly
2008-02-19 14:11:03.067 TVRec(1): HW Tuner: 1->1
2008-02-19 14:11:03.104 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:11:03.150 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:11:03.183 TVRec(1) Error: Failed to set channel to 13. Reverting to kState_None
2008-02-19 14:11:03.216 TVRec(1): Changing from RecordingOnly to None
2008-02-19 14:11:03.269 Canceled recording (Recorder Failed): Family Feud (Manual Record) "Tue Feb 19 14:11:00 2008": channel 1001 on cardid 1, sourceid 1
2008-02-19 14:11:06.321 Error deleting '/var/lib/mythtv/recordings/1001_20080219141100.nuv': No such file or directory
2008-02-19 14:11:12.361 Reschedule requested for id 0.
2008-02-19 14:11:12.409 Scheduled 1 items in 0.0 = 0.03 match + 0.01 place
2008-02-19 14:11:28.299 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:28.330 adding: mythical as a client (events: 0)
2008-02-19 14:11:28.414 Reschedule requested for id 3.
2008-02-19 14:11:28.474 Scheduled 2 items in 0.1 = 0.04 match + 0.02 place
2008-02-19 14:11:29.544 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:29.578 adding: mythical as a client (events: 0)
2008-02-19 14:11:35.165 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:35.212 adding: mythical as a client (events: 0)
2008-02-19 14:11:42.320 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:42.355 adding: mythical as a client (events: 0)
2008-02-19 14:11:47.860 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:47.898 adding: mythical as a client (events: 0)
2008-02-19 14:11:47.971 Reschedule requested for id 3.
2008-02-19 14:11:48.015 Scheduled 2 items in 0.0 = 0.03 match + 0.02 place
2008-02-19 14:11:49.079 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:49.113 adding: mythical as a client (events: 0)
2008-02-19 14:11:51.748 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:51.781 adding: mythical as a client (events: 0)
2008-02-19 14:11:54.675 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:54.705 adding: mythical as a client (events: 0)
2008-02-19 14:11:56.331 MainServer::HandleAnnounce Monitor
2008-02-19 14:11:56.361 adding: mythical as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-02-19 14:12:03.434 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:03.477 adding: mythical as a client (events: 0)
2008-02-19 14:12:10.658 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:10.689 adding: mythical as a client (events: 0)
2008-02-19 14:12:10.890 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:10.922 adding: mythical as a client (events: 0)
2008-02-19 14:12:12.585 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:12.622 adding: mythical as a client (events: 0)
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-02-19 14:12:13.915 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:13.943 adding: mythical as a client (events: 0)
2008-02-19 14:12:16.535 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:16.576 adding: mythical as a client (events: 0)
2008-02-19 14:12:21.039 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:21.078 adding: mythical as a client (events: 0)
2008-02-19 14:12:22.275 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:22.323 adding: mythical as a client (events: 0)
2008-02-19 14:12:29.485 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:29.525 adding: mythical as a client (events: 0)
2008-02-19 14:12:29.609 Reschedule requested for id 2.
2008-02-19 14:12:29.669 Scheduled 1 items in 0.1 = 0.05 match + 0.01 place
2008-02-19 14:12:30.615 Reschedule requested for id 4.
2008-02-19 14:12:30.675 Scheduled 2 items in 0.1 = 0.05 match + 0.02 place
2008-02-19 14:12:31.713 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:31.743 adding: mythical as a client (events: 0)
2008-02-19 14:12:34.512 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:34.560 adding: mythical as a client (events: 0)
2008-02-19 14:12:35.597 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:35.633 adding: mythical as a client (events: 0)
2008-02-19 14:12:41.116 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:41.151 adding: mythical as a client (events: 0)
2008-02-19 14:12:41.233 Reschedule requested for id 4.
2008-02-19 14:12:41.287 Scheduled 1 items in 0.1 = 0.04 match + 0.01 place
2008-02-19 14:12:42.352 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:42.391 adding: mythical as a client (events: 0)
2008-02-19 14:12:44.679 MainServer::HandleAnnounce Monitor
2008-02-19 14:12:44.712 adding: mythical as a client (events: 0)
2008-02-19 14:15:14.536 MainServer::HandleAnnounce Monitor
2008-02-19 14:15:14.574 adding: banana as a client (events: 0)
2008-02-19 14:15:14.608 MainServer::HandleAnnounce Monitor
2008-02-19 14:15:14.632 adding: banana as a client (events: 1)
2008-02-19 14:15:14.672 MainServer::HandleAnnounce Playback
2008-02-19 14:15:14.707 adding: banana as a client (events: 0)
2008-02-19 14:15:14.767 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:15:14.809 TVRec(1): HW Tuner: 1->1
2008-02-19 14:15:14.862 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:15:14.907 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:15:14.940 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:15:15.107 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:15:15 2008) endts(Tue Feb 19 14:15:15 2008)
             recstartts(Tue Feb 19 14:15:15 2008) recendts(Tue Feb 19 14:15:15 2008)
             title()
2008-02-19 14:15:15.300 Unknown video codec
2008-02-19 14:15:15.344 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:15:15.386 setup the four 'Software Encoders' profiles.
2008-02-19 14:15:15.415 Assuming RTjpeg for now.
2008-02-19 14:15:15.444 NVR: Error, unknown audio codec
2008-02-19 14:15:15.516 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:15:15.550 MainServer::HandleAnnounce Playback
2008-02-19 14:15:15.614 adding: banana as a client (events: 0)
2008-02-19 14:15:15.657 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:15:15.723 adding: banana as a remote file transfer
2008-02-19 14:15:22.701 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:15:22.738 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:15:22.780 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 14:15:22.816 Finished recording : channel 4294967295
2008-02-19 14:15:22.857 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:15:22 2008) endts(Tue Feb 19 14:15:22 2008)
             recstartts(Tue Feb 19 14:15:22 2008) recendts(Tue Feb 19 14:15:22 2008)
             title()
2008-02-19 14:15:22.968 Finished recording : channel 4294967295
2008-02-19 14:15:23.132 TVRec(1): RingBufferChanged()
2008-02-19 14:15:23.231 Finished recording : channel 4294967295
2008-02-19 14:15:25.715 MainServer::HandleAnnounce Playback
2008-02-19 14:15:25.751 adding: banana as a client (events: 0)
2008-02-19 14:15:25.794 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:15:25.821 adding: banana as a remote file transfer
2008-02-19 14:15:29.116 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:15:29.526 Finished recording : channel 4294967295
2008-02-19 14:16:01.046 Expiring  from Tue Feb 19 14:15:15 2008, 1 MBytes, forced expire (LiveTV recording)
2008-02-19 14:16:01.078 Expiring  from Tue Feb 19 14:15:22 2008, 1 MBytes, forced expire (LiveTV recording)
2008-02-19 14:32:21.300 MainServer::HandleAnnounce Monitor
2008-02-19 14:32:21.342 adding: mythical as a client (events: 0)
2008-02-19 14:32:21.376 MainServer::HandleAnnounce Monitor
2008-02-19 14:32:21.417 adding: mythical as a client (events: 1)
2008-02-19 14:33:17.312 MainServer::HandleAnnounce Monitor
2008-02-19 14:33:17.348 adding: mythical as a client (events: 0)
2008-02-19 14:33:17.412 MainServer::HandleAnnounce Monitor
2008-02-19 14:33:17.464 adding: mythical as a client (events: 1)
2008-02-19 14:33:17.549 MainServer::HandleAnnounce Playback
2008-02-19 14:33:17.580 adding: mythical as a client (events: 0)
2008-02-19 14:33:17.620 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:33:17.674 TVRec(1): HW Tuner: 1->1
2008-02-19 14:33:17.813 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:33:17.846 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:33:17.880 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:33:17.963 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:33:17 2008) endts(Tue Feb 19 14:33:17 2008)
             recstartts(Tue Feb 19 14:33:17 2008) recendts(Tue Feb 19 14:33:17 2008)
             title()
2008-02-19 14:33:18.062 Unknown video codec
2008-02-19 14:33:18.088 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:33:18.121 setup the four 'Software Encoders' profiles.
2008-02-19 14:33:18.154 Assuming RTjpeg for now.
2008-02-19 14:33:18.188 NVR: Error, unknown audio codec
2008-02-19 14:33:18.250 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:33:36.558 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:33:37.001 Finished recording : channel 4294967295
2008-02-19 14:33:45.688 MainServer::HandleAnnounce Playback
2008-02-19 14:33:45.718 adding: mythical as a client (events: 0)
2008-02-19 14:33:45.755 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:33:45.797 TVRec(1): HW Tuner: 1->1
2008-02-19 14:33:45.860 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:33:45.901 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:33:45.934 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:33:46.111 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:33:46 2008) endts(Tue Feb 19 14:33:46 2008)
             recstartts(Tue Feb 19 14:33:46 2008) recendts(Tue Feb 19 14:33:46 2008)
             title()
2008-02-19 14:33:46.224 Unknown video codec
2008-02-19 14:33:46.258 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:33:46.291 setup the four 'Software Encoders' profiles.
2008-02-19 14:33:46.325 Assuming RTjpeg for now.
2008-02-19 14:33:46.367 NVR: Error, unknown audio codec
2008-02-19 14:33:46.413 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:34:08.624 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:34:09.169 Finished recording : channel 4294967295
2008-02-19 14:35:40.819 Using runtime prefix = /usr
2008-02-19 14:35:40.896 New DB connection, total: 1
2008-02-19 14:35:40.928 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:35:40.970 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 14:35:41.074 New DB connection, total: 2
2008-02-19 14:35:41.103 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:35:41.139 EITHelper: localtime offset -6:00:00 
2008-02-19 14:35:41.258 New DB connection, total: 3
2008-02-19 14:35:41.286 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:35:41.339 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:35:41.377 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:35:41.423 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:35:41.460 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:35:41.512 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 14:35:41.584 New DB scheduler connection
2008-02-19 14:35:41.786 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:35:43.297 Main::Registering HttpStatus Extension
2008-02-19 14:35:43.334 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 14:35:43.366 Enabled verbose msgs:  important general
2008-02-19 14:35:43.400 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 14:35:43.438 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 14:35:44.068 Reschedule requested for id -1.
2008-02-19 14:35:44.381 Scheduled 1 items in 0.3 = 0.23 match + 0.09 place
2008-02-19 14:35:44.424 Seem to be woken up by USER
2008-02-19 14:35:49.454 MainServer::HandleAnnounce Monitor
2008-02-19 14:35:49.484 adding: mythical as a client (events: 0)
2008-02-19 14:35:49.520 MainServer::HandleAnnounce Monitor
2008-02-19 14:35:49.549 adding: mythical as a client (events: 1)
2008-02-19 14:35:49.613 MainServer::HandleAnnounce Playback
2008-02-19 14:35:49.651 adding: mythical as a client (events: 0)
2008-02-19 14:35:49.684 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:35:49.750 TVRec(1): HW Tuner: 1->1
2008-02-19 14:35:49.799 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:35:49.842 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:35:49.875 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:35:49.978 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:35:49 2008) endts(Tue Feb 19 14:35:49 2008)
             recstartts(Tue Feb 19 14:35:49 2008) recendts(Tue Feb 19 14:35:49 2008)
             title()
2008-02-19 14:35:50.182 Unknown video codec
2008-02-19 14:35:50.208 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:35:50.241 setup the four 'Software Encoders' profiles.
2008-02-19 14:35:50.273 Assuming RTjpeg for now.
2008-02-19 14:35:50.306 NVR: Error, unknown audio codec
2008-02-19 14:35:50.366 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:36:01.838 Expiring  from Tue Feb 19 14:33:17 2008, 51 MBytes, forced expire (LiveTV recording)
2008-02-19 14:36:01.897 Expiring  from Tue Feb 19 14:33:46 2008, 66 MBytes, forced expire (LiveTV recording)
2008-02-19 14:36:06.239 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:36:06.910 Finished recording : channel 4294967295
2008-02-19 14:36:56.953 MainServer::HandleAnnounce Monitor
2008-02-19 14:36:56.993 adding: banana as a client (events: 0)
2008-02-19 14:36:57.027 MainServer::HandleAnnounce Monitor
2008-02-19 14:36:57.057 adding: banana as a client (events: 1)
2008-02-19 14:36:57.094 MainServer::HandleAnnounce Playback
2008-02-19 14:36:57.118 adding: banana as a client (events: 0)
2008-02-19 14:36:57.154 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:36:57.175 TVRec(1): HW Tuner: 1->1
2008-02-19 14:36:57.226 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:36:57.276 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:36:57.309 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:36:57.398 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:36:57 2008) endts(Tue Feb 19 14:36:57 2008)
             recstartts(Tue Feb 19 14:36:57 2008) recendts(Tue Feb 19 14:36:57 2008)
             title()
2008-02-19 14:36:57.496 Unknown video codec
2008-02-19 14:36:57.559 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:36:57.617 setup the four 'Software Encoders' profiles.
2008-02-19 14:36:57.650 Assuming RTjpeg for now.
2008-02-19 14:36:57.692 NVR: Error, unknown audio codec
2008-02-19 14:36:57.745 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:36:57.759 MainServer::HandleAnnounce Playback
2008-02-19 14:36:57.867 adding: banana as a client (events: 0)
2008-02-19 14:36:57.901 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:36:57.942 adding: banana as a remote file transfer
2008-02-19 14:37:06.943 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:37:07.395 Finished recording : channel 4294967295
2008-02-19 14:38:01.973 Expiring  from Tue Feb 19 14:35:49 2008, 44 MBytes, forced expire (LiveTV recording)
2008-02-19 14:38:02.005 Expiring  from Tue Feb 19 14:36:57 2008, 27 MBytes, forced expire (LiveTV recording)
2008-02-19 14:40:30.397 Using runtime prefix = /usr
2008-02-19 14:40:30.471 New DB connection, total: 1
2008-02-19 14:40:30.498 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:40:30.538 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 14:40:30.654 New DB connection, total: 2
2008-02-19 14:40:30.694 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:40:30.740 EITHelper: localtime offset -6:00:00 
2008-02-19 14:40:30.775 New DB connection, total: 3
2008-02-19 14:40:30.807 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:40:30.863 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:40:30.898 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:40:30.938 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:40:30.981 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:40:31.015 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 14:40:31.076 New DB scheduler connection
2008-02-19 14:40:31.107 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:40:32.507 Main::Registering HttpStatus Extension
2008-02-19 14:40:32.538 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 14:40:32.571 Enabled verbose msgs:  important general
2008-02-19 14:40:32.604 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 14:40:32.640 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 14:40:33.148 Reschedule requested for id -1.
2008-02-19 14:40:33.251 Scheduled 1 items in 0.1 = 0.07 match + 0.04 place
2008-02-19 14:40:33.297 Seem to be woken up by USER
2008-02-19 14:41:05.588 MainServer::HandleAnnounce Monitor
2008-02-19 14:41:05.638 adding: banana as a client (events: 0)
2008-02-19 14:41:05.680 MainServer::HandleAnnounce Monitor
2008-02-19 14:41:05.709 adding: banana as a client (events: 1)
2008-02-19 14:41:05.751 MainServer::HandleAnnounce Playback
2008-02-19 14:41:05.779 adding: banana as a client (events: 0)
2008-02-19 14:41:05.824 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:41:05.852 TVRec(1): HW Tuner: 1->1
2008-02-19 14:41:05.896 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:41:05.925 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:41:05.967 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:41:06.068 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:41:06 2008) endts(Tue Feb 19 14:41:06 2008)
             recstartts(Tue Feb 19 14:41:06 2008) recendts(Tue Feb 19 14:41:06 2008)
             title()
2008-02-19 14:41:06.247 Unknown video codec
2008-02-19 14:41:06.291 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:41:06.325 setup the four 'Software Encoders' profiles.
2008-02-19 14:41:06.366 Assuming RTjpeg for now.
2008-02-19 14:41:06.400 NVR: Error, unknown audio codec
2008-02-19 14:41:06.475 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:41:06.480 MainServer::HandleAnnounce Playback
2008-02-19 14:41:06.561 adding: banana as a client (events: 0)
2008-02-19 14:41:06.679 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:41:06.741 adding: banana as a remote file transfer
2008-02-19 14:41:09.631 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:41:09.657 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:41:09.699 TVRec(1) Error: Failed to set channel to 13.
2008-02-19 14:41:09.748 Finished recording : channel 4294967295
2008-02-19 14:41:09.788 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:41:09 2008) endts(Tue Feb 19 14:41:09 2008)
             recstartts(Tue Feb 19 14:41:09 2008) recendts(Tue Feb 19 14:41:09 2008)
             title()
2008-02-19 14:41:09.920 Finished recording : channel 4294967295
2008-02-19 14:41:10.209 TVRec(1): RingBufferChanged()
2008-02-19 14:41:10.292 Finished recording : channel 4294967295
2008-02-19 14:41:10.478 MainServer::HandleAnnounce Playback
2008-02-19 14:41:10.523 adding: banana as a client (events: 0)
2008-02-19 14:41:10.558 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:41:10.648 adding: banana as a remote file transfer
2008-02-19 14:41:18.807 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:41:18.936 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:41:18.978 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:41:19.048 Finished recording : channel 4294967295
2008-02-19 14:41:19.093 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:41:19 2008) endts(Tue Feb 19 14:41:19 2008)
             recstartts(Tue Feb 19 14:41:19 2008) recendts(Tue Feb 19 14:41:19 2008)
             title()
2008-02-19 14:41:19.201 Finished recording : channel 4294967295
2008-02-19 14:41:19.323 TVRec(1): RingBufferChanged()
2008-02-19 14:41:19.404 Finished recording : channel 4294967295
2008-02-19 14:41:19.593 MainServer::HandleAnnounce Playback
2008-02-19 14:41:19.627 adding: banana as a client (events: 0)
2008-02-19 14:41:19.720 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:41:19.752 adding: banana as a remote file transfer
2008-02-19 14:41:26.716 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:41:26.884 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:41:26.926 TVRec(1) Error: Failed to set channel to 28.
2008-02-19 14:41:27.094 Finished recording : channel 4294967295
2008-02-19 14:41:27.277 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:41:27 2008) endts(Tue Feb 19 14:41:27 2008)
             recstartts(Tue Feb 19 14:41:27 2008) recendts(Tue Feb 19 14:41:27 2008)
             title()
2008-02-19 14:41:27.430 Finished recording : channel 4294967295
2008-02-19 14:41:27.477 TVRec(1): RingBufferChanged()
2008-02-19 14:41:27.593 Finished recording : channel 4294967295
2008-02-19 14:41:27.791 MainServer::HandleAnnounce Playback
2008-02-19 14:41:27.858 adding: banana as a client (events: 0)
2008-02-19 14:41:27.904 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:41:27.942 adding: banana as a remote file transfer
2008-02-19 14:41:32.401 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:41:32.913 Finished recording : channel 4294967295
2008-02-19 14:42:51.171 Expiring  from Tue Feb 19 14:41:06 2008, 8 MBytes, forced expire (LiveTV recording)
2008-02-19 14:42:51.203 Expiring  from Tue Feb 19 14:41:09 2008, 23 MBytes, forced expire (LiveTV recording)
2008-02-19 14:42:51.232 Expiring  from Tue Feb 19 14:41:19 2008, 19 MBytes, forced expire (LiveTV recording)
2008-02-19 14:45:45.605 Using runtime prefix = /usr
2008-02-19 14:45:45.838 New DB connection, total: 1
2008-02-19 14:45:45.903 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:45:46.028 Current Schema Version: 1160
Starting up as the master server.
2008-02-19 14:45:46.288 New DB connection, total: 2
2008-02-19 14:45:46.339 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:45:46.414 EITHelper: localtime offset -6:00:00 
2008-02-19 14:45:46.586 New DB connection, total: 3
2008-02-19 14:45:46.638 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:45:46.794 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:45:46.829 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:45:46.884 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:45:46.945 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:45:47.020 TVRec(1) Error: Setting start channel '18' failed, 
			and backup '8' failed as well.
2008-02-19 14:45:47.123 New DB scheduler connection
2008-02-19 14:45:47.171 Connected to database 'mythconverg' at host: localhost
2008-02-19 14:45:48.569 Main::Registering HttpStatus Extension
2008-02-19 14:45:48.593 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-02-19 14:45:48.628 Enabled verbose msgs:  important general
2008-02-19 14:45:48.684 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-02-19 14:45:48.720 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-02-19 14:45:49.229 Reschedule requested for id -1.
2008-02-19 14:45:49.338 Scheduled 1 items in 0.1 = 0.06 match + 0.04 place
2008-02-19 14:45:49.380 Seem to be woken up by USER
2008-02-19 14:46:07.223 Expiring  from Tue Feb 19 14:41:27 2008, 14 MBytes, forced expire (LiveTV recording)
2008-02-19 14:47:11.066 MainServer::HandleAnnounce Monitor
2008-02-19 14:47:11.121 adding: banana as a client (events: 0)
2008-02-19 14:47:11.156 MainServer::HandleAnnounce Monitor
2008-02-19 14:47:11.188 adding: banana as a client (events: 1)
2008-02-19 14:47:11.228 MainServer::HandleAnnounce Playback
2008-02-19 14:47:11.246 adding: banana as a client (events: 0)
2008-02-19 14:47:11.310 TVRec(1): Changing from None to WatchingLiveTV
2008-02-19 14:47:11.356 TVRec(1): HW Tuner: 1->1
2008-02-19 14:47:11.392 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:47:11.429 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:47:11.463 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:47:11.590 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:47:11 2008) endts(Tue Feb 19 14:47:11 2008)
             recstartts(Tue Feb 19 14:47:11 2008) recendts(Tue Feb 19 14:47:11 2008)
             title()
2008-02-19 14:47:11.873 Unknown video codec
2008-02-19 14:47:11.912 Please go into the TV Settings, Recording Profiles and
2008-02-19 14:47:11.945 setup the four 'Software Encoders' profiles.
2008-02-19 14:47:11.979 Assuming RTjpeg for now.
2008-02-19 14:47:12.004 NVR: Error, unknown audio codec
2008-02-19 14:47:12.055 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
2008-02-19 14:47:12.074 MainServer::HandleAnnounce Playback
2008-02-19 14:47:12.162 adding: banana as a client (events: 0)
2008-02-19 14:47:12.196 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:47:12.262 adding: banana as a remote file transfer
2008-02-19 14:47:17.037 Channel::GetCurrentChannelNum(): Failed to find Channel ''
2008-02-19 14:47:17.072 Channel(/dev/video0)::TuneTo(): Error, failed to find channel.
2008-02-19 14:47:17.105 TVRec(1) Error: Failed to set channel to 18.
2008-02-19 14:47:17.145 Finished recording : channel 4294967295
2008-02-19 14:47:17.185 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Feb 19 14:47:17 2008) endts(Tue Feb 19 14:47:17 2008)
             recstartts(Tue Feb 19 14:47:17 2008) recendts(Tue Feb 19 14:47:17 2008)
             title()
2008-02-19 14:47:17.306 Finished recording : channel 4294967295
2008-02-19 14:47:17.482 TVRec(1): RingBufferChanged()
2008-02-19 14:47:17.590 Finished recording : channel 4294967295
2008-02-19 14:47:17.799 MainServer::HandleAnnounce Playback
2008-02-19 14:47:17.871 adding: banana as a client (events: 0)
2008-02-19 14:47:18.022 MainServer::HandleAnnounce FileTransfer
2008-02-19 14:47:18.087 adding: banana as a remote file transfer
2008-02-19 14:47:20.565 TVRec(1): Changing from WatchingLiveTV to None
2008-02-19 14:47:21.005 Finished recording : channel 4294967295
2008-02-19 14:48:07.296 Expiring  from Tue Feb 19 14:47:11 2008, 1 MBytes, forced expire (LiveTV recording)
2008-02-19 14:48:07.354 Expiring  from Tue Feb 19 14:47:17 2008, 0 MBytes, forced expire (LiveTV recording)

```

---

### Post by maybeway36 on 2008-02-20
Bump.

---

