---
title: "lots of frontend/backend.log errors.  help requested"
date: 2008-07-17
forum: Mythbuntu
---

### Post by azmanam on 2008-07-17
**
Gateway box
P4 3GHz processor
1 GB RAM
one 40 GB Western Digital IDE Hard drive
one 500 GB Western Digital IDE Hard drive
NVidia-GeForce FX 5200 DDR 128MB Video Card
Hauppauge HVR-1600 Tuner Card (with accompanying remote of unknown model #)
Creative Sound Blaster X-Fi Card
kernel 2.6.24-19-generic
**
 
I spent a while getting my Hauppauge card recognized, but it appears to be installed.  When I attempt to configure the capture card, the Hauppauge card comes up in the various details.
 
When I attempt to watch tv, the screen goes black with no writing or picture or anything.  Pressing all buttons does nothing, and hitting escape does nothing for almost 30 seconds before I see the frontend screen again.
 
My capture card list includes:
   Cardtype: analog V4L capture card
   video device: /dev/video0
   Probed info: Hauppauge HVR-1600 [cx18]
   VBI Device:
   Audio device: /dev/dsp
   Audio sampling rate limit: (none)
   Default input: Tuner 1
and
   Card type: MPEG-2 encoder card (PVR-x50, PVR-500)
   Video device: /dev/video0
   Probed Info: Hauppauge HVR-1600 [cx18]
   Default Input: Tuner 1
 
Input connections includes 5 options for each Capture card: Tuner 1, S-Video 1, Composite 1, S-Video 2, Composite 2)
**Interestingly, attempting to scan for channels within ALL 10 input connections menu causes the Backend setup to CRASH and exit to the desktop while prompting me to run mythfilldatabase.

I tried independently opening mplayer (terminal -> mplayer /dev/video0) and that shows a screen filled with static.  ONCE, very briefly, it showed some sort of picture.  Looked like live tv, but if it was, it was that local public information station that just loops static text screens, no people moving.  So i don't know if it was actually live tv or not.  I clicked the mouse, and the screen went to static and never came back.

One forum ([http://ubuntuforums.org/showthread.php?t=813429](http://ubuntuforums.org/showthread.php?t=813429), see reply #67) suggested using me-tv.  I tried installing that, but I can't lock on any signals.  When I try to open me-tv, I get a 'no channels in channel.conf file.  Same with xine.

VLC looks like an audio player.  I see pause, play, etc.  But it's only as tall as the menu buttons, and has no visible room to display any video.

Here are the logs:

backend.log (sorry that it's so long...

```
2008-07-17 18:42:21.675 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 18:42:21.834 Empty LocalHostName.
2008-07-17 18:42:22.017 Using localhost value of adam-desktop
2008-07-17 18:42:22.457 New DB connection, total: 1
2008-07-17 18:42:22.590 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:42:22.779 Closing DB connection named 'DBManager0'
2008-07-17 18:42:22.920 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:42:23.226 New DB connection, total: 2
2008-07-17 18:42:23.573 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:42:24.021 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 18:42:24.392 New DB connection, total: 3
2008-07-17 18:42:24.553 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:42:25.288 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 18:42:25.425 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 18:42:25.513 New DB scheduler connection
2008-07-17 18:42:25.569 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:42:25.669 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 18:42:25.719 Main::Registering HttpStatus Extension
2008-07-17 18:42:25.769 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 18:42:25.819 Enabled verbose msgs:  important general
2008-07-17 18:42:25.915 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 18:42:28.636 Reschedule requested for id -1.
2008-07-17 18:42:29.947 Scheduled 0 items in 1.3 = 1.01 match + 0.29 place
2008-07-17 18:42:30.018 Seem to be woken up by USER
2008-07-17 18:43:29.722 MainServer::HandleAnnounce Monitor
2008-07-17 18:43:29.804 adding: adam-desktop as a client (events: 0)
2008-07-17 18:43:29.856 MainServer::HandleAnnounce Monitor
2008-07-17 18:43:29.905 adding: adam-desktop as a client (events: 1)
2008-07-17 18:43:29.961 MainServer::HandleAnnounce Playback
2008-07-17 18:43:30.022 adding: adam-desktop as a client (events: 0)
2008-07-17 18:43:30.099 TVRec(5): Changing from None to WatchingLiveTV
2008-07-17 18:43:30.145 TVRec(5): HW Tuner: 5->5
2008-07-17 18:43:30.663 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 18:43:30.714 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 18:43:30.764 TVRec(5) Error: Failed to set channel to 0.
2008-07-17 18:43:30.976 TVRec(5) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Thu Jul 17 18:43:30 2008) endts(Thu Jul 17 18:43:30 2008)
             recstartts(Thu Jul 17 18:43:30 2008) recendts(Thu Jul 17 18:43:30 2008)
             title()
2008-07-17 18:43:31.034 New DB connection, total: 4
2008-07-17 18:43:31.082 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:43:32.268 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four$
2008-07-17 18:43:32.406 NVR(/dev/video0) Error: Unknown audio codec
2008-07-17 18:43:32.463 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-17 18:43:32.470 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGCHAN: Invalid argument
VIDIOCGMBUF:: Invalid argument
2008-07-17 18:43:44.876 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-17 18:44:12.503 TVRec(5): Changing from WatchingLiveTV to None
2008-07-17 18:44:12.570 Finished recording : channel 4294967295
2008-07-17 18:46:44.941 Expiring 0 MBytes for 4294967295 @ Thu Jul 17 18:43:30 2008 =>
2008-07-17 18:58:45.002 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:19:55.513 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 19:19:55.553 Empty LocalHostName.
2008-07-17 19:19:55.612 Using localhost value of adam-desktop
2008-07-17 19:19:55.675 New DB connection, total: 1
2008-07-17 19:19:55.734 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:19:55.790 Closing DB connection named 'DBManager0'
2008-07-17 19:19:55.840 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:19:55.891 New DB connection, total: 2
2008-07-17 19:19:55.940 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:19:55.984 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 19:19:56.092 New DB connection, total: 3
2008-07-17 19:19:56.141 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:19:56.659 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:19:56.690 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:19:56.935 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-17 19:19:56.982 DVBChan(6:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-17 19:19:57.041 New DB scheduler connection
2008-07-17 19:19:57.091 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:19:57.162 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 19:19:57.207 Main::Registering HttpStatus Extension
2008-07-17 19:19:57.258 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:19:57.308 Enabled verbose msgs:  important general
2008-07-17 19:19:57.360 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:20:00.145 Reschedule requested for id -1.
2008-07-17 19:20:00.221 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 19:20:00.285 Seem to be woken up by USER
2008-07-17 19:20:09.862 MainServer::HandleAnnounce Monitor
2008-07-17 19:20:09.918 adding: adam-desktop as a client (events: 0)
2008-07-17 19:20:09.968 MainServer::HandleAnnounce Monitor
2008-07-17 19:20:10.018 adding: adam-desktop as a client (events: 1)
2008-07-17 19:20:12.978 MainServer::HandleAnnounce Playback
2008-07-17 19:20:13.021 adding: adam-desktop as a client (events: 0)
2008-07-17 19:20:13.073 TVRec(5): Changing from None to WatchingLiveTV
2008-07-17 19:20:13.126 TVRec(5): HW Tuner: 5->5
2008-07-17 19:20:13.654 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:20:13.705 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:20:13.755 TVRec(5) Error: Failed to set channel to 0.
2008-07-17 19:20:13.861 TVRec(5) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Thu Jul 17 19:20:13 2008) endts(Thu Jul 17 19:20:13 2008)
             recstartts(Thu Jul 17 19:20:13 2008) recendts(Thu Jul 17 19:20:13 2008)
             title()
2008-07-17 19:20:13.909 New DB connection, total: 4
2008-07-17 19:20:13.958 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:20:14.992 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four$
2008-07-17 19:20:15.124 NVR(/dev/video0) Error: Unknown audio codec
2008-07-17 19:20:15.187 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-17 19:20:15.193 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGCHAN: Invalid argument
VIDIOCGMBUF:: Invalid argument
2008-07-17 19:20:55.201 TVRec(5): Changing from WatchingLiveTV to None
2008-07-17 19:20:55.264 Finished recording : channel 4294967295
2008-07-17 19:21:17.149 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:23:55.385 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 19:23:55.424 Empty LocalHostName.
2008-07-17 19:23:55.484 Using localhost value of adam-desktop
2008-07-17 19:23:55.545 New DB connection, total: 1
2008-07-17 19:23:55.597 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:23:55.645 Closing DB connection named 'DBManager0'
2008-07-17 19:23:55.694 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:23:55.745 New DB connection, total: 2
2008-07-17 19:23:55.794 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:23:55.847 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 19:23:55.970 New DB connection, total: 3
2008-07-17 19:23:56.012 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:23:56.521 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:23:56.569 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:23:57.010 New DB scheduler connection
2008-07-17 19:23:57.053 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:23:57.125 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 19:23:57.170 Main::Registering HttpStatus Extension
2008-07-17 19:23:57.220 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:23:57.270 Enabled verbose msgs:  important general
2008-07-17 19:23:57.323 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:23:57.539 DBox2Ch(6) Error: Changing to '0' failed. DBox2 channel ID for name 'TV Guide Network' not found!
2008-07-17 19:24:00.107 Reschedule requested for id -1.
2008-07-17 19:24:00.177 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 19:24:00.241 Seem to be woken up by USER
2008-07-17 19:24:10.968 MainServer::HandleAnnounce Monitor
2008-07-17 19:24:11.019 adding: adam-desktop as a client (events: 0)
2008-07-17 19:24:11.070 MainServer::HandleAnnounce Monitor
2008-07-17 19:24:11.119 adding: adam-desktop as a client (events: 1)
2008-07-17 19:24:11.175 MainServer::HandleAnnounce Playback
2008-07-17 19:24:11.228 adding: adam-desktop as a client (events: 0)
2008-07-17 19:24:11.280 TVRec(5): Changing from None to WatchingLiveTV
2008-07-17 19:24:11.333 TVRec(5): HW Tuner: 5->5
2008-07-17 19:24:11.856 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:24:11.903 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:24:11.953 TVRec(5) Error: Failed to set channel to 0.
2008-07-17 19:24:12.046 TVRec(5) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Thu Jul 17 19:24:12 2008) endts(Thu Jul 17 19:24:12 2008)
             recstartts(Thu Jul 17 19:24:12 2008) recendts(Thu Jul 17 19:24:12 2008)
             title()
2008-07-17 19:24:12.098 New DB connection, total: 4
2008-07-17 19:24:12.146 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:24:13.184 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four$
2008-07-17 19:24:13.313 NVR(/dev/video0) Error: Unknown audio codec
2008-07-17 19:24:13.368 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-17 19:24:13.374 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGCHAN: Invalid argument
VIDIOCGMBUF:: Invalid argument
2008-07-17 19:24:17.110 Expiring 0 MBytes for 4294967295 @ Thu Jul 17 19:20:13 2008 =>
2008-07-17 19:24:53.380 TVRec(5): Changing from WatchingLiveTV to None
2008-07-17 19:24:53.433 Finished recording : channel 4294967295
2008-07-17 19:25:17.152 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:26:17.211 Expiring 0 MBytes for 4294967295 @ Thu Jul 17 19:24:12 2008 =>
2008-07-17 19:40:17.273 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:46:15.422 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 19:46:15.479 Empty LocalHostName.
2008-07-17 19:46:15.528 Using localhost value of adam-desktop
2008-07-17 19:46:15.590 New DB connection, total: 1
2008-07-17 19:46:15.641 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:46:15.688 Closing DB connection named 'DBManager0'
2008-07-17 19:46:15.738 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:46:15.789 New DB connection, total: 2
2008-07-17 19:46:15.838 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:46:15.891 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 19:46:15.999 New DB connection, total: 3
2008-07-17 19:46:16.047 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:46:16.562 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:46:16.613 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:46:17.089 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:46:17.138 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:46:17.291 New DB scheduler connection
2008-07-17 19:46:17.339 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:46:17.420 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 19:46:17.465 Main::Registering HttpStatus Extension
2008-07-17 19:46:17.507 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:46:17.549 Enabled verbose msgs:  important general
2008-07-17 19:46:17.593 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:46:20.403 Reschedule requested for id -1.
2008-07-17 19:46:20.671 Scheduled 0 items in 0.3 = 0.10 match + 0.17 place
2008-07-17 19:46:20.735 Seem to be woken up by USER
2008-07-17 19:47:17.623 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 19:47:17.670 Empty LocalHostName.
2008-07-17 19:47:17.721 Using localhost value of adam-desktop
2008-07-17 19:47:17.775 New DB connection, total: 1
2008-07-17 19:47:17.827 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:47:17.874 Closing DB connection named 'DBManager0'
2008-07-17 19:47:17.924 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:47:17.975 New DB connection, total: 2
2008-07-17 19:47:18.024 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:47:18.077 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 19:47:18.191 New DB connection, total: 3
2008-07-17 19:47:18.241 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:47:18.774 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:47:18.824 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:47:20.280 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 19:47:20.331 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 19:47:20.484 New DB scheduler connection
2008-07-17 19:47:20.539 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:47:20.603 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 19:47:20.648 Main::Registering HttpStatus Extension
2008-07-17 19:47:20.732 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:47:20.824 Enabled verbose msgs:  important general
2008-07-17 19:47:20.910 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:48:20.061 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 19:48:20.108 Empty LocalHostName.
2008-07-17 19:48:20.168 Using localhost value of adam-desktop
2008-07-17 19:48:20.230 New DB connection, total: 1
2008-07-17 19:48:20.289 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:48:20.345 Closing DB connection named 'DBManager0'
2008-07-17 19:48:20.395 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:48:20.446 New DB connection, total: 2
2008-07-17 19:48:20.495 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:48:20.539 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 19:48:20.654 New DB connection, total: 3
2008-07-17 19:48:20.696 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:48:21.207 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:48:21.253 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:48:22.568 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 19:48:22.618 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 19:48:22.771 New DB scheduler connection
2008-07-17 19:48:22.819 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:48:22.890 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 19:48:22.935 Main::Registering HttpStatus Extension
2008-07-17 19:48:22.986 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:48:23.036 Enabled verbose msgs:  important general
2008-07-17 19:48:23.088 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:48:25.872 Reschedule requested for id -1.
2008-07-17 19:48:25.942 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 19:48:26.007 Seem to be woken up by USER
2008-07-17 19:50:22.273 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 19:50:22.326 Empty LocalHostName.
2008-07-17 19:50:22.376 Using localhost value of adam-desktop
2008-07-17 19:50:22.438 New DB connection, total: 1
2008-07-17 19:50:22.504 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:50:22.553 Closing DB connection named 'DBManager0'
2008-07-17 19:50:22.594 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:50:22.646 New DB connection, total: 2
2008-07-17 19:50:22.695 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:50:22.739 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 19:50:22.848 New DB connection, total: 3
2008-07-17 19:50:22.897 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:50:23.428 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:50:23.479 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:50:24.822 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 19:50:24.869 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 19:50:25.023 New DB scheduler connection
2008-07-17 19:50:25.070 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:50:25.142 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 19:50:25.195 Main::Registering HttpStatus Extension
2008-07-17 19:50:25.245 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:50:25.295 Enabled verbose msgs:  important general
2008-07-17 19:50:25.348 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:50:28.124 Reschedule requested for id -1.
2008-07-17 19:50:28.200 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 19:50:28.264 Seem to be woken up by USER
2008-07-17 19:51:45.127 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 19:55:45.174 MainServer::HandleAnnounce Monitor
2008-07-17 19:55:45.292 adding: adam-desktop as a client (events: 0)
2008-07-17 19:55:45.343 MainServer::HandleAnnounce Monitor
2008-07-17 19:55:45.393 adding: adam-desktop as a client (events: 1)
2008-07-17 19:55:45.448 MainServer::HandleAnnounce Playback
2008-07-17 19:55:45.502 adding: adam-desktop as a client (events: 0)
2008-07-17 19:55:45.554 TVRec(5): Changing from None to WatchingLiveTV
2008-07-17 19:55:45.608 TVRec(5): HW Tuner: 5->5
2008-07-17 19:55:46.144 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 19:55:46.195 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 19:55:46.245 TVRec(5) Error: Failed to set channel to 0.
2008-07-17 19:55:46.333 TVRec(5) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Thu Jul 17 19:55:46 2008) endts(Thu Jul 17 19:55:46 2008)
             recstartts(Thu Jul 17 19:55:46 2008) recendts(Thu Jul 17 19:55:46 2008)
             title()
2008-07-17 19:55:46.390 New DB connection, total: 4
2008-07-17 19:55:46.447 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:55:47.472 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four$
2008-07-17 19:55:47.612 NVR(/dev/video0) Error: Unknown audio codec
2008-07-17 19:55:47.668 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-07-17 19:55:47.677 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGCHAN: Invalid argument
VIDIOCGMBUF:: Invalid argument
2008-07-17 19:56:27.681 TVRec(5): Changing from WatchingLiveTV to None
2008-07-17 19:56:27.772 Finished recording : channel 4294967295
2008-07-17 19:57:13.975 MainServer::HandleAnnounce Monitor
2008-07-17 19:57:14.116 adding: adam-desktop as a client (events: 0)
2008-07-17 19:57:14.167 MainServer::HandleAnnounce Monitor
2008-07-17 19:57:14.216 adding: adam-desktop as a client (events: 1)
2008-07-17 19:58:45.205 Expiring 0 MBytes for 4294967295 @ Thu Jul 17 19:55:46 2008 =>
2008-07-17 20:06:45.264 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:14:20.430 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:14:20.473 Empty LocalHostName.
2008-07-17 20:14:20.532 Using localhost value of adam-desktop
2008-07-17 20:14:20.593 New DB connection, total: 1
2008-07-17 20:14:20.645 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:20.692 Closing DB connection named 'DBManager0'
2008-07-17 20:14:20.742 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:20.793 New DB connection, total: 2
2008-07-17 20:14:20.842 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:20.895 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:14:21.012 New DB connection, total: 3
2008-07-17 20:14:21.061 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:21.601 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:14:21.643 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:14:23.052 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:14:23.100 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:14:23.245 New DB scheduler connection
2008-07-17 20:14:23.292 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:23.363 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:14:23.408 Main::Registering HttpStatus Extension
2008-07-17 20:14:23.459 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:14:23.509 Enabled verbose msgs:  important general
2008-07-17 20:14:23.562 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:14:35.909 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:14:35.963 Empty LocalHostName.
2008-07-17 20:14:36.022 Using localhost value of adam-desktop
2008-07-17 20:14:36.083 New DB connection, total: 1
2008-07-17 20:14:36.142 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:36.190 Closing DB connection named 'DBManager0'
2008-07-17 20:14:36.240 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:36.291 New DB connection, total: 2
2008-07-17 20:14:36.340 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:36.393 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:14:36.508 New DB connection, total: 3
2008-07-17 20:14:36.559 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:37.109 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:14:37.158 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:14:38.497 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:14:38.548 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:14:38.702 New DB scheduler connection
2008-07-17 20:14:38.749 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:14:38.820 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:14:38.874 Main::Registering HttpStatus Extension
2008-07-17 20:14:38.924 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:14:38.974 Enabled verbose msgs:  important general
2008-07-17 20:14:39.028 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:14:41.802 Reschedule requested for id -1.
2008-07-17 20:14:41.871 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 20:14:41.935 Seem to be woken up by USER
2008-07-17 20:15:02.380 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:15:02.425 Empty LocalHostName.
2008-07-17 20:15:02.476 Using localhost value of adam-desktop
2008-07-17 20:15:02.537 New DB connection, total: 1
2008-07-17 20:15:02.588 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:02.636 Closing DB connection named 'DBManager0'
2008-07-17 20:15:02.685 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:02.737 New DB connection, total: 2
2008-07-17 20:15:02.785 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:02.838 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:15:02.953 New DB connection, total: 3
2008-07-17 20:15:03.003 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:03.539 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:15:03.587 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:15:04.959 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:15:05.002 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:15:05.147 New DB scheduler connection
2008-07-17 20:15:05.194 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:05.257 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:15:05.302 Main::Registering HttpStatus Extension
2008-07-17 20:15:05.378 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:15:05.428 Enabled verbose msgs:  important general
2008-07-17 20:15:05.480 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:15:08.239 Reschedule requested for id -1.
2008-07-17 20:15:08.508 Scheduled 0 items in 0.3 = 0.24 match + 0.03 place
2008-07-17 20:15:08.653 Seem to be woken up by USER
2008-07-17 20:15:49.235 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:15:49.345 Empty LocalHostName.
2008-07-17 20:15:49.404 Using localhost value of adam-desktop
2008-07-17 20:15:49.456 New DB connection, total: 1
2008-07-17 20:15:49.508 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:49.556 Closing DB connection named 'DBManager0'
2008-07-17 20:15:49.605 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:49.656 New DB connection, total: 2
2008-07-17 20:15:49.705 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:49.758 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:15:49.865 New DB connection, total: 3
2008-07-17 20:15:49.915 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:50.483 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:15:50.531 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:15:51.869 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:15:51.921 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:15:52.076 New DB scheduler connection
2008-07-17 20:15:52.131 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:15:52.203 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:15:52.248 Main::Registering HttpStatus Extension
2008-07-17 20:15:52.290 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:15:52.331 Enabled verbose msgs:  important general
2008-07-17 20:15:52.376 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:15:55.185 Reschedule requested for id -1.
2008-07-17 20:15:55.253 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 20:15:55.308 Seem to be woken up by USER
2008-07-17 20:16:12.641 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:16:12.689 Empty LocalHostName.
2008-07-17 20:16:12.748 Using localhost value of adam-desktop
2008-07-17 20:16:12.810 New DB connection, total: 1
2008-07-17 20:16:12.861 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:12.917 Closing DB connection named 'DBManager0'
2008-07-17 20:16:12.966 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:13.018 New DB connection, total: 2
2008-07-17 20:16:13.066 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:13.119 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:16:13.242 New DB connection, total: 3
2008-07-17 20:16:13.292 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:13.806 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:16:13.851 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:16:15.212 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:16:15.266 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:16:15.420 New DB scheduler connection
2008-07-17 20:16:15.608 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:15.681 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:16:15.725 Main::Registering HttpStatus Extension
2008-07-17 20:16:15.775 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:16:15.825 Enabled verbose msgs:  important general
2008-07-17 20:16:15.878 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:16:18.662 Reschedule requested for id -1.
2008-07-17 20:16:18.747 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2008-07-17 20:16:18.811 Seem to be woken up by USER
2008-07-17 20:16:31.966 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:16:32.014 Empty LocalHostName.
2008-07-17 20:16:32.073 Using localhost value of adam-desktop
2008-07-17 20:16:32.135 New DB connection, total: 1
2008-07-17 20:16:32.200 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:32.242 Closing DB connection named 'DBManager0'
2008-07-17 20:16:32.283 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:32.326 New DB connection, total: 2
2008-07-17 20:16:32.375 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:32.419 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:16:32.526 New DB connection, total: 3
2008-07-17 20:16:32.576 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:33.115 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:16:33.167 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:16:35.417 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:16:35.649 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:16:35.815 New DB scheduler connection
2008-07-17 20:16:35.901 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:16:35.964 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:16:36.009 Main::Registering HttpStatus Extension
2008-07-17 20:16:36.152 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:16:36.202 Enabled verbose msgs:  important general
2008-07-17 20:16:36.255 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:16:38.946 Reschedule requested for id -1.
2008-07-17 20:16:39.401 Scheduled 0 items in 0.5 = 0.23 match + 0.23 place
2008-07-17 20:16:39.624 Seem to be woken up by USER
2008-07-17 20:17:12.463 MainServer::HandleAnnounce Monitor
2008-07-17 20:17:16.796 adding: adam-desktop as a client (events: 0)
2008-07-17 20:17:16.847 MainServer::HandleAnnounce Monitor
2008-07-17 20:17:16.897 adding: adam-desktop as a client (events: 1)
2008-07-17 20:17:16.949 Reschedule requested for id -1.
2008-07-17 20:17:17.028 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 20:17:45.130 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:17:45.174 Empty LocalHostName.
2008-07-17 20:17:45.225 Using localhost value of adam-desktop
2008-07-17 20:17:45.286 New DB connection, total: 1
2008-07-17 20:17:45.337 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:17:45.385 Closing DB connection named 'DBManager0'
2008-07-17 20:17:45.435 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:17:45.486 New DB connection, total: 2
2008-07-17 20:17:45.535 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:17:45.588 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:17:45.702 New DB connection, total: 3
2008-07-17 20:17:45.752 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:17:46.281 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:17:46.335 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:17:47.690 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:17:47.741 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:17:47.895 New DB scheduler connection
2008-07-17 20:17:47.950 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:17:48.022 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:17:48.075 Main::Registering HttpStatus Extension
2008-07-17 20:17:48.117 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:17:48.160 Enabled verbose msgs:  important general
2008-07-17 20:17:48.213 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:17:51.004 Reschedule requested for id -1.
2008-07-17 20:17:51.083 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2008-07-17 20:17:51.146 Seem to be woken up by USER
2008-07-17 20:18:37.285 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:18:37.350 Empty LocalHostName.
2008-07-17 20:18:37.409 Using localhost value of adam-desktop
2008-07-17 20:18:37.461 New DB connection, total: 1
2008-07-17 20:18:37.519 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:37.560 Closing DB connection named 'DBManager0'
2008-07-17 20:18:37.610 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:37.653 New DB connection, total: 2
2008-07-17 20:18:37.702 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:37.755 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:18:37.862 New DB connection, total: 3
2008-07-17 20:18:37.911 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:38.459 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:18:38.519 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:18:39.882 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:18:39.934 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:18:40.088 New DB scheduler connection
2008-07-17 20:18:40.136 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:40.209 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:18:40.261 Main::Registering HttpStatus Extension
2008-07-17 20:18:40.311 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:18:40.361 Enabled verbose msgs:  important general
2008-07-17 20:18:40.414 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:18:43.190 Reschedule requested for id -1.
2008-07-17 20:18:43.275 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2008-07-17 20:18:43.338 Seem to be woken up by USER
2008-07-17 20:18:57.954 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:18:57.998 Empty LocalHostName.
2008-07-17 20:18:58.048 Using localhost value of adam-desktop
2008-07-17 20:18:58.110 New DB connection, total: 1
2008-07-17 20:18:58.161 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:58.210 Closing DB connection named 'DBManager0'
2008-07-17 20:18:58.258 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:58.309 New DB connection, total: 2
2008-07-17 20:18:58.358 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:58.411 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:18:58.518 New DB connection, total: 3
2008-07-17 20:18:58.567 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:18:59.123 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:18:59.175 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:19:00.566 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:19:00.606 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:19:00.760 New DB scheduler connection
2008-07-17 20:19:00.815 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:00.889 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:19:00.933 Main::Registering HttpStatus Extension
2008-07-17 20:19:00.975 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:19:01.017 Enabled verbose msgs:  important general
2008-07-17 20:19:01.061 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:19:03.870 Reschedule requested for id -1.
2008-07-17 20:19:03.948 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 20:19:04.011 Seem to be woken up by USER
2008-07-17 20:19:18.633 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:19:18.680 Empty LocalHostName.
2008-07-17 20:19:18.739 Using localhost value of adam-desktop
2008-07-17 20:19:18.801 New DB connection, total: 1
2008-07-17 20:19:18.852 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:18.907 Closing DB connection named 'DBManager0'
2008-07-17 20:19:18.957 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:19.008 New DB connection, total: 2
2008-07-17 20:19:19.057 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:19.110 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:19:19.225 New DB connection, total: 3
2008-07-17 20:19:19.266 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:19.808 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:19:19.849 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:19:21.233 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:19:21.280 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:19:21.427 New DB scheduler connection
2008-07-17 20:19:21.474 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:21.546 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:19:21.591 Main::Registering HttpStatus Extension
2008-07-17 20:19:21.641 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:19:21.691 Enabled verbose msgs:  important general
2008-07-17 20:19:21.744 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:19:24.528 Reschedule requested for id -1.
2008-07-17 20:19:41.472 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-17 20:19:41.515 Empty LocalHostName.
2008-07-17 20:19:41.574 Using localhost value of adam-desktop
2008-07-17 20:19:41.628 New DB connection, total: 1
2008-07-17 20:19:41.679 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:41.726 Closing DB connection named 'DBManager0'
2008-07-17 20:19:41.776 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:41.819 New DB connection, total: 2
2008-07-17 20:19:41.867 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:41.920 Current Schema Version: 1214
Starting up as the master server.
2008-07-17 20:19:42.027 New DB connection, total: 3
2008-07-17 20:19:42.077 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:42.602 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2008-07-17 20:19:42.651 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2008-07-17 20:19:44.009 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2008-07-17 20:19:44.057 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2008-07-17 20:19:44.221 New DB scheduler connection
2008-07-17 20:19:44.268 Connected to database 'mythconverg' at host: localhost
2008-07-17 20:19:44.340 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-17 20:19:44.393 Main::Registering HttpStatus Extension
2008-07-17 20:19:44.443 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 20:19:44.493 Enabled verbose msgs:  important general
2008-07-17 20:19:44.546 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-17 20:19:47.322 Reschedule requested for id -1.
2008-07-17 20:19:47.390 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-17 20:19:47.445 Seem to be woken up by USER
2008-07-17 20:21:04.325 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

frontend.log

```
2008-07-17 18:42:43.538 New DB connection, total: 2
2008-07-17 18:42:43.539 Connected to database 'mythconverg' at host: localhost
2008-07-17 18:42:43.543 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 18:42:43.543 Enabled verbose msgs:  important general
2008-07-17 18:42:44.378 Unable to parse themeinfo.xml for glass-wide
2008-07-17 18:42:44.378 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-17 18:42:45.385 Unable to parse themeinfo.xml for glass-wide
2008-07-17 18:42:45.385 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-17 18:42:47.594 Primary screen 0.
2008-07-17 18:42:47.595 Using screen 0, 1360x768 at 0,0
2008-07-17 18:42:47.597 Switching to square mode (Mythbuntu-8.04)
2008-07-17 18:42:48.658 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-17 18:42:48.658 lirc_init failed for mythtv, see preceding messages
2008-07-17 18:42:48.658 JoystickMenuClient Error: Joystick disabled - Failed to read /home/adam/.mythtv/joystickmenurc
2008-07-17 18:42:50.821 Specified base font 'medium' does not exist for font clock
2008-07-17 18:42:50.821 Specified base font 'medium' does not exist for font small
2008-07-17 18:42:50.821 Specified base font 'medium' does not exist for font medium
2008-07-17 18:42:50.821 Specified base font 'medium' does not exist for font large
2008-07-17 18:42:50.823 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-17 18:42:50.948 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-17 18:42:51.103 Registering Internal as a media playback plugin.
2008-07-17 18:42:51.395 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-07-17 18:42:52.013 Failed to run 'cdrecord --scanbus'
2008-07-17 18:42:52.016 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-07-17 18:42:52.020 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-07-17 18:42:52.083 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.15.103:5060 NAT address 192.168.15.103
SIP: Cannot register; proxy, username or password not set
2008-07-17 18:43:29.720 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 18:43:29.721 Using protocol version 40
2008-07-17 18:43:29.959 TV: Attempting to change from None to WatchingLiveTV
2008-07-17 18:43:29.960 Using protocol version 40
2008-07-17 18:43:32.485 DPMS Deactivated
2008-07-17 18:44:12.473 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-07-17 18:44:12.473 TV Error: LiveTV not successfully started
2008-07-17 18:44:12.532 TV: Deleting TV Chain in destructor
2008-07-17 18:44:12.534 DPMS Reactivated.

(gksudo:5753): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5753): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:5753): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
^MReading package lists... 0%^M^MReading package lists... 100%^M^MReading package lists... Done
^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 50%^M^MBuilding dependency tree... $
^MReading state information... 0%^M^MReading state information... 0%^M^MReading state information... Done

(zenity:5812): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
to locate theme engine in module_path: "pixmap",

(zenity:5812): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:5812): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:5813): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:5813): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(gksu:5813): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 * Stopping MythTV server: mythbackend
2008-07-17 19:09:55.972 Event socket closed. No connection to the backend.
   ...done.

(gksu:6014): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:6014): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:6014): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
   ...done.

(zenity:6032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:6032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:6032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
2008-07-17 19:20:09.854 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 19:20:09.862 Using protocol version 40
2008-07-17 19:20:12.977 TV: Attempting to change from None to WatchingLiveTV
2008-07-17 19:20:12.977 Using protocol version 40
2008-07-17 19:20:15.282 DPMS Deactivated
2008-07-17 19:20:55.195 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-07-17 19:20:55.196 TV Error: LiveTV not successfully started
2008-07-17 19:20:55.243 TV: Deleting TV Chain in destructor
   ...done.

(zenity:6032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:6032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:6032): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
2008-07-17 19:20:09.854 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 19:20:09.862 Using protocol version 40
2008-07-17 19:20:12.977 TV: Attempting to change from None to WatchingLiveTV
2008-07-17 19:20:12.977 Using protocol version 40
2008-07-17 19:20:15.282 DPMS Deactivated
2008-07-17 19:20:55.195 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-07-17 19:20:55.196 TV Error: LiveTV not successfully started
2008-07-17 19:20:55.243 TV: Deleting TV Chain in destructor
2008-07-17 19:20:55.245 DPMS Reactivated.

(gksudo:6069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6069): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
^MReading package lists... 0%^M^MReading package lists... 100%^M^MReading package lists... Done
^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 50%^M^MBuilding dependency tree... $
^MReading state information... 0%^M^MReading state information... 0%^M^MReading state information... Done
 * Stopping MythTV server: mythbackend
2008-07-17 19:21:48.111 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
   ...done.
2008-07-17 19:24:10.966 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 19:24:10.968 Using protocol version 40
2008-07-17 19:24:11.173 TV: Attempting to change from None to WatchingLiveTV
2008-07-17 19:24:11.175 Using protocol version 40
2008-07-17 19:24:13.378 DPMS Deactivated
2008-07-17 19:24:53.374 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-07-17 19:24:53.374 TV Error: LiveTV not successfully started
2008-07-17 19:24:53.440 TV: Deleting TV Chain in destructor
2008-07-17 19:24:53.441 DPMS Reactivated.

(gksudo:6226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
^MReading package lists... 0%^M^MReading package lists... 100%^M^MReading package lists... Done
^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 50%^M^MBuilding dependency tree... $
^MReading state information... 0%^M^MReading state information... 0%^M^MReading state information... Done
 * Stopping MythTV server: mythbackend
2008-07-17 19:45:22.725 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend
   ...done.
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend
   ...done.
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend
   ...done.
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.
   ...done.
Starting mythfrontend.real..
2008-07-17 19:55:40.206 New DB connection, total: 2
2008-07-17 19:55:40.207 Connected to database 'mythconverg' at host: localhost
2008-07-17 19:55:40.209 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-17 19:55:40.209 Enabled verbose msgs:  important general
2008-07-17 19:55:40.328 Unable to parse themeinfo.xml for glass-wide
2008-07-17 19:55:40.328 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-17 19:55:40.515 Unable to parse themeinfo.xml for glass-wide
2008-07-17 19:55:40.515 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-17 19:55:40.812 Primary screen 0.
2008-07-17 19:55:40.812 Using screen 0, 1360x768 at 0,0
2008-07-17 19:55:40.815 Switching to square mode (Mythbuntu-8.04)
2008-07-17 19:55:40.834 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-17 19:55:40.835 lirc_init failed for mythtv, see preceding messages
2008-07-17 19:55:40.835 JoystickMenuClient Error: Joystick disabled - Failed to read /home/adam/.mythtv/joystickmenurc
2008-07-17 19:55:42.235 Specified base font 'medium' does not exist for font clock
2008-07-17 19:55:42.236 Specified base font 'medium' does not exist for font small
2008-07-17 19:55:42.236 Specified base font 'medium' does not exist for font medium
2008-07-17 19:55:42.236 Specified base font 'medium' does not exist for font large
2008-07-17 19:55:42.238 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-17 19:55:42.340 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-17 19:55:42.418 Registering Internal as a media playback plugin.
2008-07-17 19:55:42.538 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-07-17 19:55:42.603 Failed to run 'cdrecord --scanbus'
2008-07-17 19:55:42.606 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-07-17 19:55:42.609 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-07-17 19:55:42.661 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to bind for SIP connection 192.168.15.103
SIP listening on IP Address :5060 NAT address
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object
2008-07-17 19:55:45.172 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 19:55:45.173 Using protocol version 40
2008-07-17 19:55:45.447 TV: Attempting to change from None to WatchingLiveTV
2008-07-17 19:55:45.448 Using protocol version 40
2008-07-17 19:55:47.674 DPMS Deactivated
2008-07-17 19:56:27.675 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-07-17 19:56:27.675 TV Error: LiveTV not successfully started
2008-07-17 19:56:27.723 TV: Deleting TV Chain in destructor
2008-07-17 19:56:27.725 DPMS Reactivated.

(gksudo:6736): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6736): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6736): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
^MReading package lists... 0%^M^MReading package lists... 100%^M^MReading package lists... Done
^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 0%^M^MBuilding dependency tree... 50%^M^MBuilding dependency tree... $
^MReading state information... 0%^M^MReading state information... 0%^M^MReading state information... Done
2008-07-17 19:57:04.341 Deleting UPnP client...
2008-07-17 19:57:13.974 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-17 19:57:13.974 Using protocol version 40
Destroying SipFsm object
2008-07-17 19:57:18.400 Deleting UPnP client...
```

None of that really means anything to me.  So if it means anything to you, I'd be most appreciative if you could help me sort it out:)

---

### Post by superm1 on 2008-07-17
My guess would be you are missing the firmware for your cx18.  Need to see dmesg to know for sure.

---

### Post by azmanam on 2008-07-17
```
adam@adam-desktop:/$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 261936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261936
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261936
[    0.000000] On node 0 totalpages: 261936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32306 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:  Product ID: Springdale-G APIC at: 0xFEE00000
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259890
[    0.000000] Kernel command line: root=UUID=2e916da9-0ff1-4f33-a24d-68dfe6e67644 ro quiet splash acpi=off apm=power_off
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3059.095 MHz processor.
[   23.351643] Console: colour VGA+ 80x25
[   23.351647] console [tty0] enabled
[   23.352262] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.352846] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.380229] Memory: 1026476k/1047744k available (2177k kernel code, 20596k reserved, 1006k data, 368k init, 130240k highmem)
[   23.380239] virtual kernel memory layout:
[   23.380240]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.380241]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.380242]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.380242]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.380243]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   23.380244]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   23.380245]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   23.380248] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.380300] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   23.460149] Calibrating delay using timer specific routine.. 6123.41 BogoMIPS (lpj=12246825)
[   23.460180] Security Framework initialized
[   23.460190] SELinux:  Disabled at boot.
[   23.460207] AppArmor: AppArmor initialized
[   23.460212] Failure registering capabilities with primary security module.
[   23.460220] Mount-cache hash table entries: 512
[   23.460374] Initializing cgroup subsys ns
[   23.460379] Initializing cgroup subsys cpuacct
[   23.460391] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   23.460404] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   23.460407] CPU: L2 cache: 512K
[   23.460409] CPU: Physical Processor ID: 0
[   23.460411] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   23.460424] Compat vDSO mapped to ffffe000.
[   23.460439] Checking 'hlt' instruction... OK.
[   23.476484] SMP alternatives: switching to UP code
[   23.477940] Freeing SMP alternatives: 11k freed
[   23.478063] Early unpacking initramfs... done
[   23.761052] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
[   23.761091] Total of 1 processors activated (6123.41 BogoMIPS).
[   23.761149] ExtINT not setup in hardware but reported by MP table
[   23.761225] ENABLING IO-APIC IRQs
[   23.761413] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   24.014994] Brought up 1 CPUs
[   24.015016] CPU0 attaching sched-domain:
[   24.015019]  domain 0: span 01
[   24.015021]   groups: 01
[   24.015215] net_namespace: 64 bytes
[   24.015227] Booting paravirtualized kernel on bare hardware
[   24.015721] Time: 22:41:48  Date: 07/17/08
[   24.015750] NET: Registered protocol family 16
[   24.015973] EISA bus registered
[   24.017356] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   24.017359] PCI: Using configuration type 1
[   24.017377] Setting up standard PCI resources
[   24.028110] ACPI: Interpreter disabled.
[   24.028114] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.028146] pnp: PnP ACPI: disabled
[   24.028150] PnPBIOS: Scanning system for PnP BIOS support...
[   24.028161] PnPBIOS: Found PnP BIOS installation structure at 0xc00f3450
[   24.028164] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x3a6a, dseg 0xf0000
[   24.028695] PNPBIOS fault.. attempting recovery.
[   24.028745] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   24.028791] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   24.028836] PnPBIOS: Check with your vendor for an updated BIOS
[   24.028880] PnPBIOS: get_dev_node: unexpected status 0x37
[   24.028922] PnPBIOS: 12 nodes reported by PnP BIOS; 12 recorded by driver
[   24.029159] PCI: Probing PCI hardware
[   24.029162] PCI: Probing PCI hardware (bus 00)
[   24.029630] Force enabled HPET at base address 0xfed00000
[   24.029636] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   24.029639] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   24.030172] PCI: Transparent bridge - 0000:00:1e.0
[   24.030908] PCI: Using IRQ router PIIX/ICH [8086/24d0] at 0000:00:1f.0
[   24.030927] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 16
[   24.030931] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 19
[   24.030936] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 18
[   24.030940] PCI->APIC IRQ transform: 0000:00:1d.3[A] -> IRQ 16
[   24.030945] PCI->APIC IRQ transform: 0000:00:1d.7[D] -> IRQ 23
[   24.030952] PCI->APIC IRQ transform: 0000:00:1f.1[A] -> IRQ 18
[   24.030956] PCI->APIC IRQ transform: 0000:00:1f.2[A] -> IRQ 18
[   24.030960] PCI->APIC IRQ transform: 0000:00:1f.3[B] -> IRQ 17
[   24.030963] PCI->APIC IRQ transform: 0000:00:1f.5[B] -> IRQ 17
[   24.030966] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   24.030970] PCI->APIC IRQ transform: 0000:02:03.0[A] -> IRQ 19
[   24.030973] PCI->APIC IRQ transform: 0000:02:04.0[A] -> IRQ 18
[   24.030977] PCI->APIC IRQ transform: 0000:02:08.0[A] -> IRQ 20
[   24.042978] NET: Registered protocol family 8
[   24.042980] NET: Registered protocol family 20
[   24.043095] hpet clockevent registered
[   24.043100] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.043105] hpet0: 3 64-bit timers, 14318180 Hz
[   24.044144] AppArmor: AppArmor Filesystem Enabled
[   24.044185] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   24.044189] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   24.044191] system 00:00: iomem range 0xe6000-0xfffff could not be reserved
[   24.044193] system 00:00: iomem range 0x100000-0x3ff2ffff could not be reserved
[   24.044196] system 00:00: iomem range 0x3ff30000-0x3ff3ffff could not be reserved
[   24.044198] system 00:00: iomem range 0x3ff40000-0x3ffeffff could not be reserved
[   24.044201] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   24.044203] system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
[   24.044206] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   24.044634] PCI: Bridge: 0000:00:01.0
[   24.044636]   IO window: disabled.
[   24.044641]   MEM window: ec500000-ee5fffff
[   24.044644]   PREFETCH window: d4300000-e42fffff
[   24.044650] PCI: Bridge: 0000:00:1e.0
[   24.044652]   IO window: b000-bfff
[   24.044657]   MEM window: ee600000-feafffff
[   24.044661]   PREFETCH window: e4300000-e43fffff
[   24.044680] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.044690] NET: Registered protocol family 2
[   24.046878] Time: tsc clocksource has been installed.
[   24.078895] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.079226] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.080116] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.080632] TCP: Hash tables configured (established 131072 bind 65536)
[   24.080637] TCP reno registered
[   24.090976] checking if image is initramfs... it is
[   24.545804] Switched to high resolution mode on CPU 0
[   24.644311] Freeing initrd memory: 7460k freed
[   24.644916] audit: initializing netlink socket (disabled)
[   24.644933] audit(1216334508.160:1): initialized
[   24.645116] highmem bounce pool size: 64 pages
[   24.646961] VFS: Disk quotas dquot_6.5.1
[   24.647044] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.647231] io scheduler noop registered
[   24.647233] io scheduler anticipatory registered
[   24.647235] io scheduler deadline registered
[   24.647245] io scheduler cfq registered (default)
[   24.647337] Boot video device is 0000:01:00.0
[   24.647343] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   24.647585] isapnp: Scanning for PnP cards...
[   25.000786] isapnp: No Plug & Play device found
[   25.030621] Real Time Clock Driver v1.12ac
[   25.030698] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.030813] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.031612] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.032406] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.032473] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.032585] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.035760] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.035765] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.048670] mice: PS/2 mouse device common for all mice
[   25.048793] EISA: Probing bus 0 at eisa.0
[   25.048826] EISA: Detected 0 cards.
[   25.048829] cpuidle: using governor ladder
[   25.048831] cpuidle: using governor menu
[   25.048922] NET: Registered protocol family 1
[   25.048952] Using IPI No-Shortcut mode
[   25.048983] registered taskstats version 1
[   25.049063]   Magic number: 0:750:704
[   25.049159] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.049160] EDD information not available.
[   25.049547] Freeing unused kernel memory: 368k freed
[   25.076570] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.257047] fuse init (API version 7.9)
[   26.286626] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   26.493408] usbcore: registered new interface driver usbfs
[   26.493435] usbcore: registered new interface driver hub
[   26.505365] usbcore: registered new device driver usb
[   26.513375] USB Universal Host Controller Interface driver v3.0
[   26.513453] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.513457] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.513752] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.513780] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   26.513916] usb usb1: configuration #1 chosen from 1 choice
[   26.513939] hub 1-0:1.0: USB hub found
[   26.513946] hub 1-0:1.0: 2 ports detected
[   26.573226] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   26.573230] e100: Copyright(c) 1999-2006 Intel Corporation
[   26.609344] SCSI subsystem initialized
[   26.617162] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.617168] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.617191] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.617217] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[   26.617324] usb usb2: configuration #1 chosen from 1 choice
[   26.617347] hub 2-0:1.0: USB hub found
[   26.617353] hub 2-0:1.0: 2 ports detected
[   26.661280] libata version 3.00 loaded.
[   26.720929] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.720935] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.720959] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.720985] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   26.721099] usb usb3: configuration #1 chosen from 1 choice
[   26.721122] hub 3-0:1.0: USB hub found
[   26.721128] hub 3-0:1.0: 2 ports detected
[   26.793756] Floppy drive(s): fd0 is 1.44M
[   26.812331] FDC 0 is a post-1991 82077
[   26.824721] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.824727] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.824751] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   26.824775] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   26.824886] usb usb4: configuration #1 chosen from 1 choice
[   26.824909] hub 4-0:1.0: USB hub found
[   26.824916] hub 4-0:1.0: 2 ports detected
[   26.928599] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   26.928605] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   26.928636] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   26.932551] ehci_hcd 0000:00:1d.7: debug port 1
[   26.932557] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   26.932566] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[   26.948308] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.948429] usb usb5: configuration #1 chosen from 1 choice
[   26.948454] hub 5-0:1.0: USB hub found
[   26.948461] hub 5-0:1.0: 8 ports detected
[   27.075466] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:07:e9:64:96:8f
[   27.075485] ata_piix 0000:00:1f.1: version 2.12
[   27.075499] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   27.075547] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.077165] scsi0 : ata_piix
[   27.078070] scsi1 : ata_piix
[   27.078122] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   27.078125] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   27.248854] ata1.00: ATA-5: WDC WD400BB-53AUA1, 18.20D18, max UDMA/100
[   27.248859] ata1.00: 78165360 sectors, multi 16: LBA 
[   27.258296] ata1.01: ATA-7: WDC WD5000AAJB-00UHA0, 07.01N01, max UDMA/100
[   27.258300] ata1.01: 976773168 sectors, multi 16: LBA48 
[   27.273152] ata1.00: configured for UDMA/100
[   27.288316] ata1.01: configured for UDMA/100
[   27.810625] ata2.00: ATAPI: MATSHITA CR-594, YS0M, max UDMA/33
[   27.810647] ata2.01: ATAPI: _NEC NR-7700A, 1.23, max MWDMA2
[   27.982163] ata2.00: configured for UDMA/33
[   28.185889] ata2.01: configured for MWDMA2
[   28.186011] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-53AU 18.2 PQ: 0 ANSI: 5
[   28.186432] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAJB-0 07.0 PQ: 0 ANSI: 5
[   28.188934] scsi 1:0:0:0: CD-ROM            MATSHITA CD-ROM CR-594    YS0M PQ: 0 ANSI: 5
[   28.193255] scsi 1:0:1:0: CD-ROM            _NEC     NR-7700A         1.23 PQ: 0 ANSI: 5
[   28.193325] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   28.193383] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.193720] scsi2 : ata_piix
[   28.193884] scsi3 : ata_piix
[   28.193917] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[   28.193919] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[   28.544324] Driver 'sd' needs updating - please use bus_type methods
[   28.544418] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   28.544432] sd 0:0:0:0: [sda] Write Protect is off
[   28.544434] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.544454] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   28.544503] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   28.544514] sd 0:0:0:0: [sda] Write Protect is off
[   28.544517] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.544535] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   28.544540]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.565542]  sda1 sda2
[   28.589074] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.589144] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   28.589158] sd 0:0:1:0: [sdb] Write Protect is off
[   28.589160] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.589180] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.589224] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   28.589235] sd 0:0:1:0: [sdb] Write Protect is off
[   28.589237] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.589256] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.589260]  sdb: sdb1
[   28.592843] sd 0:0:1:0: [sdb] Attached SCSI disk
[   28.602653] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.602673] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   28.602692] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   28.602709] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   28.606348] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   28.606354] Uniform CD-ROM driver Revision: 3.20
[   28.606414] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   28.627067] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   28.627126] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   28.966446] Attempting manual resume
[   28.966450] swsusp: Resume From Partition 8:2
[   28.966452] PM: Checking swsusp image.
[   28.966636] PM: Resume from disk failed.
[   29.012779] kjournald starting.  Commit interval 5 seconds
[   29.012794] EXT3-fs: mounted filesystem with ordered data mode.
[   36.399088] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   36.560523] iTCO_vendor_support: vendor-support=0
[   36.566071] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.582596] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.590252] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.612660] Linux agpgart interface v0.102
[   36.715299] agpgart: Detected an Intel 865 Chipset.
[   36.718084] agpgart: AGP aperture is 64M @ 0xe8000000
[   37.198004] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   37.229342] Linux video capture interface: v2.00
[   37.231499] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   37.231534] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.334249] nvidia: module license 'NVIDIA' taints kernel.
[   37.912270] Intel 82802 RNG detected
[   37.928537] cx18:  Start initialization, version 1.0.0
[   37.928602] cx18-0: Initializing card #0
[   37.928607] cx18-0: Autodetected Hauppauge card
[   37.928634] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   37.928814] cx18-0: cx23418 revision 01010000 (B)
[   38.060291] tveeprom 0-0050: Hauppauge model 74041, rev C6B2, serial# 936551
[   38.060295] tveeprom 0-0050: MAC address is 00-0D-FE-0E-4A-67
[   38.060298] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   38.060300] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   38.060303] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   38.060305] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   38.060307] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   38.060309] cx18-0: Autodetected Hauppauge HVR-1600
[   38.060311] cx18-0: VBI is not yet supported
[   38.196061] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   38.196085] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   38.197737] cx18-0: Disabled encoder IDX device
[   38.197765] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   38.197769] DVB: registering new adapter (cx18)
[   38.323536] MXL5005S: Attached at address 0x63
[   38.323543] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   38.323610] cx18-0: DVB Frontend registered
[   38.323631] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   38.323648] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   38.370610] tuner-simple 1-0061: creating new instance
[   38.370615] tuner-simple 1-0061: type set to 50 (TCL 2002N)
[   39.138906] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   39.239417] cx18-0: loaded v4l-cx23418-cpu.fw firmware (174716 bytes)
[   39.245524] cx18-0: FW version: 0.0.71.0 (Release 2006/12/29)
[   39.809639] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   39.813885] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   39.814202] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   39.814778] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   39.830758] cx18:  End initialization
[   40.234115] intel8x0_measure_ac97_clock: measured 52014 usecs
[   40.234119] intel8x0: clocking to 48000
[   40.794152] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[   40.888974] lp0: using parport0 (polling).
[   40.948144] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.238941] Adding 2947916k swap on /dev/sda2.  Priority:-1 extents:1 across:2947916k
[   41.930867] EXT3 FS on sda1, internal journal
[   42.848685] JFS: nTxBlock = 8082, nTxLock = 64662
[   43.605613] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.808494] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   46.808547] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   46.808719] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   46.808799] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   49.026933] NET: Registered protocol family 10
[   49.027167] lo: Disabled Privacy Extensions
[   61.365196] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.366202] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   61.378479] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.154120] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   64.154136] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   64.154169] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   65.160697] NET: Registered protocol family 17
[   81.388381] eth0: no IPv6 routers present
[  126.555879] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  126.555885] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1679.573851] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1679.573857] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1739.216897] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1739.216902] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2274.330452] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2274.330458] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2334.041917] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2334.041922] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2410.269395] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2410.269401] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2452.096951] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[ 2452.096956] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[ 2452.147136] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[ 2452.147140] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[ 2470.836585] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2470.836591] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2530.449170] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2530.449176] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3405.345247] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3405.345253] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3556.562486] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3556.562492] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3615.904123] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3615.904129] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3675.503660] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3675.503666] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3749.027082] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3749.027088] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3830.927591] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3830.927597] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3880.422397] mythtv-setup.re[6405]: segfault at 000000b8 eip b6566e91 esp afca1d80 error 4
[ 3895.335092] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3895.335098] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 3942.477434] mythtv-setup.re[6486]: segfault at 000000b8 eip b65bee91 esp afcf9d80 error 4
[ 3954.906773] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 3954.906779] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4004.706221] mythtv-setup.re[6557]: segfault at 000000b8 eip b65b9e91 esp afcf4d80 error 4
[ 4021.604012] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4021.604018] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4087.815027] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4087.815033] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4126.705498] mythtv-setup.re[6640]: segfault at 000000b8 eip b6598e91 esp afcd3d80 error 4
[ 4201.020641] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4201.020646] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4262.275716] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4262.275722] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4385.397878] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4385.397884] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4430.623128] DVB: frontend 0 frequency 11954000 out of range (54000000..858000000)
[ 4452.158150] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4452.158156] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 4511.724889] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 4511.724894] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5373.703985] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5373.703991] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5462.895109] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5462.895115] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5555.718851] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5555.718857] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5561.619720] mythtv-setup.re[11309]: segfault at 000000b8 eip b657ce91 esp afc95d80 error 4
[ 5577.061619] mythtv-setup.re[11378]: segfault at 000000b8 eip b655ae91 esp afc73d80 error 4
[ 5603.473400] mythtv-setup.re[11447]: segfault at 000000b8 eip b657ce91 esp afc95d80 error 4
[ 5615.212396] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5615.212402] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5648.861972] atkbd.c: Unknown key pressed (translated set 2, code 0xbe on isa0060/serio0).
[ 5648.861978] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
[ 5649.135970] atkbd.c: Unknown key released (translated set 2, code 0xbe on isa0060/serio0).
[ 5649.135976] atkbd.c: Use 'setkeycodes e03e <keycode>' to make it known.
[ 5673.573024] mythtv-setup.re[11612]: segfault at 000000b8 eip b65b3e91 esp afcccd80 error 4
[ 5678.159813] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5678.159819] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5692.852553] mythtv-setup.re[11681]: segfault at 000000b8 eip b65b2e91 esp afccbd80 error 4
[ 5753.030289] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5753.030294] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5765.841190] mythtv-setup.re[11785]: segfault at 000000b8 eip b6546e91 esp afc5fd80 error 4
[ 5812.504742] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5812.504748] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5817.884403] mythtv-setup.re[11904]: segfault at 000000b8 eip b65e6e91 esp afcffd80 error 4
[ 5838.506468] mythtv-setup.re[11973]: segfault at 000000b8 eip b660ae91 esp afd23d80 error 4
[ 5859.138619] mythtv-setup.re[12042]: segfault at 000000b8 eip b656ee91 esp afc87d80 error 4
[ 5872.107123] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5872.107129] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 5881.927038] mythtv-setup.re[12111]: segfault at 000000b8 eip b6615e91 esp afd2ed80 error 4
[ 5955.727289] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 5955.727295] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6015.366781] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6015.366786] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6167.791852] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6167.791858] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6227.504174] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6227.504180] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6308.677019] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6308.677025] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6372.353618] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6372.353624] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6434.393572] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6434.393578] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6497.728714] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6497.728720] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6562.475108] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6562.475113] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 6622.414715] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 6622.414721] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 8486.020253] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 8486.020259] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 8551.741953] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 8551.741959] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 8619.609687] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 8619.609692] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[10676.149757] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[10676.149763] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[10735.520722] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[10735.520727] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[10795.200022] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[10795.200028] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[10857.280981] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[10857.280986] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[10916.915524] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[10916.915530] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11067.819899] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11067.819905] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11159.010377] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11159.010382] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11219.830086] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11219.830092] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11286.811108] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11286.811114] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11346.513360] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11346.513366] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11407.307144] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11407.307150] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11466.920398] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11466.920404] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11526.515763] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11526.515769] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11596.182133] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11596.182139] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11655.803204] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11655.803210] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[11736.402126] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[11736.402132] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[12175.309518] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[12175.309523] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[12472.373626] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[12472.373632] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
```


Thanks for taking a look at it.

---

### Post by superm1 on 2008-07-18
OK well not firmware errors.  It looks like you are trying the analog side only..  Have you tried to see if the digital side can capture?

---

### Post by azmanam on 2008-07-18
ah hell...

I ran the scheduled updates before I turned my computer off last night, and it must have updated some or all of the kernel (I guess).  It reverted all my settings to a position I was in several days ago.  Not only has all my progress with the tv tuner card been lost, but other problems I've had that I have found fixes for in other forum threads (e.g. [http://ubuntuforums.org/showthread.php?t=603054](http://ubuntuforums.org/showthread.php?t=603054)) also reverted to pre-fixed condition.

So I assumed I'd have to go back through and redo all the steps for those various problems, including the tv tuner card. ... But all the modifications I had made were still present.  The only thing I can see missing is the ENTIRE /dev/dvb folder.  I don't know where it went, and after following the directions for the Hauppauge 1600 card, the folder does not return.

The instructions tell me to confirm the output of /dev/dvb/adapter0 to ensure the dvb adaptor is working.  I can't confirm that because the file doesn't exist because the folder doesn't exist.

When I (laughingly) attempt to Watch TV, the screen flashes black and reverts to the frontend menu.  I've posted about this before ([http://ubuntuforums.org/showthread.php?t=851602](http://ubuntuforums.org/showthread.php?t=851602)), and I cannot repeat the suggestions there, because my Capture Cards menu isn't populated because it cannot recognize the TV Tuner card.

So I don't know what to do anymore.  I've tried redoing the steps for the Hauppauge card that I thought were working for me before, but I can't progress any further if a key folder is missing.  I'm now further away from having a working system than I was when I posted this topic 24 hours ago.

This is getting mighty frustrating mighty fast.  I really appreciate anyone who can offer advice or assistance. 





One thought, in my /lib/firmware folder, I have folders for 2.6.24-16-generic AND 2.6.24-19-generic kernels.  When I was running through the Hauppauge instructions, I noticed the output of the make and make install seemed to be accessing the 16 folder at the exclusion of the 19 folder.  Could this have anything to do with anything, and if I straight delete the 16 folder from the /lib/firmware folder will this help or crash my system?

---

### Post by azmanam on 2008-07-18
> It looks like you are trying the analog side only.. Have you tried to see if the digital side can capture?

99% of the time, I had the coax cable hooked into the ATSC jack.  My brief success with some sort of picture that I mentioned was from the ATCS jack.  Every once in a rare while, I would hook it into the TV jack for a short time to see what happened.  I was about to hook it into the TV jack and try watching /dev/video0, but never got that far because of the aforementioned issues...

(edited for clarity)

---

### Post by azmanam on 2008-07-18
(ps.  Just checked, and now /dev/video0 doesn't even exist anymore either)

---

### Post by azmanam on 2008-07-18
what's the phrase?  If it ain't broke... fix it til it is.

I've heard from coworkers and seen on forums that an upgrade of the kernel requires reinstallation of NVIDIA drivers.  So I go to NVIDIA's website and follow the instructions for the requisite drivers.  Install.  Reboot.  Total crash.  Splash screen loads, various text about not doing something so trying it another way.  Not on screen long enough to read.  Eventually screen to black, nothing I can do but a hard shutdown.

Load into shell, quickly roll back drivers.  Reboot.  SAME THING.  I can't get into the GUI at all.  I think this means X isn't loading, but I don't really know what that phrase means.

I'm shutting it down for the night and I'm going to put in a DVD.  I'm considering a total OS reinstall.  That's gonna happen on Sunday unless someone convinces me not to.

---

### Post by azmanam on 2008-07-19
Saturday morning instead of booting into shell, I selected 'try to fix x server' then 'continue into normal boot'  and, well, I can get into the GUI again.  So I guess the x-server is fixed (whew).  So this message and the one immediately previous can be disregarded, and I'm only dealing with all the other problems I have...

---

### Post by willoconley on 2008-07-19
hello, 
 for the nvidia drivers to work with v4l try adding what is in red to /boot/grub/menu.lst on the kernel line like:

## ## End Default Options ##
title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=f70a49f8-885a-4942-904b-56a0ae6f68bc ro quiet splash rootflags=data=writeback [COLOR=Red]vmalloc=192M pci=nommconf[/COLOR]
initrd /boot/initrd.img-2.6.24-18-generic
quiet

and then you will have to edit /etc/X11/xorg.conf to use nvidia driver, if when you ran 'try to fix x server' changed to nv or vesa

could you post the output of:
cat dmesg | grep cx18

also what procedure did you use to install the v4l drivers

---

### Post by azmanam on 2008-07-19
Thanks for taking a look at this :)

**vmalloc=192M pci=nommconf
done

**edit /etc/X11/xorg.conf to use nvidia driver
Not sure what to do here.  Here is my .conf file:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

**could you post the output of: cat dmesg | grep cx18
Gladly:

```
adam@adam-desktop:~$ cat dmesg | grep cx18
cat: dmesg: No such file or directory
```

**what procedure did you use to install the v4l drivers
Via [http://ubuntuforums.org/showthread.php?t=813429](http://ubuntuforums.org/showthread.php?t=813429) reply #67:

> download
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

extract here in the desktop and open terminal and enter commands

cd ~/Desktop/v4l-dvb-04ddbe145932
make *(I needed to sudo this command, too. -ed)*
sudo make install (dont forget to enter password)

now to add a startup and in terminal you type
------------------------------------------
sudo gedit /etc/modules
add cx18 at the bottom.
save and exit
reboot

now do a "ls -l /dev/dvb/adapter0" without parenthesis.

and you should see an output like this part

-desktop:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-06-10 09:16 demux0
crw-rw----+ 1 root video 212, 5 2008-06-10 09:16 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-10 09:16 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-10 09:16 net0

And my result (after the 'upgrade' devolved my system, I repeated the above steps except for downloading the tar.bz2 file because it was still there and except for appending the /etc/modules file because it was still appended):

```
adam@adam-desktop:~$ ls -l /dev/dvb/adapter0
ls: cannot access /dev/dvb/adapter0: No such file or directory
```

Thanks again for giving me a hand.  I really really appreciate all the help I can get.

(edited for clarity)

---

### Post by willoconley on 2008-07-19
oops sorry,

cat dmesg | grep cx18

should be

dmesg | grep cx18


so if that is your xorg.conf then you aren't using nvidia, you could try 

gksudo nvidia-settings 

it gives you a bunch of options to set up twinview and set resolutions and such or just add whats in red to xorg.conf

```
Section "Device"
        Identifier      "Configured Video Device"
	[COLOR="Red"]Driver		"nvidia"[/COLOR]
EndSection
```

for v4l probably all you'll need to add to what you did is

cd ~/Desktop/v4l-dvb-04ddbe145932
[COLOR="Red"]sudo make unload
sudo make distclean[/COLOR]
sudo make
sudo make install

---

### Post by azmanam on 2008-07-19
**thanks:

```
adam@adam-desktop:~$ dmesg | grep cx18
[   38.921672] cx18: disagrees about version of symbol dvb_dmxdev_init
[   38.921679] cx18: Unknown symbol dvb_dmxdev_init
[   38.922331] cx18: disagrees about version of symbol dvb_register_adapter
[   38.922335] cx18: Unknown symbol dvb_register_adapter
[   38.923021] cx18: disagrees about version of symbol dvb_net_init
[   38.923025] cx18: Unknown symbol dvb_net_init
[   38.923114] cx18: disagrees about version of symbol video_unregister_device
[   38.923118] cx18: Unknown symbol video_unregister_device
[   38.923174] cx18: disagrees about version of symbol dvb_dmxdev_release
[   38.923178] cx18: Unknown symbol dvb_dmxdev_release
[   38.923225] cx18: disagrees about version of symbol cx2341x_update
[   38.923228] cx18: Unknown symbol cx2341x_update
[   38.923274] cx18: disagrees about version of symbol video_device_alloc
[   38.923278] cx18: Unknown symbol video_device_alloc
[   38.923361] cx18: disagrees about version of symbol video_register_device
[   38.923365] cx18: Unknown symbol video_register_device
[   38.923500] cx18: disagrees about version of symbol dvb_frontend_detach
[   38.923504] cx18: Unknown symbol dvb_frontend_detach
[   38.923571] cx18: disagrees about version of symbol dvb_net_release
[   38.923575] cx18: Unknown symbol dvb_net_release
[   38.923830] cx18: disagrees about version of symbol dvb_unregister_frontend
[   38.923834] cx18: Unknown symbol dvb_unregister_frontend
[   38.923961] cx18: disagrees about version of symbol dvb_register_frontend
[   38.923965] cx18: Unknown symbol dvb_register_frontend
[   38.924136] cx18: disagrees about version of symbol video_device_release
[   38.924140] cx18: Unknown symbol video_device_release
[   40.717322] cx18: disagrees about version of symbol dvb_dmxdev_init
[   40.717328] cx18: Unknown symbol dvb_dmxdev_init
[   40.717784] cx18: disagrees about version of symbol dvb_register_adapter
[   40.717786] cx18: Unknown symbol dvb_register_adapter
[   40.718296] cx18: disagrees about version of symbol dvb_net_init
[   40.718298] cx18: Unknown symbol dvb_net_init
[   40.718363] cx18: disagrees about version of symbol video_unregister_device
[   40.718365] cx18: Unknown symbol video_unregister_device
[   40.718406] cx18: disagrees about version of symbol dvb_dmxdev_release
[   40.718408] cx18: Unknown symbol dvb_dmxdev_release
[   40.718441] cx18: disagrees about version of symbol cx2341x_update
[   40.718443] cx18: Unknown symbol cx2341x_update
[   40.718476] cx18: disagrees about version of symbol video_device_alloc
[   40.718478] cx18: Unknown symbol video_device_alloc
[   40.718538] cx18: disagrees about version of symbol video_register_device
[   40.718540] cx18: Unknown symbol video_register_device
[   40.718639] cx18: disagrees about version of symbol dvb_frontend_detach
[   40.718641] cx18: Unknown symbol dvb_frontend_detach
[   40.718690] cx18: disagrees about version of symbol dvb_net_release
[   40.718691] cx18: Unknown symbol dvb_net_release
[   40.718878] cx18: disagrees about version of symbol dvb_unregister_frontend
[   40.718880] cx18: Unknown symbol dvb_unregister_frontend
[   40.718973] cx18: disagrees about version of symbol dvb_register_frontend
[   40.718975] cx18: Unknown symbol dvb_register_frontend
[   40.719100] cx18: disagrees about version of symbol video_device_release
[   40.719102] cx18: Unknown symbol video_device_release
```

**gksudo nvidia-settings gives me an error about not using nvidia in x-server or something, so I appended the .conf as suggested.

**after adding the 2 make commands, the rest seemed to access the 19 kernel as expected.  I have to run out, so I won't get to see the new results until tomorrow, but I'll post more trials tribulations later :)

Thanks SO much for your assistance!  I'll get this working yet.

---

### Post by azmanam on 2008-07-19
PS.  It's interesting that I'm not using NVIDIA.  The first thing I see when I turn on the computer is info about my NVIDIA card: model, ram, etc.  In fact, I know when I've screwed up my driver and am going to have to backpedal because I WON'T see the NVIDIA info when I boot up.

---

### Post by azmanam on 2008-07-20
When I booted up this morning, I saw a full-screen NVIDIA splash screen.  I haven't seen that before.  That seems like a step forward.  I also noticed /dev/dvb is back!  WOOHOO!

```
adam@adam-desktop:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-07-20 06:45 demux0
crw-rw----+ 1 root video 212, 5 2008-07-20 06:45 dvr0
crw-rw----+ 1 root video 212, 3 2008-07-20 06:45 frontend0
crw-rw----+ 1 root video 212, 7 2008-07-20 06:45 net0
```

When I attempt to scan for channels via reply 67 from above, every tuning failed:

```
adam@adam-desktop:/usr/share/doc/dvb-utils$ sudo scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!

...

WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
```

This is my new dmesg | grep cx18 output:

```
adam@adam-desktop:~$ dmesg | grep cx18
[   39.903394] cx18:  Start initialization, version 1.0.0
[   39.903477] cx18-0: Initializing card #0
[   39.903483] cx18-0: Autodetected Hauppauge card
[   39.903531] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   39.903843] cx18-0: cx23418 revision 01010000 (B)
[   40.112636] cx18-0: Autodetected Hauppauge HVR-1600
[   40.112640] cx18-0: VBI is not yet supported
[   40.254164] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   40.254209] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   40.338206] cx18-0: Disabled encoder IDX device
[   40.338267] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   40.338273] DVB: registering new adapter (cx18)
[   40.549578] cx18-0: DVB Frontend registered
[   40.549613] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   40.549646] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   40.549650] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   40.549788] cx18:  End initialization
[   62.762898] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   63.322532] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   63.328516] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   63.334733] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   63.334787] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 158332 bytes)
[   63.334792] cx18-0: Did you put the firmware in the hotplug firmware directory?
[   63.334797] cx18-0: Retry loading firmware
[   63.388535] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   63.887851] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   63.893908] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   63.900106] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   63.900157] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 158332 bytes)
[   63.900163] cx18-0: Did you put the firmware in the hotplug firmware directory?
[   63.900168] cx18-0: Failed to initialize on minor 0
[   63.901212] cx18-0: Failed to initialize on minor 0
[   63.904949] cx18-0: Failed to initialize on minor 24
[   63.907476] cx18-0: Failed to initialize on minor 32
[   64.029590] cx18-0: Failed to initialize on minor 0
[   84.423772] cx18-0: Failed to initialize on minor 24
```

I saw this in that other thread, too, so I'll post it in case it's relevant:

```
adam@adam-desktop:~$ ls /lib/modules/2.6.24-??-generic/kernel/drivers/media/video/* | grep cx18
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/cx18:
cx18.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/cx18:
cx18.ko
```

The rest of the posts in that thread seem to springboard off the fact that OP can receive a successful output from channel scanning.  I'll stop here as I am as yet unable to do that and await further instructions.

Thanks for all your help and for convincing me not to reinstall the OS.

---

### Post by azmanam on 2008-07-20
I tried configuring some of the backend options this morning.

In the Capture Cards menu, if I select analog v4l, the video device option remains blank.  If I manually input /dev/video0, the vbi device line remains blank and the default input line reads 'could not open /dev/video0 to'.  the probe info line reads 'Failed to open.'

If I select DVB DTV Capture card (v3.x), the DVB Device number read '0' and the frontend ID reads 'Samsung S5H1409 QAM/Subtype ATSC'

In the Input Connections menu, if I select the DVB card, the capture device line reads 'DVB : 0,' the input line reads 'DVB Input.'  If I attempt to 'scan for channels,' I receive Timeout-No signal for every channel. The scan configuration menu has input read 'DVB:0 (DVBInput), scan type reads 'full scan,' Frequency table reads 'broadcast', modulation reads 'Terrestrial (8-VSB), ATSC Channel separator reads '(51) None' and existing channel treatment reads 'minimal updates'

In the initial input connections menu, where I choose which capture card to manipulate, the V4L one reads 'V4L :/dev/video0 (could not open /dev/video0 to probe its inputs) -> none'  If I open that card to see the options, Input again reads the 'could not probe' message, and all lines are blank.

This is different from the settings in post 1.  Whatever happened when I ran the scheduled updates really rolled back my system.

Just for reference, here is how my log files read for today:

Backend:

```
$cat /var/log/mythtv/mythbackend.log
2008-07-20 06:45:42.575 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-20 06:45:42.716 Empty LocalHostName.
2008-07-20 06:45:42.908 Using localhost value of adam-desktop
2008-07-20 06:45:43.132 New DB connection, total: 1
2008-07-20 06:45:43.381 Connected to database 'mythconverg' at host: localhost
2008-07-20 06:45:43.540 Closing DB connection named 'DBManager0'
2008-07-20 06:45:43.680 Connected to database 'mythconverg' at host: localhost
2008-07-20 06:45:43.942 New DB connection, total: 2
2008-07-20 06:45:44.155 Connected to database 'mythconverg' at host: localhost
2008-07-20 06:45:44.770 Current Schema Version: 1214
Starting up as the master server.
2008-07-20 06:45:46.854 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
2008-07-20 06:45:46.984 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-07-20 06:45:47.211 New DB connection, total: 3
2008-07-20 06:45:47.268 Connected to database 'mythconverg' at host: localhost
2008-07-20 06:45:47.319 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-20 06:45:47.544 Main::Registering HttpStatus Extension
2008-07-20 06:45:47.661 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 06:45:47.728 Enabled verbose msgs:  important general
2008-07-20 06:45:47.824 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 06:47:07.710 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 06:56:07.999 MainServer::HandleAnnounce Monitor
2008-07-20 06:56:08.089 adding: adam-desktop as a client (events: 0)
2008-07-20 06:56:08.140 MainServer::HandleAnnounce Monitor
2008-07-20 06:56:08.190 adding: adam-desktop as a client (events: 1)
2008-07-20 07:02:08.408 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 07:17:08.490 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 10:03:49.673 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-20 10:03:49.841 Empty LocalHostName.
2008-07-20 10:03:50.029 Using localhost value of adam-desktop
2008-07-20 10:03:50.372 New DB connection, total: 1
2008-07-20 10:03:50.526 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:03:50.606 Closing DB connection named 'DBManager0'
2008-07-20 10:03:50.722 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:03:51.116 New DB connection, total: 2
2008-07-20 10:03:51.465 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:03:51.776 Current Schema Version: 1214
Starting up as the master server.
2008-07-20 10:03:53.735 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
2008-07-20 10:03:53.874 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-07-20 10:03:54.183 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-20 10:03:54.256 Main::Registering HttpStatus Extension
2008-07-20 10:03:54.323 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 10:03:54.515 Enabled verbose msgs:  important general
2008-07-20 10:03:54.657 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 10:04:28.402 MainServer::HandleAnnounce Monitor
2008-07-20 10:04:28.485 adding: adam-desktop as a client (events: 0)
2008-07-20 10:04:28.536 MainServer::HandleAnnounce Monitor
2008-07-20 10:04:28.585 adding: adam-desktop as a client (events: 1)
2008-07-20 10:07:16.881 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-20 10:07:16.950 Empty LocalHostName.
2008-07-20 10:07:17.008 Using localhost value of adam-desktop
2008-07-20 10:07:17.070 New DB connection, total: 1
2008-07-20 10:07:17.131 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:07:17.178 Closing DB connection named 'DBManager0'
2008-07-20 10:07:17.228 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:07:17.279 New DB connection, total: 2
2008-07-20 10:07:17.328 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:07:17.381 Current Schema Version: 1214
Starting up as the master server.
2008-07-20 10:07:17.490 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
2008-07-20 10:07:17.608 New DB connection, total: 3
2008-07-20 10:07:17.654 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:07:19.440 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:07:19.621 DVBChan(6:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:07:21.747 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:07:22.064 DVBChan(7:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:07:22.437 New DB scheduler connection
2008-07-20 10:07:22.667 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:07:23.098 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-20 10:07:23.259 Main::Registering HttpStatus Extension
2008-07-20 10:07:23.569 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 10:07:23.711 Enabled verbose msgs:  important general
2008-07-20 10:07:23.948 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 10:07:26.080 Reschedule requested for id -1.
2008-07-20 10:07:26.323 Scheduled 0 items in 0.2 = 0.21 match + 0.03 place
2008-07-20 10:07:26.427 Seem to be woken up by USER
2008-07-20 10:08:02.025 MainServer::HandleAnnounce Monitor
2008-07-20 10:08:06.326 adding: adam-desktop as a client (events: 0)
2008-07-20 10:08:06.394 MainServer::HandleAnnounce Monitor
2008-07-20 10:08:06.443 adding: adam-desktop as a client (events: 1)
2008-07-20 10:08:06.495 Reschedule requested for id -1.
2008-07-20 10:08:06.571 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-20 10:08:43.085 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 10:22:07.473 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-20 10:22:07.514 Empty LocalHostName.
2008-07-20 10:22:07.573 Using localhost value of adam-desktop
2008-07-20 10:22:07.634 New DB connection, total: 1
2008-07-20 10:22:07.686 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:22:07.742 Closing DB connection named 'DBManager0'
2008-07-20 10:22:07.791 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:22:07.843 New DB connection, total: 2
2008-07-20 10:22:07.891 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:22:07.944 Current Schema Version: 1214
Starting up as the master server.
2008-07-20 10:22:08.122 New DB connection, total: 3
2008-07-20 10:22:08.169 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:22:08.246 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:22:08.294 DVBChan(8:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:22:08.395 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:22:08.444 DVBChan(9:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:22:08.653 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:22:08.703 DVBChan(10:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:22:08.857 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
2008-07-20 10:22:08.922 New DB scheduler connection
2008-07-20 10:22:08.971 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:22:09.042 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-20 10:22:09.096 Main::Registering HttpStatus Extension
2008-07-20 10:22:09.146 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 10:22:09.196 Enabled verbose msgs:  important general
2008-07-20 10:22:09.249 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 10:22:12.025 Reschedule requested for id -1.
2008-07-20 10:22:12.120 Scheduled 0 items in 0.1 = 0.05 match + 0.05 place
2008-07-20 10:22:12.181 Seem to be woken up by USER
2008-07-20 10:31:10.702 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-20 10:31:10.748 Empty LocalHostName.
2008-07-20 10:31:10.808 Using localhost value of adam-desktop
2008-07-20 10:31:10.868 New DB connection, total: 1
2008-07-20 10:31:10.920 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:31:10.968 Closing DB connection named 'DBManager0'
2008-07-20 10:31:11.027 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:31:11.078 New DB connection, total: 2
2008-07-20 10:31:11.127 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:31:11.180 Current Schema Version: 1214
Starting up as the master server.
2008-07-20 10:31:11.374 New DB connection, total: 3
2008-07-20 10:31:11.420 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:31:11.488 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:31:11.536 DVBChan(8:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:31:11.627 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:31:11.670 DVBChan(9:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:31:11.929 DTVMux, Error: Could not find tuning parameters for mplex 32767
2008-07-20 10:31:11.978 DVBChan(10:0) Error: SetChannelByString(0): Failed to initialize multiplex options
2008-07-20 10:31:12.136 Channel(/dev/video0)::Open(): Can't open video device, error "No such device or address"
2008-07-20 10:31:12.206 New DB scheduler connection
2008-07-20 10:31:12.254 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:31:12.327 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-07-20 10:31:12.371 Main::Registering HttpStatus Extension
2008-07-20 10:31:12.421 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 10:31:12.471 Enabled verbose msgs:  important general
2008-07-20 10:31:12.524 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-20 10:31:15.308 Reschedule requested for id -1.
2008-07-20 10:31:15.376 Scheduled 0 items in 0.1 = 0.05 match + 0.02 place
2008-07-20 10:31:15.440 Seem to be woken up by USER
2008-07-20 10:32:32.311 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

Frontend:

```
$cat /var/log/mythtv/mythfrontend.log
2008-07-20 06:46:07.625 New DB connection, total: 2
2008-07-20 06:46:07.626 Connected to database 'mythconverg' at host: localhost
2008-07-20 06:46:07.630 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 06:46:07.630 Enabled verbose msgs:  important general
2008-07-20 06:46:08.963 Unable to parse themeinfo.xml for glass-wide
2008-07-20 06:46:08.963 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-20 06:46:10.336 Unable to parse themeinfo.xml for glass-wide
2008-07-20 06:46:10.336 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-20 06:46:12.367 Primary screen 0.
2008-07-20 06:46:12.367 Using screen 0, 1360x768 at 0,0
2008-07-20 06:46:12.370 Switching to square mode (Mythbuntu-8.04)
2008-07-20 06:46:12.398 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-20 06:46:12.399 lirc_init failed for mythtv, see preceding messages
2008-07-20 06:46:12.399 JoystickMenuClient Error: Joystick disabled - Failed to read /home/adam/.mythtv/joystickmenurc
2008-07-20 06:46:14.178 Specified base font 'medium' does not exist for font clock
2008-07-20 06:46:14.178 Specified base font 'medium' does not exist for font small
2008-07-20 06:46:14.178 Specified base font 'medium' does not exist for font medium
2008-07-20 06:46:14.178 Specified base font 'medium' does not exist for font large
2008-07-20 06:46:14.180 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-20 06:46:14.317 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-20 06:46:14.474 Registering Internal as a media playback plugin.
2008-07-20 06:46:14.769 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-07-20 06:46:15.267 Failed to run 'cdrecord --scanbus'
2008-07-20 06:46:15.272 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-07-20 06:46:15.276 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-07-20 06:46:15.336 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.15.103:5060 NAT address 192.168.15.103
SIP: Cannot register; proxy, username or password not set
2008-07-20 06:56:07.996 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-20 06:56:07.998 Using protocol version 40
Destroying SipFsm object 
2008-07-20 06:56:10.592 Deleting UPnP client...
Starting mythfrontend.real..
2008-07-20 10:04:10.879 New DB connection, total: 2
2008-07-20 10:04:10.880 Connected to database 'mythconverg' at host: localhost
2008-07-20 10:04:10.882 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-07-20 10:04:10.883 Enabled verbose msgs:  important general
2008-07-20 10:04:12.077 Unable to parse themeinfo.xml for glass-wide
2008-07-20 10:04:12.078 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-20 10:04:12.911 Unable to parse themeinfo.xml for glass-wide
2008-07-20 10:04:12.911 The theme (glass-wide) is missing a themeinfo.xml file
2008-07-20 10:04:15.038 Primary screen 0.
2008-07-20 10:04:15.038 Using screen 0, 1360x768 at 0,0
2008-07-20 10:04:15.041 Switching to square mode (Mythbuntu-8.04)
2008-07-20 10:04:15.071 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-07-20 10:04:15.071 lirc_init failed for mythtv, see preceding messages
2008-07-20 10:04:15.072 JoystickMenuClient Error: Joystick disabled - Failed to read /home/adam/.mythtv/joystickmenurc
2008-07-20 10:04:16.905 Specified base font 'medium' does not exist for font clock
2008-07-20 10:04:16.905 Specified base font 'medium' does not exist for font small
2008-07-20 10:04:16.905 Specified base font 'medium' does not exist for font medium
2008-07-20 10:04:16.906 Specified base font 'medium' does not exist for font large
2008-07-20 10:04:16.907 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-07-20 10:04:17.043 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-07-20 10:04:17.197 Registering Internal as a media playback plugin.
2008-07-20 10:04:17.851 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-07-20 10:04:18.346 Failed to run 'cdrecord --scanbus'
2008-07-20 10:04:18.349 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-07-20 10:04:18.352 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-07-20 10:04:18.412 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.15.103:5060 NAT address 192.168.15.103
SIP: Cannot register; proxy, username or password not set
2008-07-20 10:04:28.400 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-20 10:04:28.402 Using protocol version 40
Destroying SipFsm object 
2008-07-20 10:04:31.653 Deleting UPnP client...
```

In case it's relevant, syslog (at least what I could copy from terminal):

```
$cat /var/log/syslog
/100
Jul 20 10:03:39 adam-desktop kernel: [   28.274814] ata2.00: ATAPI: MATSHITA CR-594, YS0M, max UDMA/33
Jul 20 10:03:39 adam-desktop kernel: [   28.274837] ata2.01: ATAPI: _NEC NR-7700A, 1.23, max MWDMA2
Jul 20 10:03:39 adam-desktop kernel: [   28.446356] ata2.00: configured for UDMA/33
Jul 20 10:03:39 adam-desktop kernel: [   28.650078] ata2.01: configured for MWDMA2
Jul 20 10:03:39 adam-desktop kernel: [   28.650202] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-53AU 18.2 PQ: 0 ANSI: 5
Jul 20 10:03:39 adam-desktop kernel: [   28.650627] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAJB-0 07.0 PQ: 0 ANSI: 5
Jul 20 10:03:39 adam-desktop kernel: [   28.653132] scsi 1:0:0:0: CD-ROM            MATSHITA CD-ROM CR-594    YS0M PQ: 0 ANSI: 5
Jul 20 10:03:39 adam-desktop kernel: [   28.657845] scsi 1:0:1:0: CD-ROM            _NEC     NR-7700A         1.23 PQ: 0 ANSI: 5
Jul 20 10:03:39 adam-desktop kernel: [   28.657916] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Jul 20 10:03:39 adam-desktop kernel: [   28.657972] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul 20 10:03:39 adam-desktop kernel: [   28.658317] scsi2 : ata_piix
Jul 20 10:03:39 adam-desktop kernel: [   28.658484] scsi3 : ata_piix
Jul 20 10:03:39 adam-desktop kernel: [   28.658516] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
Jul 20 10:03:39 adam-desktop kernel: [   28.658519] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
Jul 20 10:03:39 adam-desktop kernel: [   29.008521] Driver 'sd' needs updating - please use bus_type methods
Jul 20 10:03:39 adam-desktop kernel: [   29.008612] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Jul 20 10:03:39 adam-desktop kernel: [   29.008626] sd 0:0:0:0: [sda] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   29.008628] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   29.008648] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   29.008697] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Jul 20 10:03:39 adam-desktop kernel: [   29.008708] sd 0:0:0:0: [sda] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   29.008710] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   29.008728] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   29.008732]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jul 20 10:03:39 adam-desktop kernel: [   29.172267]  sda1 sda2
Jul 20 10:03:39 adam-desktop kernel: [   29.195823] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 20 10:03:39 adam-desktop kernel: [   29.196363] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 20 10:03:39 adam-desktop kernel: [   29.196377] sd 0:0:1:0: [sdb] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   29.196380] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   29.196399] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   29.196461] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 20 10:03:39 adam-desktop kernel: [   29.196472] sd 0:0:1:0: [sdb] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   29.196475] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   29.196493] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   29.196497]  sdb: sdb1
Jul 20 10:03:39 adam-desktop kernel: [   29.198924] sd 0:0:1:0: [sdb] Attached SCSI disk
Jul 20 10:03:39 adam-desktop kernel: [   29.208330] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 20 10:03:39 adam-desktop kernel: [   29.208351] sd 0:0:1:0: Attached scsi generic sg1 type 0
Jul 20 10:03:39 adam-desktop kernel: [   29.208368] sr 1:0:0:0: Attached scsi generic sg2 type 5
Jul 20 10:03:39 adam-desktop kernel: [   29.208401] scsi 1:0:1:0: Attached scsi generic sg3 type 5
Jul 20 10:03:39 adam-desktop kernel: [   29.212668] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Jul 20 10:03:39 adam-desktop kernel: [   29.212673] Uniform CD-ROM driver Revision: 3.20
Jul 20 10:03:39 adam-desktop kernel: [   29.212736] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 20 10:03:39 adam-desktop kernel: [   29.233394] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Jul 20 10:03:39 adam-desktop kernel: [   29.233447] sr 1:0:1:0: Attached scsi CD-ROM sr1
Jul 20 10:03:39 adam-desktop kernel: [   29.516005] Attempting manual resume
Jul 20 10:03:39 adam-desktop kernel: [   29.516009] swsusp: Resume From Partition 8:2
Jul 20 10:03:39 adam-desktop kernel: [   29.516011] PM: Checking swsusp image.
Jul 20 10:03:39 adam-desktop kernel: [   29.536132] swsusp: Signature found, resuming
Jul 20 10:03:39 adam-desktop kernel: [   29.536210] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
Jul 20 10:03:39 adam-desktop kernel: [   29.536215] swsusp: Basic memory bitmaps created
Jul 20 10:03:39 adam-desktop kernel: [   29.536217] PM: Preparing processes for restore.
Jul 20 10:03:39 adam-desktop kernel: [   29.536218] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jul 20 10:03:39 adam-desktop kernel: [   29.545491] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jul 20 10:03:39 adam-desktop kernel: [   29.545512] PM: Reading swsusp image.
Jul 20 10:03:39 adam-desktop kernel: [   29.552979] Loading image data pages (124893 pages) ...     ^H^H^H^H  0%^H^H^H^H  1%^H^H^H^H  2%^H^H^H^H  3%^H^H^H^H  4%^H^H^H^H  5%^H^H^H^H  6%^H^H^H^H  7%^H^H^H^H  8%^H^H^H^H  9%^H^H^H^H 10%^H^H^H^H 11%^H^H^H^H 12%^H^H^H^H 13%^H^H^H^H 14%^H^H^H^H 15%^H^H^H^H 16%^H^H^H^H 17%^H^H^H^H 18%^H^H^H^H 19%^H^H^H^H 20%^H^H^H^H 21%^H^H^H^H 22%^H^H^H^H 23%^H^H^H^H 24%^H^H^H^H 25%^H^H^H^H 26%^H^H^H^H 27%^H^H^H^H 28%^H^H^H^H 29%^H^H^H^H 30%^H^H^H^H 31%^H^H^H^H 32%^H^H^H^H 33%^H^H^H^H 34%^H^H^H^H 35%^H^H^H^H 36%^H^H^H^H 37%^H^H^H^H 38%^H^H^H^H 39%^H^H^H^H 40%^H^H^H^H 41%^H^H^H^H 42%^H^H^H^H 43%^H^H^H^H 44%^H^H^H^H 45%^H^H^H^H 46%^H^H^H^H 47%^H^H^H^H 48%^H^H^H^H 49%^H^H^H^H 50%^H^H^H^H 51%^H^H^H^H 52%^H^H^H^H 53%^H^H^H^H 54%^H^H^H^H 55%^H^H^H^H 56%^H^H^H^H 57%^H^H^H^H 58%^H^H^H^H 59%^H^H^H^H 60%^H^H^H^H 61%^H^H^H^H 62%^H^H^H^H 63%^H^H^H^H 64%^H^H^H^H 65%^H^H^H^H 66%^H^H^H^H 67%^H^H^H^H 68%^H^H^H^H 69%^H^H^H^H 70%^H^H^H^H 71%^H^H^H^H 72%^H^H^H^H 73%^H^H^H^H 74%^H^H^H^H 75%^H^H^H^H 76%^H^H^H^H 7
Jul 20 10:03:39 adam-desktop kernel: [   53.184966] Read 499572 kbytes in 23.68 seconds (21.09 MB/s)
Jul 20 10:03:39 adam-desktop kernel: [   53.184984] swsusp: Reading resume file was successful
Jul 20 10:03:39 adam-desktop kernel: [   53.184986] Suspending console(s)
Jul 20 10:03:39 adam-desktop kernel: [   53.184999] sd 0:0:1:0: [sdb] Synchronizing SCSI cache
Jul 20 10:03:39 adam-desktop kernel: [   53.185577] Trying to free already-free IRQ 20
Jul 20 10:03:39 adam-desktop kernel: [   53.205793] PnPBIOS: get_dev_node: function not supported on this system
Jul 20 10:03:39 adam-desktop kernel: [   53.205796] serial 00:0a: disable failed
Jul 20 10:03:39 adam-desktop kernel: [   53.205797] suspend_device(): pnp_bus_suspend+0x0/0xa0() returns -5
Jul 20 10:03:39 adam-desktop kernel: [   53.205809] Could not suspend device 00:0a: error -5
Jul 20 10:03:39 adam-desktop kernel: [   53.205889] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jul 20 10:03:39 adam-desktop kernel: [   53.205933] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2880003, writing 2880007)
Jul 20 10:03:39 adam-desktop kernel: [   53.205947] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Jul 20 10:03:39 adam-desktop kernel: [   53.206165] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2a00001, writing 2a00005)
Jul 20 10:03:39 adam-desktop kernel: [   53.206178] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul 20 10:03:39 adam-desktop kernel: [   53.221453] PM: Writing back config space on device 0000:02:08.0 at offset f (was 38080100, writing 38080109)
Jul 20 10:03:39 adam-desktop kernel: [   53.221466] PM: Writing back config space on device 0000:02:08.0 at offset 5 (was 1, writing b801)
Jul 20 10:03:39 adam-desktop kernel: [   53.221470] PM: Writing back config space on device 0000:02:08.0 at offset 4 (was 0, writing feaff000)
Jul 20 10:03:39 adam-desktop kernel: [   53.221474] PM: Writing back config space on device 0000:02:08.0 at offset 3 (was 0, writing 2008)
Jul 20 10:03:39 adam-desktop kernel: [   53.221479] PM: Writing back config space on device 0000:02:08.0 at offset 1 (was 2900000, writing 2900117)
Jul 20 10:03:39 adam-desktop kernel: [   53.255519] sd 0:0:0:0: [sda] Starting disk
Jul 20 10:03:39 adam-desktop kernel: [   53.418197] ata1.00: configured for UDMA/100
Jul 20 10:03:39 adam-desktop kernel: [   53.433737] ata1.01: configured for UDMA/100
Jul 20 10:03:39 adam-desktop kernel: [   53.452223] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Jul 20 10:03:39 adam-desktop kernel: [   53.452238] sd 0:0:0:0: [sda] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   53.452240] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   53.452259] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   53.452280] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 20 10:03:39 adam-desktop kernel: [   53.452291] sd 0:0:1:0: [sdb] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   53.452293] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   53.452310] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   53.452330] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Jul 20 10:03:39 adam-desktop kernel: [   53.452340] sd 0:0:0:0: [sda] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   53.452342] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   53.452359] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   53.452378] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 20 10:03:39 adam-desktop kernel: [   53.452388] sd 0:0:1:0: [sdb] Write Protect is off
Jul 20 10:03:39 adam-desktop kernel: [   53.452390] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jul 20 10:03:39 adam-desktop kernel: [   53.452407] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 20 10:03:39 adam-desktop kernel: [   53.452414] sd 0:0:1:0: [sdb] Starting disk
Jul 20 10:03:39 adam-desktop kernel: [   53.459058] PM: Restore failed, recovering.
Jul 20 10:03:39 adam-desktop kernel: [   53.491463] Restarting tasks ... done.
Jul 20 10:03:39 adam-desktop kernel: [   53.492114] swsusp: Basic memory bitmaps freed
Jul 20 10:03:39 adam-desktop kernel: [   53.492116] PM: Resume from disk failed.
Jul 20 10:03:39 adam-desktop kernel: [   53.506948] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 20 10:03:39 adam-desktop kernel: [   53.506952] EXT3-fs: write access will be enabled during recovery.
Jul 20 10:03:39 adam-desktop kernel: [   53.900115] ata2.00: configured for UDMA/33
Jul 20 10:03:39 adam-desktop kernel: [   54.103825] ata2.01: configured for MWDMA2
Jul 20 10:03:39 adam-desktop kernel: [   57.568548] kjournald starting.  Commit interval 5 seconds
Jul 20 10:03:39 adam-desktop kernel: [   57.568570] EXT3-fs: sda1: orphan cleanup on readonly fs
Jul 20 10:03:39 adam-desktop kernel: [   57.568577] ext3_orphan_cleanup: deleting unreferenced inode 836232
Jul 20 10:03:39 adam-desktop kernel: [   57.568606] ext3_orphan_cleanup: deleting unreferenced inode 559055
Jul 20 10:03:39 adam-desktop kernel: [   57.568615] ext3_orphan_cleanup: deleting unreferenced inode 548870
Jul 20 10:03:39 adam-desktop kernel: [   57.568622] ext3_orphan_cleanup: deleting unreferenced inode 548869
Jul 20 10:03:39 adam-desktop kernel: [   57.568627] ext3_orphan_cleanup: deleting unreferenced inode 548868
Jul 20 10:03:39 adam-desktop kernel: [   57.568632] ext3_orphan_cleanup: deleting unreferenced inode 548867
Jul 20 10:03:39 adam-desktop kernel: [   57.568649] ext3_orphan_cleanup: deleting unreferenced inode 548866
Jul 20 10:03:39 adam-desktop kernel: [   57.568653] EXT3-fs: sda1: 7 orphan inodes deleted
Jul 20 10:03:39 adam-desktop kernel: [   57.568654] EXT3-fs: recovery complete.
Jul 20 10:03:39 adam-desktop kernel: [   57.686556] EXT3-fs: mounted filesystem with ordered data mode.
Jul 20 10:03:39 adam-desktop kernel: [   64.758762] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 20 10:03:39 adam-desktop kernel: [   64.854626] iTCO_vendor_support: vendor-support=0
Jul 20 10:03:39 adam-desktop kernel: [   64.870541] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jul 20 10:03:39 adam-desktop kernel: [   64.919216] Linux agpgart interface v0.102
Jul 20 10:03:39 adam-desktop kernel: [   64.942693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 20 10:03:39 adam-desktop kernel: [   64.958725] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 20 10:03:39 adam-desktop kernel: [   65.026949] agpgart: Detected an Intel 865 Chipset.
Jul 20 10:03:39 adam-desktop kernel: [   65.029739] agpgart: AGP aperture is 64M @ 0xe8000000
Jul 20 10:03:39 adam-desktop kernel: [   65.406420] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
Jul 20 10:03:39 adam-desktop kernel: [   65.436083] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
Jul 20 10:03:39 adam-desktop kernel: [   65.436113] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jul 20 10:03:39 adam-desktop kernel: [   65.633130] Intel 82802 RNG detected
Jul 20 10:03:39 adam-desktop kernel: [   65.844685] nvidia: module license 'NVIDIA' taints kernel.
Jul 20 10:03:39 adam-desktop kernel: [   66.245358] Linux video capture interface: v2.00
Jul 20 10:03:39 adam-desktop kernel: [   66.398462] cx18:  Start initialization, version 1.0.0
Jul 20 10:03:39 adam-desktop kernel: [   66.398529] cx18-0: Initializing card #0
Jul 20 10:03:39 adam-desktop kernel: [   66.398533] cx18-0: Autodetected Hauppauge card
Jul 20 10:03:39 adam-desktop kernel: [   66.398560] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
Jul 20 10:03:39 adam-desktop kernel: [   66.398733] cx18-0: cx23418 revision 01010000 (B)
Jul 20 10:03:39 adam-desktop kernel: [   66.586295] tveeprom 0-0050: Hauppauge model 74041, rev C6B2, serial# 936551
Jul 20 10:03:39 adam-desktop kernel: [   66.586299] tveeprom 0-0050: MAC address is 00-0D-FE-0E-4A-67
Jul 20 10:03:39 adam-desktop kernel: [   66.586302] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
Jul 20 10:03:39 adam-desktop kernel: [   66.586305] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
Jul 20 10:03:39 adam-desktop kernel: [   66.586307] tveeprom 0-0050: audio processor is CX23418 (idx 38)
Jul 20 10:03:39 adam-desktop kernel: [   66.586309] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
Jul 20 10:03:39 adam-desktop kernel: [   66.586311] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
Jul 20 10:03:39 adam-desktop kernel: [   66.586313] cx18-0: Autodetected Hauppauge HVR-1600
Jul 20 10:03:39 adam-desktop kernel: [   66.586316] cx18-0: VBI is not yet supported
Jul 20 10:03:39 adam-desktop kernel: [   66.690444] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
Jul 20 10:03:39 adam-desktop kernel: [   66.690469] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
Jul 20 10:03:39 adam-desktop kernel: [   66.755109] tuner-simple 1-0061: creating new instance
Jul 20 10:03:39 adam-desktop kernel: [   66.755114] tuner-simple 1-0061: type set to 50 (TCL 2002N)
Jul 20 10:03:39 adam-desktop kernel: [   66.756069] cx18-0: Disabled encoder IDX device
Jul 20 10:03:39 adam-desktop kernel: [   66.756115] cx18-0: Registered device video0 for encoder MPEG (2 MB)
Jul 20 10:03:39 adam-desktop kernel: [   66.756118] DVB: registering new adapter (cx18)
Jul 20 10:03:39 adam-desktop kernel: [   66.886027] MXL5005S: Attached at address 0x63
Jul 20 10:03:39 adam-desktop kernel: [   66.886034] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
Jul 20 10:03:39 adam-desktop kernel: [   66.886096] cx18-0: DVB Frontend registered
Jul 20 10:03:39 adam-desktop kernel: [   66.886116] cx18-0: Registered device video32 for encoder YUV (2 MB)
Jul 20 10:03:39 adam-desktop kernel: [   66.886133] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
Jul 20 10:03:39 adam-desktop kernel: [   66.886136] cx18-0: Initialized card #0: Hauppauge HVR-1600
Jul 20 10:03:39 adam-desktop kernel: [   66.886153] cx18:  End initialization
Jul 20 10:03:39 adam-desktop kernel: [   66.886567] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Jul 20 10:03:39 adam-desktop kernel: [   66.887458] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Jul 20 10:03:39 adam-desktop kernel: [   67.313220] intel8x0_measure_ac97_clock: measured 55870 usecs
Jul 20 10:03:39 adam-desktop kernel: [   67.313224] intel8x0: clocking to 48000
Jul 20 10:03:39 adam-desktop kernel: [   68.094355] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
Jul 20 10:03:39 adam-desktop kernel: [   68.191543] lp0: using parport0 (polling).
Jul 20 10:03:39 adam-desktop kernel: [   68.227179] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 20 10:03:39 adam-desktop kernel: [   68.571803] Adding 2947916k swap on /dev/sda2.  Priority:-1 extents:1 across:2947916k
Jul 20 10:03:39 adam-desktop kernel: [   69.257515] EXT3 FS on sda1, internal journal
Jul 20 10:03:39 adam-desktop kernel: [   71.683321] JFS: nTxBlock = 8082, nTxLock = 64662
Jul 20 10:03:39 adam-desktop kernel: [   72.313410] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 20 10:03:39 adam-desktop kernel: [   75.093529] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Jul 20 10:03:39 adam-desktop kernel: [   75.093581] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Jul 20 10:03:39 adam-desktop kernel: [   75.093749] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Jul 20 10:03:39 adam-desktop kernel: [   75.093827] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
Jul 20 10:03:39 adam-desktop NetworkManager: <info>  starting... 
Jul 20 10:03:40 adam-desktop kernel: [   77.099121] NET: Registered protocol family 10
Jul 20 10:03:40 adam-desktop kernel: [   77.099627] lo: Disabled Privacy Extensions
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Found user 'avahi' (UID 112) and group 'avahi' (GID 119).
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Successfully dropped root privileges.
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: avahi-daemon 0.6.22 starting up.
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: WARNING: No NSS support for mDNS detected, consider installing nss-mdns!
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Successfully called chroot().
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Successfully dropped remaining capabilities.
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: No service file found in /etc/avahi/services.
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Network interface enumeration completed.
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Registering HINFO record with values 'I686'/'LINUX'.
Jul 20 10:03:41 adam-desktop avahi-daemon[4591]: Server startup complete. Host name is adam-desktop.local. Local service cookie is 760847080.
Jul 20 10:03:42 adam-desktop apmd[4642]: apmd 3.2.1 interfacing with apm driver 1.16ac and APM BIOS 1.2
Jul 20 10:03:43 adam-desktop mysqld_safe[4744]: started
Jul 20 10:03:43 adam-desktop mysqld[4748]: InnoDB: The log sequence number in ibdata files does not match
Jul 20 10:03:43 adam-desktop mysqld[4748]: InnoDB: the log sequence number in the ib_logfiles!
Jul 20 10:03:43 adam-desktop mysqld[4748]: 080720 10:03:43  InnoDB: Database was not shut down normally!
Jul 20 10:03:43 adam-desktop mysqld[4748]: InnoDB: Starting crash recovery.
Jul 20 10:03:43 adam-desktop mysqld[4748]: InnoDB: Reading tablespace information from the .ibd files...
Jul 20 10:03:43 adam-desktop mysqld[4748]: InnoDB: Restoring possible half-written data pages from the doublewrite
Jul 20 10:03:43 adam-desktop mysqld[4748]: InnoDB: buffer...
Jul 20 10:03:44 adam-desktop mysqld[4748]: 080720 10:03:44  InnoDB: Started; log sequence number 0 54141
Jul 20 10:03:44 adam-desktop mysqld[4748]: 080720 10:03:44 [Note] /usr/sbin/mysqld: ready for connections.
Jul 20 10:03:44 adam-desktop mysqld[4748]: Version: '5.0.51a-3ubuntu5.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4785]: Upgrading MySQL tables if necessary.
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4790]: Looking for 'mysql' in: /usr/bin/mysql
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4790]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4790]: This installation of MySQL is already upgraded to 5.0.51a, use --force if you still need to run mysql_upgrade
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4816]: Checking for insecure root accounts.
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4820]: WARNING: mysql.user contains 3 root accounts without password!
Jul 20 10:03:44 adam-desktop /etc/mysql/debian-start[4821]: Checking for crashed MySQL tables.
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: WARNING: mysqlcheck has found corrupt tables
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: mythconverg.settings
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: warning  : 1 client is using or hasn't closed the table properly
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: 
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]:  Improperly closed tables are also reported if clients are accessing
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]:  the tables *now*. A list of current connections is below.
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: 
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: +----+------------------+-----------+----+---------+------+-------+------------------+
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: | Id | User             | Host      | db | Command | Time | State | Info             |
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: +----+------------------+-----------+----+---------+------+-------+------------------+
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: | 7  | debian-sys-maint | localhost |    | Query   | 0    |       | show processlist |
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: +----+------------------+-----------+----+---------+------+-------+------------------+
Jul 20 10:03:46 adam-desktop /etc/mysql/debian-start[4830]: Uptime: 3  Threads: 1  Questions: 127  Slow queries: 0  Opens: 115  Flush tables: 1  Open tables: 64  Queries per second avg: 42.333
Jul 20 10:03:49 adam-desktop ntpd[4861]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jul 20 10:03:49 adam-desktop ntpd[4862]: precision = 1.000 usec
Jul 20 10:03:49 adam-desktop ntpd[4862]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jul 20 10:03:49 adam-desktop ntpd[4862]: Listening on interface #1 wildcard, ::#123 Disabled
Jul 20 10:03:49 adam-desktop ntpd[4862]: Listening on interface #2 lo, ::1#123 Enabled
Jul 20 10:03:49 adam-desktop ntpd[4862]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Jul 20 10:03:49 adam-desktop ntpd[4862]: kernel time sync status 0040
Jul 20 10:03:49 adam-desktop ntpd[4862]: frequency initialized 13.385 PPM from /var/lib/ntp/ntp.drift
Jul 20 10:03:51 adam-desktop dhcdbd: Started up.
Jul 20 10:03:51 adam-desktop ntpd_initres[4867]: host name not found: ntp.ubuntu.com
Jul 20 10:03:51 adam-desktop ntpd_initres[4867]: couldn't resolve `ntp.ubuntu.com', giving up on it
Jul 20 10:03:52 adam-desktop kernel: [   89.267113] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
Jul 20 10:03:53 adam-desktop kernel: [   89.814287] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
Jul 20 10:03:53 adam-desktop kernel: [   89.819390] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
Jul 20 10:03:53 adam-desktop kernel: [   89.823981] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
Jul 20 10:03:53 adam-desktop kernel: [   89.824006] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 158332 bytes)
Jul 20 10:03:53 adam-desktop kernel: [   89.824010] cx18-0: Did you put the firmware in the hotplug firmware directory?
Jul 20 10:03:53 adam-desktop kernel: [   89.824012] cx18-0: Retry loading firmware
Jul 20 10:03:53 adam-desktop kernel: [   89.877604] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
Jul 20 10:03:53 adam-desktop kernel: [   90.379620] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
Jul 20 10:03:53 adam-desktop kernel: [   90.385167] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
Jul 20 10:03:53 adam-desktop kernel: [   90.389725] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
Jul 20 10:03:53 adam-desktop kernel: [   90.389747] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 158332 bytes)
Jul 20 10:03:53 adam-desktop kernel: [   90.389751] cx18-0: Did you put the firmware in the hotplug firmware directory?
Jul 20 10:03:53 adam-desktop kernel: [   90.389755] cx18-0: Failed to initialize on minor 0
Jul 20 10:03:53 adam-desktop kernel: [   90.390617] cx18-0: Failed to initialize on minor 0
Jul 20 10:03:53 adam-desktop kernel: [   90.393253] cx18-0: Failed to initialize on minor 24
Jul 20 10:03:53 adam-desktop kernel: [   90.397699] cx18-0: Failed to initialize on minor 32
Jul 20 10:03:53 adam-desktop kernel: [   90.528472] cx18-0: Failed to initialize on minor 0
Jul 20 10:03:54 adam-desktop kernel: [   90.982095] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 20 10:03:54 adam-desktop kernel: [   90.983105] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Jul 20 10:03:54 adam-desktop kernel: [   90.985363] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'e100'. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Deactivating device eth0. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul 20 10:03:54 adam-desktop NetworkManager: <debug> [1216562634.380173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_NR_7700A'). 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jul 20 10:03:54 adam-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) started... 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jul 20 10:03:54 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jul 20 10:03:55 adam-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jul 20 10:03:55 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jul 20 10:03:55 adam-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jul 20 10:03:55 adam-desktop gdm[5197]: WARNING: Didn't understand `' (expected true or false) 
Jul 20 10:03:56 adam-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jul 20 10:03:56 adam-desktop kernel: [   93.409628] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 20 10:03:56 adam-desktop kernel: [   93.409645] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 20 10:03:56 adam-desktop kernel: [   93.411235] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 20 10:03:57 adam-desktop kernel: [   93.684990] NET: Registered protocol family 17
Jul 20 10:03:59 adam-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jul 20 10:03:59 adam-desktop dhclient: DHCPOFFER of 192.168.15.103 from 192.168.15.1
Jul 20 10:03:59 adam-desktop dhclient: DHCPREQUEST of 192.168.15.103 on eth0 to 255.255.255.255 port 67
Jul 20 10:03:59 adam-desktop dhclient: DHCPACK of 192.168.15.103 from 192.168.15.1
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.103.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: New relevant interface eth0.IPv4 for mDNS.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Registering new address record for 192.168.15.103 on eth0.IPv4.
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jul 20 10:03:59 adam-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 20 10:03:59 adam-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 20 10:03:59 adam-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>    address 192.168.15.103 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>    netmask 255.255.255.0 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>    broadcast 192.168.15.255 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>    gateway 192.168.15.1 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>    nameserver 192.168.15.1 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>    hostname 'adam-desktop' 
Jul 20 10:03:59 adam-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jul 20 10:03:59 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jul 20 10:03:59 adam-desktop dhclient: bound to 192.168.15.103 -- renewal in 41075 seconds.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Withdrawing address record for 192.168.15.103 on eth0.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.15.103.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.15.103.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: New relevant interface eth0.IPv4 for mDNS.
Jul 20 10:03:59 adam-desktop avahi-daemon[4591]: Registering new address record for 192.168.15.103 on eth0.IPv4.
Jul 20 10:04:00 adam-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Jul 20 10:04:00 adam-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jul 20 10:04:00 adam-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jul 20 10:04:00 adam-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jul 20 10:04:00 adam-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul 20 10:04:00 adam-desktop ntpd[4862]: ntpd exiting on signal 15
Jul 20 10:04:00 adam-desktop ntpdate[5338]: step time server 91.189.94.4 offset 0.655806 sec
Jul 20 10:04:01 adam-desktop ntpd[5409]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jul 20 10:04:01 adam-desktop ntpd[5410]: precision = 1.000 usec
Jul 20 10:04:01 adam-desktop ntpd[5410]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jul 20 10:04:01 adam-desktop ntpd[5410]: Listening on interface #1 wildcard, ::#123 Disabled
Jul 20 10:04:01 adam-desktop ntpd[5410]: Listening on interface #2 lo, ::1#123 Enabled
Jul 20 10:04:01 adam-desktop ntpd[5410]: bind() fd 19, family 10, port 123, scope 2, addr fe80::207:e9ff:fe64:968f, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Jul 20 10:04:01 adam-desktop ntpd[5410]: unable to create socket on eth0 (3) for fe80::207:e9ff:fe64:968f#123
Jul 20 10:04:01 adam-desktop ntpd[5410]: failed to initialize interface for address fe80::207:e9ff:fe64:968f
Jul 20 10:04:01 adam-desktop ntpd[5410]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jul 20 10:04:01 adam-desktop ntpd[5410]: Listening on interface #5 eth0, 192.168.15.103#123 Enabled
Jul 20 10:04:01 adam-desktop ntpd[5410]: kernel time sync status 0040
Jul 20 10:04:01 adam-desktop ntpd[5410]: frequency initialized 13.385 PPM from /var/lib/ntp/ntp.drift
Jul 20 10:04:02 adam-desktop avahi-daemon[4591]: Registering new address record for fe80::207:e9ff:fe64:968f on eth0.*.
Jul 20 10:04:02 adam-desktop ntpd[5410]: Listening on interface #6 eth0, fe80::207:e9ff:fe64:968f#123 Enabled
Jul 20 10:04:05 adam-desktop /usr/sbin/cron[5570]: (CRON) INFO (pidfile fd = 3)
Jul 20 10:04:05 adam-desktop /usr/sbin/cron[5571]: (CRON) STARTUP (fork ok)
Jul 20 10:04:05 adam-desktop /usr/sbin/cron[5571]: (CRON) INFO (Running @reboot jobs)
Jul 20 10:04:11 adam-desktop kernel: [  107.121857] eth0: no IPv6 routers present
Jul 20 10:04:11 adam-desktop kernel: [  107.199721] cx18-0: Failed to initialize on minor 24
Jul 20 10:04:11 adam-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jul 20 10:04:11 adam-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul 20 10:04:28 adam-desktop kernel: [  124.238088] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:04:28 adam-desktop kernel: [  124.238093] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:05:18 adam-desktop kernel: [  174.726792] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:18 adam-desktop kernel: [  174.727085] cx18-0: Failed to initialize on minor 24
Jul 20 10:05:18 adam-desktop kernel: [  174.727297] cx18-0: Failed to initialize on minor 32
Jul 20 10:05:18 adam-desktop kernel: [  174.768232] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:18 adam-desktop kernel: [  174.784271] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:18 adam-desktop kernel: [  174.791590] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:18 adam-desktop kernel: [  174.795488] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:18 adam-desktop kernel: [  174.795737] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:19 adam-desktop kernel: [  174.871262] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:19 adam-desktop kernel: [  174.878471] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:19 adam-desktop kernel: [  174.880816] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:19 adam-desktop kernel: [  174.881063] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:28 adam-desktop kernel: [  183.979672] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:05:28 adam-desktop kernel: [  183.979678] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:05:34 adam-desktop kernel: [  190.141325] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.141604] cx18-0: Failed to initialize on minor 24
Jul 20 10:05:34 adam-desktop kernel: [  190.141777] cx18-0: Failed to initialize on minor 32
Jul 20 10:05:34 adam-desktop kernel: [  190.170019] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.182791] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.189931] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.193882] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.194132] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.269776] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.276933] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.279374] cx18-0: Failed to initialize on minor 0
Jul 20 10:05:34 adam-desktop kernel: [  190.279625] cx18-0: Failed to initialize on minor 0
Jul 20 10:06:07 adam-desktop kernel: [  222.943319] cx18-0: Failed to initialize on minor 0
Jul 20 10:06:31 adam-desktop kernel: [  246.744793] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:06:31 adam-desktop kernel: [  246.744799] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:06:35 adam-desktop kernel: [  251.135732] cx18-0: Failed to initialize on minor 0
Jul 20 10:06:50 adam-desktop kernel: [  266.418699] cx18-0: Failed to initialize on minor 0
Jul 20 10:07:03 adam-desktop kernel: [  279.065020] cx18-0: Failed to initialize on minor 0
Jul 20 10:07:08 adam-desktop kernel: [  283.984845] cx18-0: Failed to initialize on minor 0
Jul 20 10:07:17 adam-desktop kernel: [  293.022618] cx18-0: Failed to initialize on minor 0
Jul 20 10:08:05 adam-desktop kernel: [  340.466755] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:08:05 adam-desktop kernel: [  340.466761] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:08:18 adam-desktop ntpd[5410]: synchronized to 91.189.94.4, stratum 2
Jul 20 10:08:18 adam-desktop ntpd[5410]: kernel time sync status change 0001
Jul 20 10:09:01 adam-desktop /USR/SBIN/CRON[6043]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul 20 10:09:18 adam-desktop kernel: [  413.280018] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:09:18 adam-desktop kernel: [  413.280024] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:10:01 adam-desktop /USR/SBIN/CRON[6083]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Jul 20 10:12:08 adam-desktop kernel: [  583.680274] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:12:08 adam-desktop kernel: [  583.680280] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:12:11 adam-desktop kernel: [  586.518434] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Jul 20 10:12:11 adam-desktop kernel: [  586.518440] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Jul 20 10:12:11 adam-desktop kernel: [  586.633977] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Jul 20 10:12:11 adam-desktop kernel: [  586.633982] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Jul 20 10:13:24 adam-desktop kernel: [  658.711457] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:13:24 adam-desktop kernel: [  658.711463] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:14:28 adam-desktop kernel: [  723.375548] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:14:28 adam-desktop kernel: [  723.375554] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:17:01 adam-desktop /USR/SBIN/CRON[6107]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 20 10:17:06 adam-desktop kernel: [  880.758267] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:17:06 adam-desktop kernel: [  880.758273] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:17:08 adam-desktop kernel: [  883.037907] cx18-0: Failed to initialize on minor 0
Jul 20 10:17:39 adam-desktop kernel: [  913.141526] cx18-0: Failed to initialize on minor 0
Jul 20 10:18:10 adam-desktop kernel: [  944.713777] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:18:10 adam-desktop kernel: [  944.713783] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:18:18 adam-desktop kernel: [  952.129569] cx18-0: Failed to initialize on minor 0
Jul 20 10:19:23 adam-desktop kernel: [ 1017.534604] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:19:23 adam-desktop kernel: [ 1017.534610] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:19:59 adam-desktop kernel: [ 1053.581115] cx18-0: Failed to initialize on minor 0
Jul 20 10:19:59 adam-desktop kernel: [ 1053.581413] cx18-0: Failed to initialize on minor 24
Jul 20 10:19:59 adam-desktop kernel: [ 1053.581589] cx18-0: Failed to initialize on minor 32
Jul 20 10:19:59 adam-desktop kernel: [ 1053.616254] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:01 adam-desktop /USR/SBIN/CRON[6164]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Jul 20 10:20:21 adam-desktop kernel: [ 1075.589791] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:21 adam-desktop kernel: [ 1075.590062] cx18-0: Failed to initialize on minor 24
Jul 20 10:20:21 adam-desktop kernel: [ 1075.590235] cx18-0: Failed to initialize on minor 32
Jul 20 10:20:21 adam-desktop kernel: [ 1075.622214] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:23 adam-desktop kernel: [ 1076.996318] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:20:23 adam-desktop kernel: [ 1076.996324] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:20:31 adam-desktop kernel: [ 1085.387304] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:31 adam-desktop kernel: [ 1085.394867] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:33 adam-desktop kernel: [ 1087.348274] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:33 adam-desktop kernel: [ 1087.355714] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:34 adam-desktop kernel: [ 1088.362012] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:34 adam-desktop kernel: [ 1088.369423] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:35 adam-desktop kernel: [ 1088.743130] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:35 adam-desktop kernel: [ 1088.750627] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:35 adam-desktop kernel: [ 1089.047601] cx18-0: Failed to initialize on minor 0
Jul 20 10:20:35 adam-desktop kernel: [ 1089.055012] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:23 adam-desktop kernel: [ 1136.956933] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:21:23 adam-desktop kernel: [ 1136.956939] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:21:32 adam-desktop kernel: [ 1146.272349] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:32 adam-desktop kernel: [ 1146.272630] cx18-0: Failed to initialize on minor 24
Jul 20 10:21:32 adam-desktop kernel: [ 1146.272800] cx18-0: Failed to initialize on minor 32
Jul 20 10:21:32 adam-desktop kernel: [ 1146.312782] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:35 adam-desktop kernel: [ 1148.692466] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:35 adam-desktop kernel: [ 1148.692736] cx18-0: Failed to initialize on minor 24
Jul 20 10:21:35 adam-desktop kernel: [ 1148.692942] cx18-0: Failed to initialize on minor 32
Jul 20 10:21:35 adam-desktop kernel: [ 1148.721185] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:37 adam-desktop kernel: [ 1151.536475] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:37 adam-desktop kernel: [ 1151.536751] cx18-0: Failed to initialize on minor 24
Jul 20 10:21:37 adam-desktop kernel: [ 1151.536924] cx18-0: Failed to initialize on minor 32
Jul 20 10:21:38 adam-desktop kernel: [ 1151.565697] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:40 adam-desktop kernel: [ 1153.661524] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:40 adam-desktop kernel: [ 1153.661797] cx18-0: Failed to initialize on minor 24
Jul 20 10:21:40 adam-desktop kernel: [ 1153.661968] cx18-0: Failed to initialize on minor 32
Jul 20 10:21:40 adam-desktop kernel: [ 1153.690315] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:44 adam-desktop kernel: [ 1158.360462] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:44 adam-desktop kernel: [ 1158.368828] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:51 adam-desktop kernel: [ 1164.868850] cx18-0: Failed to initialize on minor 0
Jul 20 10:21:56 adam-desktop kernel: [ 1169.997841] cx18-0: Failed to initialize on minor 0
Jul 20 10:22:02 adam-desktop kernel: [ 1176.173623] cx18-0: Failed to initialize on minor 0
Jul 20 10:22:08 adam-desktop kernel: [ 1182.346113] cx18-0: Failed to initialize on minor 0
Jul 20 10:22:23 adam-desktop kernel: [ 1196.599881] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:22:23 adam-desktop kernel: [ 1196.599888] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:23:08 adam-desktop kernel: [ 1241.874364] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1241.874660] cx18-0: Failed to initialize on minor 24
Jul 20 10:23:08 adam-desktop kernel: [ 1241.874841] cx18-0: Failed to initialize on minor 32
Jul 20 10:23:08 adam-desktop kernel: [ 1241.910335] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1241.926639] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1241.933752] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1241.937640] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1241.937900] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1242.014065] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1242.021209] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1242.023474] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:08 adam-desktop kernel: [ 1242.023720] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:22 adam-desktop kernel: [ 1256.140286] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:23:22 adam-desktop kernel: [ 1256.140292] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:23:54 adam-desktop kernel: [ 1287.654969] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.655664] cx18-0: Failed to initialize on minor 24
Jul 20 10:23:54 adam-desktop kernel: [ 1287.655910] cx18-0: Failed to initialize on minor 32
Jul 20 10:23:54 adam-desktop kernel: [ 1287.683881] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.696152] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.703335] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.705771] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.706023] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.779272] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.786470] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.788821] cx18-0: Failed to initialize on minor 0
Jul 20 10:23:54 adam-desktop kernel: [ 1287.789105] cx18-0: Failed to initialize on minor 0
Jul 20 10:24:22 adam-desktop kernel: [ 1315.803499] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:24:22 adam-desktop kernel: [ 1315.803505] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:24:46 adam-desktop kernel: [ 1339.430737] cx18-0: Failed to initialize on minor 0
Jul 20 10:24:46 adam-desktop kernel: [ 1339.431018] cx18-0: Failed to initialize on minor 24
Jul 20 10:24:46 adam-desktop kernel: [ 1339.431190] cx18-0: Failed to initialize on minor 32
Jul 20 10:24:46 adam-desktop kernel: [ 1339.470918] cx18-0: Failed to initialize on minor 0
Jul 20 10:25:22 adam-desktop kernel: [ 1375.597328] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:25:22 adam-desktop kernel: [ 1375.597334] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:25:55 adam-desktop kernel: [ 1408.481857] cx18-0: Failed to initialize on minor 0
Jul 20 10:26:03 adam-desktop kernel: [ 1416.612085] cx18-0: Failed to initialize on minor 0
Jul 20 10:26:04 adam-desktop kernel: [ 1417.933804] cx18-0: Failed to initialize on minor 0
Jul 20 10:26:22 adam-desktop kernel: [ 1435.568076] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:26:22 adam-desktop kernel: [ 1435.568082] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:27:22 adam-desktop kernel: [ 1495.042376] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:27:22 adam-desktop kernel: [ 1495.042382] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:28:22 adam-desktop kernel: [ 1554.785184] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:28:22 adam-desktop kernel: [ 1554.785190] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:28:57 adam-desktop kernel: [ 1589.916085] cx18-0: Failed to initialize on minor 0
Jul 20 10:29:22 adam-desktop kernel: [ 1614.609478] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:29:22 adam-desktop kernel: [ 1614.609484] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:30:01 adam-desktop /USR/SBIN/CRON[6274]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Jul 20 10:30:21 adam-desktop kernel: [ 1673.901861] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:30:21 adam-desktop kernel: [ 1673.901867] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:31:05 adam-desktop kernel: [ 1717.577938] cx18-0: Failed to initialize on minor 0
Jul 20 10:31:12 adam-desktop kernel: [ 1724.382446] cx18-0: Failed to initialize on minor 0
Jul 20 10:31:23 adam-desktop kernel: [ 1735.454079] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:31:23 adam-desktop kernel: [ 1735.454085] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:32:51 adam-desktop kernel: [ 1823.422160] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:32:51 adam-desktop kernel: [ 1823.422166] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:34:14 adam-desktop kernel: [ 1906.145015] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:34:14 adam-desktop kernel: [ 1906.145021] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:35:24 adam-desktop kernel: [ 1975.708588] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:35:24 adam-desktop kernel: [ 1975.708594] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jul 20 10:36:24 adam-desktop kernel: [ 2036.081771] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jul 20 10:36:24 adam-desktop kernel: [ 2036.081777] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
```

and mysqld log:

```
$ cat /var/log/mysqld/mysqld.log
cat: /var/log/mysqld/mysqld.log: No such file or directory
```

And, for completeness, the full dmesg:

```
$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] 191MB HIGHMEM available.
[    0.000000] 832MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 261936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   212992
[    0.000000]   HighMem    212992 ->   261936
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261936
[    0.000000] On node 0 totalpages: 261936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1632 pages used for memmap
[    0.000000]   Normal zone: 207264 pages, LIFO batch:31
[    0.000000]   HighMem zone: 382 pages used for memmap
[    0.000000]   HighMem zone: 48562 pages, LIFO batch:15
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:  Product ID: Springdale-G APIC at: 0xFEE00000
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259890
[    0.000000] Kernel command line: root=UUID=2e916da9-0ff1-4f33-a24d-68dfe6e67644 ro quiet splash acpi=off apm=power_off vmalloc=192M pci=nommconf
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3059.043 MHz processor.
[   23.816138] Console: colour VGA+ 80x25
[   23.816141] console [tty0] enabled
[   23.816755] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.817341] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.848481] Memory: 1026272k/1047744k available (2177k kernel code, 20596k reserved, 1006k data, 368k init, 195776k highmem)
[   23.848491] virtual kernel memory layout:
[   23.848492]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.848493]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.848494]     vmalloc : 0xf4800000 - 0xff7fe000   ( 175 MB)
[   23.848495]     lowmem  : 0xc0000000 - 0xf4000000   ( 832 MB)
[   23.848495]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   23.848496]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   23.848497]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   23.848500] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.848551] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   23.928399] Calibrating delay using timer specific routine.. 6123.14 BogoMIPS (lpj=12246283)
[   23.928433] Security Framework initialized
[   23.928443] SELinux:  Disabled at boot.
[   23.928460] AppArmor: AppArmor initialized
[   23.928465] Failure registering capabilities with primary security module.
[   23.928474] Mount-cache hash table entries: 512
[   23.928628] Initializing cgroup subsys ns
[   23.928633] Initializing cgroup subsys cpuacct
[   23.928645] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   23.928658] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   23.928661] CPU: L2 cache: 512K
[   23.928663] CPU: Physical Processor ID: 0
[   23.928665] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   23.928678] Compat vDSO mapped to ffffe000.
[   23.928692] Checking 'hlt' instruction... OK.
[   23.944737] SMP alternatives: switching to UP code
[   23.946192] Freeing SMP alternatives: 11k freed
[   23.946316] Early unpacking initramfs... done
[   24.229319] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
[   24.229358] Total of 1 processors activated (6123.14 BogoMIPS).
[   24.229416] ExtINT not setup in hardware but reported by MP table
[   24.229492] ENABLING IO-APIC IRQs
[   24.229680] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   24.483243] Brought up 1 CPUs
[   24.483265] CPU0 attaching sched-domain:
[   24.483268]  domain 0: span 01
[   24.483270]   groups: 01
[   24.483462] net_namespace: 64 bytes
[   24.483473] Booting paravirtualized kernel on bare hardware
[   24.483968] Time: 14:02:48  Date: 07/20/08
[   24.483996] NET: Registered protocol family 16
[   24.484218] EISA bus registered
[   24.485602] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   24.485604] PCI: Using configuration type 1
[   24.485623] Setting up standard PCI resources
[   24.496571] ACPI: Interpreter disabled.
[   24.496575] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.496608] pnp: PnP ACPI: disabled
[   24.496611] PnPBIOS: Scanning system for PnP BIOS support...
[   24.496622] PnPBIOS: Found PnP BIOS installation structure at 0xc00f3450
[   24.496625] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x3a6a, dseg 0xf0000
[   24.497154] PNPBIOS fault.. attempting recovery.
[   24.497204] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   24.497249] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   24.497295] PnPBIOS: Check with your vendor for an updated BIOS
[   24.497338] PnPBIOS: get_dev_node: unexpected status 0x37
[   24.497381] PnPBIOS: 12 nodes reported by PnP BIOS; 12 recorded by driver
[   24.497616] PCI: Probing PCI hardware
[   24.497619] PCI: Probing PCI hardware (bus 00)
[   24.498087] Force enabled HPET at base address 0xfed00000
[   24.498094] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   24.498098] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   24.498632] PCI: Transparent bridge - 0000:00:1e.0
[   24.499374] PCI: Using IRQ router PIIX/ICH [8086/24d0] at 0000:00:1f.0
[   24.499384] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 16
[   24.499388] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 19
[   24.499391] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 18
[   24.499395] PCI->APIC IRQ transform: 0000:00:1d.3[A] -> IRQ 16
[   24.499399] PCI->APIC IRQ transform: 0000:00:1d.7[D] -> IRQ 23
[   24.499404] PCI->APIC IRQ transform: 0000:00:1f.1[A] -> IRQ 18
[   24.499408] PCI->APIC IRQ transform: 0000:00:1f.2[A] -> IRQ 18
[   24.499411] PCI->APIC IRQ transform: 0000:00:1f.3[B] -> IRQ 17
[   24.499414] PCI->APIC IRQ transform: 0000:00:1f.5[B] -> IRQ 17
[   24.499418] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   24.499421] PCI->APIC IRQ transform: 0000:02:03.0[A] -> IRQ 19
[   24.499424] PCI->APIC IRQ transform: 0000:02:04.0[A] -> IRQ 18
[   24.499428] PCI->APIC IRQ transform: 0000:02:08.0[A] -> IRQ 20
[   24.511228] NET: Registered protocol family 8
[   24.511231] NET: Registered protocol family 20
[   24.511343] hpet clockevent registered
[   24.511349] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.511353] hpet0: 3 64-bit timers, 14318180 Hz
[   24.512392] AppArmor: AppArmor Filesystem Enabled
[   24.512434] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   24.512437] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   24.512439] system 00:00: iomem range 0xe6000-0xfffff could not be reserved
[   24.512442] system 00:00: iomem range 0x100000-0x3ff2ffff could not be reserved
[   24.512444] system 00:00: iomem range 0x3ff30000-0x3ff3ffff could not be reserved
[   24.512447] system 00:00: iomem range 0x3ff40000-0x3ffeffff could not be reserved
[   24.512449] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   24.512452] system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
[   24.512454] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   24.512887] PCI: Bridge: 0000:00:01.0
[   24.512889]   IO window: disabled.
[   24.512893]   MEM window: ec500000-ee5fffff
[   24.512897]   PREFETCH window: d4300000-e42fffff
[   24.512902] PCI: Bridge: 0000:00:1e.0
[   24.512905]   IO window: b000-bfff
[   24.512910]   MEM window: ee600000-feafffff
[   24.512913]   PREFETCH window: e4300000-e43fffff
[   24.512932] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.512942] NET: Registered protocol family 2
[   24.515127] Time: tsc clocksource has been installed.
[   24.547141] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.547471] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.548360] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.548877] TCP: Hash tables configured (established 131072 bind 65536)
[   24.548882] TCP reno registered
[   24.559220] checking if image is initramfs... it is
[   25.014037] Switched to high resolution mode on CPU 0
[   25.113096] Freeing initrd memory: 7460k freed
[   25.113699] audit: initializing netlink socket (disabled)
[   25.113716] audit(1216562568.160:1): initialized
[   25.113918] highmem bounce pool size: 64 pages
[   25.115744] VFS: Disk quotas dquot_6.5.1
[   25.115832] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.116015] io scheduler noop registered
[   25.116017] io scheduler anticipatory registered
[   25.116019] io scheduler deadline registered
[   25.116032] io scheduler cfq registered (default)
[   25.116125] Boot video device is 0000:01:00.0
[   25.116130] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   25.116373] isapnp: Scanning for PnP cards...
[   25.469530] isapnp: No Plug & Play device found
[   25.499318] Real Time Clock Driver v1.12ac
[   25.499396] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.499511] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.500300] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.501103] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.501171] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.501280] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.504174] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.504179] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.505221] mice: PS/2 mouse device common for all mice
[   25.505350] EISA: Probing bus 0 at eisa.0
[   25.505383] EISA: Detected 0 cards.
[   25.505386] cpuidle: using governor ladder
[   25.505389] cpuidle: using governor menu
[   25.505480] NET: Registered protocol family 1
[   25.505510] Using IPI No-Shortcut mode
[   25.505540] registered taskstats version 1
[   25.505622]   Magic number: 0:953:30
[   25.505630]   hash matches device ttydd
[   25.505718] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.505720] EDD information not available.
[   25.506106] Freeing unused kernel memory: 368k freed
[   25.532831] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.712602] fuse init (API version 7.9)
[   26.746819] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   26.959852] usbcore: registered new interface driver usbfs
[   26.959878] usbcore: registered new interface driver hub
[   26.969352] usbcore: registered new device driver usb
[   26.981830] USB Universal Host Controller Interface driver v3.0
[   26.981903] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.981907] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.982188] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.982217] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   26.982352] usb usb1: configuration #1 chosen from 1 choice
[   26.982375] hub 1-0:1.0: USB hub found
[   26.982382] hub 1-0:1.0: 2 ports detected
[   27.039624] SCSI subsystem initialized
[   27.085375] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.085380] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.085407] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.085434] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[   27.085540] usb usb2: configuration #1 chosen from 1 choice
[   27.085563] hub 2-0:1.0: USB hub found
[   27.085569] hub 2-0:1.0: 2 ports detected
[   27.096745] libata version 3.00 loaded.
[   27.104167] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   27.104171] e100: Copyright(c) 1999-2006 Intel Corporation
[   27.189175] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.189181] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.189205] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.189231] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   27.189350] usb usb3: configuration #1 chosen from 1 choice
[   27.189373] hub 3-0:1.0: USB hub found
[   27.189379] hub 3-0:1.0: 2 ports detected
[   27.252939] Floppy drive(s): fd0 is 1.44M
[   27.272577] FDC 0 is a post-1991 82077
[   27.292933] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.292939] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.292963] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.292987] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   27.293095] usb usb4: configuration #1 chosen from 1 choice
[   27.293118] hub 4-0:1.0: USB hub found
[   27.293125] hub 4-0:1.0: 2 ports detected
[   27.396794] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.396800] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.396831] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.400737] ehci_hcd 0000:00:1d.7: debug port 1
[   27.400743] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.400752] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[   27.416509] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.416633] usb usb5: configuration #1 chosen from 1 choice
[   27.416659] hub 5-0:1.0: USB hub found
[   27.416666] hub 5-0:1.0: 8 ports detected
[   27.543678] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:07:e9:64:96:8f
[   27.543699] ata_piix 0000:00:1f.1: version 2.12
[   27.543713] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   27.543758] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.545539] scsi0 : ata_piix
[   27.546490] scsi1 : ata_piix
[   27.546542] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   27.546545] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   27.716997] ata1.00: ATA-5: WDC WD400BB-53AUA1, 18.20D18, max UDMA/100
[   27.717002] ata1.00: 78165360 sectors, multi 16: LBA 
[   27.723063] ata1.01: ATA-7: WDC WD5000AAJB-00UHA0, 07.01N01, max UDMA/100
[   27.723066] ata1.01: 976773168 sectors, multi 16: LBA48 
[   27.736917] ata1.00: configured for UDMA/100
[   27.752195] ata1.01: configured for UDMA/100
[   28.274814] ata2.00: ATAPI: MATSHITA CR-594, YS0M, max UDMA/33
[   28.274837] ata2.01: ATAPI: _NEC NR-7700A, 1.23, max MWDMA2
[   28.446356] ata2.00: configured for UDMA/33
[   28.650078] ata2.01: configured for MWDMA2
[   28.650202] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-53AU 18.2 PQ: 0 ANSI: 5
[   28.650627] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAJB-0 07.0 PQ: 0 ANSI: 5
[   28.653132] scsi 1:0:0:0: CD-ROM            MATSHITA CD-ROM CR-594    YS0M PQ: 0 ANSI: 5
[   28.657845] scsi 1:0:1:0: CD-ROM            _NEC     NR-7700A         1.23 PQ: 0 ANSI: 5
[   28.657916] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   28.657972] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.658317] scsi2 : ata_piix
[   28.658484] scsi3 : ata_piix
[   28.658516] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[   28.658519] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[   29.008521] Driver 'sd' needs updating - please use bus_type methods
[   29.008612] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   29.008626] sd 0:0:0:0: [sda] Write Protect is off
[   29.008628] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.008648] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   29.008697] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   29.008708] sd 0:0:0:0: [sda] Write Protect is off
[   29.008710] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.008728] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   29.008732]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   29.172267]  sda1 sda2
[   29.195823] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.196363] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.196377] sd 0:0:1:0: [sdb] Write Protect is off
[   29.196380] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.196399] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.196461] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.196472] sd 0:0:1:0: [sdb] Write Protect is off
[   29.196475] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.196493] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.196497]  sdb: sdb1
[   29.198924] sd 0:0:1:0: [sdb] Attached SCSI disk
[   29.208330] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.208351] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   29.208368] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   29.208401] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   29.212668] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   29.212673] Uniform CD-ROM driver Revision: 3.20
[   29.212736] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.233394] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   29.233447] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   29.516005] Attempting manual resume
[   29.516009] swsusp: Resume From Partition 8:2
[   29.516011] PM: Checking swsusp image.
[   29.536132] swsusp: Signature found, resuming
[   29.536210] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
[   29.536215] swsusp: Basic memory bitmaps created
[   29.536217] PM: Preparing processes for restore.
[   29.536218] Freezing user space processes ... (elapsed 0.00 seconds) done.
[   29.545491] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[   29.545512] PM: Reading swsusp image.
[   29.552979] Loading image data pages (124893 pages) ... done
[   53.184966] Read 499572 kbytes in 23.68 seconds (21.09 MB/s)
[   53.184984] swsusp: Reading resume file was successful
[   53.184986] Suspending console(s)
[   53.184999] sd 0:0:1:0: [sdb] Synchronizing SCSI cache
[   53.185577] Trying to free already-free IRQ 20
[   53.205793] PnPBIOS: get_dev_node: function not supported on this system
[   53.205796] serial 00:0a: disable failed
[   53.205797] suspend_device(): pnp_bus_suspend+0x0/0xa0() returns -5
[   53.205809] Could not suspend device 00:0a: error -5
[   53.205889] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   53.205933] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2880003, writing 2880007)
[   53.205947] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   53.206165] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2a00001, writing 2a00005)
[   53.206178] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   53.221453] PM: Writing back config space on device 0000:02:08.0 at offset f (was 38080100, writing 38080109)
[   53.221466] PM: Writing back config space on device 0000:02:08.0 at offset 5 (was 1, writing b801)
[   53.221470] PM: Writing back config space on device 0000:02:08.0 at offset 4 (was 0, writing feaff000)
[   53.221474] PM: Writing back config space on device 0000:02:08.0 at offset 3 (was 0, writing 2008)
[   53.221479] PM: Writing back config space on device 0000:02:08.0 at offset 1 (was 2900000, writing 2900117)
[   53.255519] sd 0:0:0:0: [sda] Starting disk
[   53.418197] ata1.00: configured for UDMA/100
[   53.433737] ata1.01: configured for UDMA/100
[   53.452223] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   53.452238] sd 0:0:0:0: [sda] Write Protect is off
[   53.452240] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   53.452259] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   53.452280] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   53.452291] sd 0:0:1:0: [sdb] Write Protect is off
[   53.452293] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   53.452310] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.452330] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   53.452340] sd 0:0:0:0: [sda] Write Protect is off
[   53.452342] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   53.452359] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   53.452378] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   53.452388] sd 0:0:1:0: [sdb] Write Protect is off
[   53.452390] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   53.452407] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.452414] sd 0:0:1:0: [sdb] Starting disk
[   53.459058] PM: Restore failed, recovering.
[   53.491463] Restarting tasks ... done.
[   53.492114] swsusp: Basic memory bitmaps freed
[   53.492116] PM: Resume from disk failed.
[   53.506948] EXT3-fs: INFO: recovery required on readonly filesystem.
[   53.506952] EXT3-fs: write access will be enabled during recovery.
[   53.900115] ata2.00: configured for UDMA/33
[   54.103825] ata2.01: configured for MWDMA2
[   57.568548] kjournald starting.  Commit interval 5 seconds
[   57.568570] EXT3-fs: sda1: orphan cleanup on readonly fs
[   57.568577] ext3_orphan_cleanup: deleting unreferenced inode 836232
[   57.568606] ext3_orphan_cleanup: deleting unreferenced inode 559055
[   57.568615] ext3_orphan_cleanup: deleting unreferenced inode 548870
[   57.568622] ext3_orphan_cleanup: deleting unreferenced inode 548869
[   57.568627] ext3_orphan_cleanup: deleting unreferenced inode 548868
[   57.568632] ext3_orphan_cleanup: deleting unreferenced inode 548867
[   57.568649] ext3_orphan_cleanup: deleting unreferenced inode 548866
[   57.568653] EXT3-fs: sda1: 7 orphan inodes deleted
[   57.568654] EXT3-fs: recovery complete.
[   57.686556] EXT3-fs: mounted filesystem with ordered data mode.
[   64.758762] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   64.854626] iTCO_vendor_support: vendor-support=0
[   64.870541] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   64.919216] Linux agpgart interface v0.102
[   64.942693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.958725] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.026949] agpgart: Detected an Intel 865 Chipset.
[   65.029739] agpgart: AGP aperture is 64M @ 0xe8000000
[   65.406420] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   65.436083] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   65.436113] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   65.633130] Intel 82802 RNG detected
[   65.844685] nvidia: module license 'NVIDIA' taints kernel.
[   66.245358] Linux video capture interface: v2.00
[   66.398462] cx18:  Start initialization, version 1.0.0
[   66.398529] cx18-0: Initializing card #0
[   66.398533] cx18-0: Autodetected Hauppauge card
[   66.398560] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   66.398733] cx18-0: cx23418 revision 01010000 (B)
[   66.586295] tveeprom 0-0050: Hauppauge model 74041, rev C6B2, serial# 936551
[   66.586299] tveeprom 0-0050: MAC address is 00-0D-FE-0E-4A-67
[   66.586302] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   66.586305] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   66.586307] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   66.586309] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   66.586311] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   66.586313] cx18-0: Autodetected Hauppauge HVR-1600
[   66.586316] cx18-0: VBI is not yet supported
[   66.690444] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   66.690469] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   66.755109] tuner-simple 1-0061: creating new instance
[   66.755114] tuner-simple 1-0061: type set to 50 (TCL 2002N)
[   66.756069] cx18-0: Disabled encoder IDX device
[   66.756115] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   66.756118] DVB: registering new adapter (cx18)
[   66.886027] MXL5005S: Attached at address 0x63
[   66.886034] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   66.886096] cx18-0: DVB Frontend registered
[   66.886116] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   66.886133] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   66.886136] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   66.886153] cx18:  End initialization
[   66.886567] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   66.887458] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   67.313220] intel8x0_measure_ac97_clock: measured 55870 usecs
[   67.313224] intel8x0: clocking to 48000
[   68.094355] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[   68.191543] lp0: using parport0 (polling).
[   68.227179] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   68.571803] Adding 2947916k swap on /dev/sda2.  Priority:-1 extents:1 across:2947916k
[   69.257515] EXT3 FS on sda1, internal journal
[   71.683321] JFS: nTxBlock = 8082, nTxLock = 64662
[   72.313410] ip_tables: (C) 2000-2006 Netfilter Core Team
[   75.093529] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   75.093581] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   75.093749] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   75.093827] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   77.099121] NET: Registered protocol family 10
[   77.099627] lo: Disabled Privacy Extensions
[   89.267113] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   89.814287] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   89.819390] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   89.823981] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   89.824006] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 158332 bytes)
[   89.824010] cx18-0: Did you put the firmware in the hotplug firmware directory?
[   89.824012] cx18-0: Retry loading firmware
[   89.877604] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   90.379620] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   90.385167] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   90.389725] cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)
[   90.389747] cx18-0: Unable to open firmware v4l-cx23418-cpu.fw (must be 158332 bytes)
[   90.389751] cx18-0: Did you put the firmware in the hotplug firmware directory?
[   90.389755] cx18-0: Failed to initialize on minor 0
[   90.390617] cx18-0: Failed to initialize on minor 0
[   90.393253] cx18-0: Failed to initialize on minor 24
[   90.397699] cx18-0: Failed to initialize on minor 32
[   90.528472] cx18-0: Failed to initialize on minor 0
[   90.982095] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   90.983105] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   90.985363] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   93.409628] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   93.409645] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   93.411235] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   93.684990] NET: Registered protocol family 17
[  107.121857] eth0: no IPv6 routers present
[  107.199721] cx18-0: Failed to initialize on minor 24
[  124.238088] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  124.238093] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  174.726792] cx18-0: Failed to initialize on minor 0
[  174.727085] cx18-0: Failed to initialize on minor 24
[  174.727297] cx18-0: Failed to initialize on minor 32
[  174.768232] cx18-0: Failed to initialize on minor 0
[  174.784271] cx18-0: Failed to initialize on minor 0
[  174.791590] cx18-0: Failed to initialize on minor 0
[  174.795488] cx18-0: Failed to initialize on minor 0
[  174.795737] cx18-0: Failed to initialize on minor 0
[  174.871262] cx18-0: Failed to initialize on minor 0
[  174.878471] cx18-0: Failed to initialize on minor 0
[  174.880816] cx18-0: Failed to initialize on minor 0
[  174.881063] cx18-0: Failed to initialize on minor 0
[  183.979672] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  183.979678] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  190.141325] cx18-0: Failed to initialize on minor 0
[  190.141604] cx18-0: Failed to initialize on minor 24
[  190.141777] cx18-0: Failed to initialize on minor 32
[  190.170019] cx18-0: Failed to initialize on minor 0
[  190.182791] cx18-0: Failed to initialize on minor 0
[  190.189931] cx18-0: Failed to initialize on minor 0
[  190.193882] cx18-0: Failed to initialize on minor 0
[  190.194132] cx18-0: Failed to initialize on minor 0
[  190.269776] cx18-0: Failed to initialize on minor 0
[  190.276933] cx18-0: Failed to initialize on minor 0
[  190.279374] cx18-0: Failed to initialize on minor 0
[  190.279625] cx18-0: Failed to initialize on minor 0
[  222.943319] cx18-0: Failed to initialize on minor 0
[  246.744793] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  246.744799] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  251.135732] cx18-0: Failed to initialize on minor 0
[  266.418699] cx18-0: Failed to initialize on minor 0
[  279.065020] cx18-0: Failed to initialize on minor 0
[  283.984845] cx18-0: Failed to initialize on minor 0
[  293.022618] cx18-0: Failed to initialize on minor 0
[  340.466755] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  340.466761] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  413.280018] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  413.280024] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  583.680274] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  583.680280] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  586.518434] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
[  586.518440] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
[  586.633977] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
[  586.633982] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
[  658.711457] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  658.711463] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  723.375548] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  723.375554] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  880.758267] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  880.758273] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  883.037907] cx18-0: Failed to initialize on minor 0
[  913.141526] cx18-0: Failed to initialize on minor 0
[  944.713777] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  944.713783] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  952.129569] cx18-0: Failed to initialize on minor 0
[ 1017.534604] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1017.534610] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1053.581115] cx18-0: Failed to initialize on minor 0
[ 1053.581413] cx18-0: Failed to initialize on minor 24
[ 1053.581589] cx18-0: Failed to initialize on minor 32
[ 1053.616254] cx18-0: Failed to initialize on minor 0
[ 1075.589791] cx18-0: Failed to initialize on minor 0
[ 1075.590062] cx18-0: Failed to initialize on minor 24
[ 1075.590235] cx18-0: Failed to initialize on minor 32
[ 1075.622214] cx18-0: Failed to initialize on minor 0
[ 1076.996318] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1076.996324] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1085.387304] cx18-0: Failed to initialize on minor 0
[ 1085.394867] cx18-0: Failed to initialize on minor 0
[ 1087.348274] cx18-0: Failed to initialize on minor 0
[ 1087.355714] cx18-0: Failed to initialize on minor 0
[ 1088.362012] cx18-0: Failed to initialize on minor 0
[ 1088.369423] cx18-0: Failed to initialize on minor 0
[ 1088.743130] cx18-0: Failed to initialize on minor 0
[ 1088.750627] cx18-0: Failed to initialize on minor 0
[ 1089.047601] cx18-0: Failed to initialize on minor 0
[ 1089.055012] cx18-0: Failed to initialize on minor 0
[ 1136.956933] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1136.956939] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1146.272349] cx18-0: Failed to initialize on minor 0
[ 1146.272630] cx18-0: Failed to initialize on minor 24
[ 1146.272800] cx18-0: Failed to initialize on minor 32
[ 1146.312782] cx18-0: Failed to initialize on minor 0
[ 1148.692466] cx18-0: Failed to initialize on minor 0
[ 1148.692736] cx18-0: Failed to initialize on minor 24
[ 1148.692942] cx18-0: Failed to initialize on minor 32
[ 1148.721185] cx18-0: Failed to initialize on minor 0
[ 1151.536475] cx18-0: Failed to initialize on minor 0
[ 1151.536751] cx18-0: Failed to initialize on minor 24
[ 1151.536924] cx18-0: Failed to initialize on minor 32
[ 1151.565697] cx18-0: Failed to initialize on minor 0
[ 1153.661524] cx18-0: Failed to initialize on minor 0
[ 1153.661797] cx18-0: Failed to initialize on minor 24
[ 1153.661968] cx18-0: Failed to initialize on minor 32
[ 1153.690315] cx18-0: Failed to initialize on minor 0
[ 1158.360462] cx18-0: Failed to initialize on minor 0
[ 1158.368828] cx18-0: Failed to initialize on minor 0
[ 1164.868850] cx18-0: Failed to initialize on minor 0
[ 1169.997841] cx18-0: Failed to initialize on minor 0
[ 1176.173623] cx18-0: Failed to initialize on minor 0
[ 1182.346113] cx18-0: Failed to initialize on minor 0
[ 1196.599881] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1196.599888] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1241.874364] cx18-0: Failed to initialize on minor 0
[ 1241.874660] cx18-0: Failed to initialize on minor 24
[ 1241.874841] cx18-0: Failed to initialize on minor 32
[ 1241.910335] cx18-0: Failed to initialize on minor 0
[ 1241.926639] cx18-0: Failed to initialize on minor 0
[ 1241.933752] cx18-0: Failed to initialize on minor 0
[ 1241.937640] cx18-0: Failed to initialize on minor 0
[ 1241.937900] cx18-0: Failed to initialize on minor 0
[ 1242.014065] cx18-0: Failed to initialize on minor 0
[ 1242.021209] cx18-0: Failed to initialize on minor 0
[ 1242.023474] cx18-0: Failed to initialize on minor 0
[ 1242.023720] cx18-0: Failed to initialize on minor 0
[ 1256.140286] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1256.140292] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1287.654969] cx18-0: Failed to initialize on minor 0
[ 1287.655664] cx18-0: Failed to initialize on minor 24
[ 1287.655910] cx18-0: Failed to initialize on minor 32
[ 1287.683881] cx18-0: Failed to initialize on minor 0
[ 1287.696152] cx18-0: Failed to initialize on minor 0
[ 1287.703335] cx18-0: Failed to initialize on minor 0
[ 1287.705771] cx18-0: Failed to initialize on minor 0
[ 1287.706023] cx18-0: Failed to initialize on minor 0
[ 1287.779272] cx18-0: Failed to initialize on minor 0
[ 1287.786470] cx18-0: Failed to initialize on minor 0
[ 1287.788821] cx18-0: Failed to initialize on minor 0
[ 1287.789105] cx18-0: Failed to initialize on minor 0
[ 1315.803499] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1315.803505] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1339.430737] cx18-0: Failed to initialize on minor 0
[ 1339.431018] cx18-0: Failed to initialize on minor 24
[ 1339.431190] cx18-0: Failed to initialize on minor 32
[ 1339.470918] cx18-0: Failed to initialize on minor 0
[ 1375.597328] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1375.597334] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1408.481857] cx18-0: Failed to initialize on minor 0
[ 1416.612085] cx18-0: Failed to initialize on minor 0
[ 1417.933804] cx18-0: Failed to initialize on minor 0
[ 1435.568076] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1435.568082] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1495.042376] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1495.042382] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1554.785184] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1554.785190] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1589.916085] cx18-0: Failed to initialize on minor 0
[ 1614.609478] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1614.609484] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1673.901861] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1673.901867] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1717.577938] cx18-0: Failed to initialize on minor 0
[ 1724.382446] cx18-0: Failed to initialize on minor 0
[ 1735.454079] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1735.454085] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1823.422160] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1823.422166] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1906.145015] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1906.145021] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1975.708588] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1975.708594] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2036.081771] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2036.081777] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2172.487437] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2172.487443] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2237.132136] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2237.132141] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2355.558120] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2355.558126] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
```

---

### Post by azmanam on 2008-07-20
@ superm1, reply #4

I moved the coax into the TV jack and restarted the computer.  I tied 'Watch TV' and the screen went to black, BUT showed the program information (with much better graphics than last time I had this problem).  I could navigate through the channels and see program information, but screen remained black throughout and when I selected a channel, a box appeared that said I should be receiving a lock by now, and I can change channels (arrows) or something with Y and C.  Nothing did anything.  I went into the backend settings, and everything is still the same as my most recent update (reply #16).

I moved the coax back to the ATSC jack and restarted the computer.  Attempting 'Watch TV' gave the same output.  I could see program information, but always a black screen and always the 'you should have a lock' message.  Backend options are the same as well.

I feel now as if my system is closer to reply #7 in an earlier thread I started ([http://ubuntuforums.org/showthread.php?t=851602](http://ubuntuforums.org/showthread.php?t=851602)) than what I originally posted in this thread.  I'll put some kind of update in the other thread to make note of this.

Thanks again for everyone's help!

---

### Post by willoconley on 2008-07-20
hello, 

this from dmesg is a problem:

cx18-0: retry: file loaded was not v4l-cx23418-cpu.fw (expected size 158332, got 174716)

I don't think anything will tune until you get that to go away. i have had that same message before too, i think updating v4l fixed it. assuming your using the same firmware files and the same v4l driver you are using when you had it working with the -16 kernel - if the only thing that has changed is the kernel, that is the only thing i can think of to try. if you want to try that i think it goes something like:

cd ~/Desktop/v4l-dvb-04ddbe145932
sudo make unload
sudo make install -r    (i think the -r option removes it, not sure though)
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd ~/v4l*
sudo make
sudo make install

if you try that, then check 

dmesg | grep cx18

to see is that firmware message went away.

---

### Post by flammon on 2008-07-20
I just tried to compile the latest version and I get the following:

```

...
LD [M]  /home/rich/Projects/PVR/v4l-dvb/v4l/ir-common.o
LD [M]  /home/rich/Projects/PVR/v4l-dvb/v4l/videodev.o
CC [M]  /home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.o 
/home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.c: In function 'v4l_compat_ioctl32':
/home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.c:985: error: implicit declaration of function 'v4l_printk_ioctl'
make[3]: *** [/home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.o] Error 1
make[2]: *** [_module_/home/rich/Projects/PVR/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/rich/Projects/PVR/v4l-dvb/v4l'
make: *** [all] Error 2

```

---

### Post by azmanam on 2008-07-20
Thanks for the suggestion.  You say 'assuming your using the same firmware files and the same v4l driver you are using when you had it working with the -16 kernel.'  I've not had it working yet.  All this is still my first time trying to get everything set up.  Additionally, I only think I had the 16 kernel for the very first fledgling attempts at getting things to work, and I updated it relatively quickly.  I think.
 
At any rate:

```
adam@adam-desktop:~/Desktop/v4l-dvb-b34907d3d4df$ sudo make unload
make -C /home/adam/Desktop/v4l-dvb-b34907d3d4df/v4l unload
make[1]: Entering directory `/home/adam/Desktop/v4l-dvb-b34907d3d4df/v4l'
scripts/rmmod.pl unload
found 256 modules
/sbin/rmmod tuner_types
ERROR: Module tuner_types is in use by tuner_simple
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple is in use
/sbin/rmmod tuner
/sbin/rmmod cx18
ERROR: Module cx18 is in use
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by cx18
/sbin/rmmod videodev
ERROR: Module videodev is in use by cx18
/sbin/rmmod cs5345
/sbin/rmmod tuner_simple
/sbin/rmmod compat_ioctl32
ERROR: Module compat_ioctl32 is in use by cx18
/sbin/rmmod s5h1409
ERROR: Module s5h1409 is in use
/sbin/rmmod tuner_types
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by cx18,cx2341x
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by videodev
/sbin/rmmod dvb_core
ERROR: Module dvb_core is in use by cx18
/sbin/rmmod mxl5005s
ERROR: Module mxl5005s is in use
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by cx18
/sbin/rmmod tuner_types
ERROR: Module tuner_types does not exist in /proc/modules
/sbin/rmmod tuner_simple
ERROR: Module tuner_simple does not exist in /proc/modules
/sbin/rmmod cx18
ERROR: Module cx18 is in use
/sbin/rmmod cx2341x
ERROR: Module cx2341x is in use by cx18
/sbin/rmmod videodev
ERROR: Module videodev is in use by cx18
/sbin/rmmod compat_ioctl32
ERROR: Module compat_ioctl32 is in use by cx18
/sbin/rmmod s5h1409
ERROR: Module s5h1409 is in use
/sbin/rmmod v4l2_common
ERROR: Module v4l2_common is in use by cx18,cx2341x
/sbin/rmmod v4l1_compat
ERROR: Module v4l1_compat is in use by videodev
/sbin/rmmod dvb_core
ERROR: Module dvb_core is in use by cx18
/sbin/rmmod mxl5005s
ERROR: Module mxl5005s is in use
/sbin/rmmod tveeprom
ERROR: Module tveeprom is in use by cx18
Couldn't unload: tveeprom mxl5005s dvb_core v4l1_compat v4l2_common s5h1409 compat_ioctl32 videodev cx2341x cx18 tuner_simple tuner_types
make[1]: Leaving directory `/home/adam/Desktop/v4l-dvb-b34907d3d4df/v4l'
```

What do I need to turn off (and how) in order to proceed.  I tried removing cx18 from /etc/modules and rebooting, but that must not have worked.

---

### Post by willoconley on 2008-07-20
hello,
ignore what i wrote in the last post as well as those errors. execute.

sudo make uninstall
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd ~/v4l*
sudo make
sudo make install
reboot

---

### Post by azmanam on 2008-07-20
```
adam@adam-desktop:~/Desktop/v4l-dvb-b34907d3d4df$ sudo make uninstall 
make -C /home/adam/Desktop/v4l-dvb-b34907d3d4df/v4l uninstall
make[1]: Entering directory `/home/adam/Desktop/v4l-dvb-b34907d3d4df/v4l'
make[1]: *** No rule to make target `uninstall'.  Stop.
make[1]: Leaving directory `/home/adam/Desktop/v4l-dvb-b34907d3d4df/v4l'
make: *** [uninstall] Error 2
```

---

### Post by azmanam on 2008-07-20
PS.  I'm sorry I'm not very fluent in linux/shell/bash/whatever it is language.  If I were more fluent, I feel like I could do more of this on my own.  I am truly grateful for your patience with me.

---

### Post by willoconley on 2008-07-20
thats okay i'm not that fluent with any of the 4 either. 

so v4l doesn't include directions for uninstalling, i suppose it isn't necessary. looking back at the thread you originally got directions from sofasurfer installed over a previous v4l installation and was okay (because i told him the wrong make command, otherwise i would have already known this), i would just delete the v4l directory on your desktop and continue with the commands from my last post.

---

### Post by willoconley on 2008-07-20
> **flammon said:**
> I just tried to compile the latest version and I get the following:

```

...
LD [M]  /home/rich/Projects/PVR/v4l-dvb/v4l/ir-common.o
LD [M]  /home/rich/Projects/PVR/v4l-dvb/v4l/videodev.o
CC [M]  /home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.o 
/home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.c: In function 'v4l_compat_ioctl32':
/home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.c:985: error: implicit declaration of function 'v4l_printk_ioctl'
make[3]: *** [/home/rich/Projects/PVR/v4l-dvb/v4l/compat_ioctl32.o] Error 1
make[2]: *** [_module_/home/rich/Projects/PVR/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/rich/Projects/PVR/v4l-dvb/v4l'
make: *** [all] Error 2

```

hi,
this has to be a bug in v4l, try updating the source, if you have the newest try an older revision.
if you used mercurial to get it you can use

hg udpate -c xxxx

where x is the revision number to get a specific revision, the list can be found at [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

---

### Post by azmanam on 2008-07-20
~/Desktop/v4l* and ~/Desktop/v4l*.tar deleted

hg clone done

cd /lib/firmware/v4l-dvb (it seemed like this was the directory created in the hg clone command) (I think I happened to be in the firmware folder when I executed the hg clone command...  Is this a problem?  Should I move the /lib/firmware/v4l-dvb directory somewhere else?)

sudo make gave an interesting warning at start.  Something about not having full kernel sources installed, but would build the tree anyway. (I'm glad I saw it.  It scrolled off the screen by the time make was done.)

sudo make install seemed to work without problem.

reboot.

```
adam@adam-desktop:~$ dmesg | grep cx18
[   37.925022] cx18:  Start initialization, version 1.0.0
[   37.925087] cx18-0: Initializing card #0
[   37.925092] cx18-0: Autodetected Hauppauge card
[   37.925118] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   37.925305] cx18-0: cx23418 revision 01010000 (B)
[   38.114496] cx18-0: Autodetected Hauppauge HVR-1600
[   38.114498] cx18-0: VBI is not yet supported
[   38.222609] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   38.222633] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   38.280087] cx18-0: Disabled encoder IDX device
[   38.280137] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   38.280140] DVB: registering new adapter (cx18)
[   38.395228] cx18-0: DVB Frontend registered
[   38.395250] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   38.395269] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   38.395272] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   38.395289] cx18:  End initialization
[B][   59.933895] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   60.540435] cx18-0: loaded v4l-cx23418-cpu.fw firmware (174716 bytes)
[   60.546540] cx18-0: FW version: 0.0.71.0 (Release 2006/12/29)
[   61.875818] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)[/B]
```


Getting excited, now.  (but not getting my hopes up too high)

Tried $ mplayer /dev/video0
  Got snow

Tried $ me-tv /dev/video0
  Got 'failed to open tuner: device or resource busy' and noticed in the output 'Unable to locate theme engine in module_path: "pixmap"'.  Went here ([http://ubuntuforums.org/showthread.php?t=332958](http://ubuntuforums.org/showthread.php?t=332958)) and fixed that problem.

Retried $ me-tv /dev/video0
  Got 'failed' message again.

Went into backend setup.  Went into Capture card menu.  Selected v4l : /dev/video0. Probed info now recognized the Hauppauge card.  Default input initially says 'could not open /dev/video0', but if I change video device away from /dev/vide0 and back again, default input changes to read 'Tuner 1' VBI device is still blank.

DVB DTV capture card has dvb device # as 0, frontend id: samsung (as before).

Just incase, created a MPEG-2 encoder card entry.  video device reads '/dev/video0' (manually inputted), probed info reads the Hauppauge card.

Channel frequency table in video sources menu is 'default'

In the input connections, I have the 5 options for the analog and MPEG capture cards that I mentioned previously.  Scanning for channels in any of the MPEG cards or DVB cards returns no lock-no signal errors.  Scanning for channels in analog card CRASHES THE BACKEND SETUP and prompts me to run mythfilldatabase.

Channel editor shows all my local channels.

For good measure:

```
adam@adam-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] 191MB HIGHMEM available.
[    0.000000] 832MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 261936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   212992
[    0.000000]   HighMem    212992 ->   261936
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261936
[    0.000000] On node 0 totalpages: 261936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1632 pages used for memmap
[    0.000000]   Normal zone: 207264 pages, LIFO batch:31
[    0.000000]   HighMem zone: 382 pages used for memmap
[    0.000000]   HighMem zone: 48562 pages, LIFO batch:15
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:  Product ID: Springdale-G APIC at: 0xFEE00000
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259890
[    0.000000] Kernel command line: root=UUID=2e916da9-0ff1-4f33-a24d-68dfe6e67644 ro quiet splash acpi=off apm=power_off vmalloc=192M pci=nommconf
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3059.154 MHz processor.
[   23.313760] Console: colour VGA+ 80x25
[   23.313764] console [tty0] enabled
[   23.314371] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.314958] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.348135] Memory: 1026272k/1047744k available (2177k kernel code, 20596k reserved, 1006k data, 368k init, 195776k highmem)
[   23.348145] virtual kernel memory layout:
[   23.348146]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.348147]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.348148]     vmalloc : 0xf4800000 - 0xff7fe000   ( 175 MB)
[   23.348149]     lowmem  : 0xc0000000 - 0xf4000000   ( 832 MB)
[   23.348150]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   23.348151]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   23.348152]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   23.348155] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.348205] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   23.428055] Calibrating delay using timer specific routine.. 6123.29 BogoMIPS (lpj=12246590)
[   23.428088] Security Framework initialized
[   23.428098] SELinux:  Disabled at boot.
[   23.428116] AppArmor: AppArmor initialized
[   23.428121] Failure registering capabilities with primary security module.
[   23.428129] Mount-cache hash table entries: 512
[   23.428286] Initializing cgroup subsys ns
[   23.428292] Initializing cgroup subsys cpuacct
[   23.428304] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   23.428316] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   23.428319] CPU: L2 cache: 512K
[   23.428321] CPU: Physical Processor ID: 0
[   23.428324] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   23.428336] Compat vDSO mapped to ffffe000.
[   23.428351] Checking 'hlt' instruction... OK.
[   23.444401] SMP alternatives: switching to UP code
[   23.445873] Freeing SMP alternatives: 11k freed
[   23.445997] Early unpacking initramfs... done
[   23.729452] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
[   23.729491] Total of 1 processors activated (6123.29 BogoMIPS).
[   23.729549] ExtINT not setup in hardware but reported by MP table
[   23.729625] ENABLING IO-APIC IRQs
[   23.729813] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   23.982899] Brought up 1 CPUs
[   23.982922] CPU0 attaching sched-domain:
[   23.982925]  domain 0: span 01
[   23.982927]   groups: 01
[   23.983119] net_namespace: 64 bytes
[   23.983130] Booting paravirtualized kernel on bare hardware
[   23.983629] Time:  1:55:03  Date: 07/21/08
[   23.983658] NET: Registered protocol family 16
[   23.983877] EISA bus registered
[   23.985398] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   23.985401] PCI: Using configuration type 1
[   23.985420] Setting up standard PCI resources
[   23.997219] ACPI: Interpreter disabled.
[   23.997223] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.997256] pnp: PnP ACPI: disabled
[   23.997260] PnPBIOS: Scanning system for PnP BIOS support...
[   23.997271] PnPBIOS: Found PnP BIOS installation structure at 0xc00f3450
[   23.997274] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x3a6a, dseg 0xf0000
[   23.997803] PNPBIOS fault.. attempting recovery.
[   23.997853] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   23.997899] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   23.997944] PnPBIOS: Check with your vendor for an updated BIOS
[   23.997988] PnPBIOS: get_dev_node: unexpected status 0x37
[   23.998030] PnPBIOS: 12 nodes reported by PnP BIOS; 12 recorded by driver
[   23.998265] PCI: Probing PCI hardware
[   23.998268] PCI: Probing PCI hardware (bus 00)
[   23.998736] Force enabled HPET at base address 0xfed00000
[   23.998743] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   23.998746] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   23.999292] PCI: Transparent bridge - 0000:00:1e.0
[   24.000028] PCI: Using IRQ router PIIX/ICH [8086/24d0] at 0000:00:1f.0
[   24.000037] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 16
[   24.000041] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 19
[   24.000045] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 18
[   24.000048] PCI->APIC IRQ transform: 0000:00:1d.3[A] -> IRQ 16
[   24.000052] PCI->APIC IRQ transform: 0000:00:1d.7[D] -> IRQ 23
[   24.000057] PCI->APIC IRQ transform: 0000:00:1f.1[A] -> IRQ 18
[   24.000060] PCI->APIC IRQ transform: 0000:00:1f.2[A] -> IRQ 18
[   24.000064] PCI->APIC IRQ transform: 0000:00:1f.3[B] -> IRQ 17
[   24.000067] PCI->APIC IRQ transform: 0000:00:1f.5[B] -> IRQ 17
[   24.000070] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   24.000073] PCI->APIC IRQ transform: 0000:02:03.0[A] -> IRQ 19
[   24.000076] PCI->APIC IRQ transform: 0000:02:04.0[A] -> IRQ 18
[   24.000080] PCI->APIC IRQ transform: 0000:02:08.0[A] -> IRQ 20
[   24.010885] NET: Registered protocol family 8
[   24.010887] NET: Registered protocol family 20
[   24.011001] hpet clockevent registered
[   24.011007] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   24.011011] hpet0: 3 64-bit timers, 14318180 Hz
[   24.012048] AppArmor: AppArmor Filesystem Enabled
[   24.012090] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   24.012092] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   24.012095] system 00:00: iomem range 0xe6000-0xfffff could not be reserved
[   24.012097] system 00:00: iomem range 0x100000-0x3ff2ffff could not be reserved
[   24.012100] system 00:00: iomem range 0x3ff30000-0x3ff3ffff could not be reserved
[   24.012102] system 00:00: iomem range 0x3ff40000-0x3ffeffff could not be reserved
[   24.012104] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   24.012107] system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
[   24.012110] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   24.012538] PCI: Bridge: 0000:00:01.0
[   24.012540]   IO window: disabled.
[   24.012545]   MEM window: ec500000-ee5fffff
[   24.012548]   PREFETCH window: d4300000-e42fffff
[   24.012553] PCI: Bridge: 0000:00:1e.0
[   24.012556]   IO window: b000-bfff
[   24.012561]   MEM window: ee600000-feafffff
[   24.012565]   PREFETCH window: e4300000-e43fffff
[   24.012583] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.012593] NET: Registered protocol family 2
[   24.014784] Time: tsc clocksource has been installed.
[   24.046800] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.047138] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.048026] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.048546] TCP: Hash tables configured (established 131072 bind 65536)
[   24.048551] TCP reno registered
[   24.058882] checking if image is initramfs... it is
[   24.513709] Switched to high resolution mode on CPU 0
[   24.615649] Freeing initrd memory: 7460k freed
[   24.616246] audit: initializing netlink socket (disabled)
[   24.616263] audit(1216605303.164:1): initialized
[   24.616442] highmem bounce pool size: 64 pages
[   24.618274] VFS: Disk quotas dquot_6.5.1
[   24.618358] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.618538] io scheduler noop registered
[   24.618541] io scheduler anticipatory registered
[   24.618542] io scheduler deadline registered
[   24.618557] io scheduler cfq registered (default)
[   24.618649] Boot video device is 0000:01:00.0
[   24.618655] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   24.618895] isapnp: Scanning for PnP cards...
[   24.972036] isapnp: No Plug & Play device found
[   25.000436] Real Time Clock Driver v1.12ac
[   25.000513] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.000678] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.001768] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.002552] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.002620] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.002728] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.005619] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.005624] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.012645] mice: PS/2 mouse device common for all mice
[   25.012766] EISA: Probing bus 0 at eisa.0
[   25.012799] EISA: Detected 0 cards.
[   25.012802] cpuidle: using governor ladder
[   25.012804] cpuidle: using governor menu
[   25.012895] NET: Registered protocol family 1
[   25.012923] Using IPI No-Shortcut mode
[   25.012955] registered taskstats version 1
[   25.013035]   Magic number: 0:577:913
[   25.013088]   hash matches device ptyz9
[   25.013096]   hash matches device ptywc
[   25.013133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.013135] EDD information not available.
[   25.013525] Freeing unused kernel memory: 368k freed
[   25.040505] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.221139] fuse init (API version 7.9)
[   26.250579] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   26.461381] usbcore: registered new interface driver usbfs
[   26.461407] usbcore: registered new interface driver hub
[   26.469810] usbcore: registered new device driver usb
[   26.477318] USB Universal Host Controller Interface driver v3.0
[   26.477395] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.477400] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.477688] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.477717] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   26.477855] usb usb1: configuration #1 chosen from 1 choice
[   26.477878] hub 1-0:1.0: USB hub found
[   26.477885] hub 1-0:1.0: 2 ports detected
[   26.545129] SCSI subsystem initialized
[   26.581145] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.581151] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.581174] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.581200] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[   26.581304] usb usb2: configuration #1 chosen from 1 choice
[   26.581327] hub 2-0:1.0: USB hub found
[   26.581333] hub 2-0:1.0: 2 ports detected
[   26.597029] libata version 3.00 loaded.
[   26.611423] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   26.611427] e100: Copyright(c) 1999-2006 Intel Corporation
[   26.684895] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.684901] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.684924] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.684950] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   26.685067] usb usb3: configuration #1 chosen from 1 choice
[   26.685091] hub 3-0:1.0: USB hub found
[   26.685097] hub 3-0:1.0: 2 ports detected
[   26.746235] Floppy drive(s): fd0 is 1.44M
[   26.764313] FDC 0 is a post-1991 82077
[   26.788670] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.788676] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.788701] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   26.788724] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   26.788837] usb usb4: configuration #1 chosen from 1 choice
[   26.788861] hub 4-0:1.0: USB hub found
[   26.788867] hub 4-0:1.0: 2 ports detected
[   26.892563] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   26.892569] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   26.892600] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   26.896509] ehci_hcd 0000:00:1d.7: debug port 1
[   26.896516] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   26.896525] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[   26.912274] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.912399] usb usb5: configuration #1 chosen from 1 choice
[   26.912423] hub 5-0:1.0: USB hub found
[   26.912431] hub 5-0:1.0: 8 ports detected
[   27.038973] e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:07:e9:64:96:8f
[   27.038991] ata_piix 0000:00:1f.1: version 2.12
[   27.039004] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   27.039050] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.040705] scsi0 : ata_piix
[   27.041610] scsi1 : ata_piix
[   27.041662] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   27.041665] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   27.212775] ata1.00: ATA-5: WDC WD400BB-53AUA1, 18.20D18, max UDMA/100
[   27.212780] ata1.00: 78165360 sectors, multi 16: LBA 
[   27.234460] ata1.01: ATA-7: WDC WD5000AAJB-00UHA0, 07.01N01, max UDMA/100
[   27.234464] ata1.01: 976773168 sectors, multi 16: LBA48 
[   27.248683] ata1.00: configured for UDMA/100
[   27.264494] ata1.01: configured for UDMA/100
[   27.786576] ata2.00: ATAPI: MATSHITA CR-594, YS0M, max UDMA/33
[   27.786598] ata2.01: ATAPI: _NEC NR-7700A, 1.23, max MWDMA2
[   27.958125] ata2.00: configured for UDMA/33
[   28.161844] ata2.01: configured for MWDMA2
[   28.161971] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-53AU 18.2 PQ: 0 ANSI: 5
[   28.162386] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAJB-0 07.0 PQ: 0 ANSI: 5
[   28.164880] scsi 1:0:0:0: CD-ROM            MATSHITA CD-ROM CR-594    YS0M PQ: 0 ANSI: 5
[   28.169250] scsi 1:0:1:0: CD-ROM            _NEC     NR-7700A         1.23 PQ: 0 ANSI: 5
[   28.169315] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   28.169371] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.169699] scsi2 : ata_piix
[   28.169860] scsi3 : ata_piix
[   28.169892] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[   28.169894] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[   28.520396] Driver 'sd' needs updating - please use bus_type methods
[   28.520486] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   28.520500] sd 0:0:0:0: [sda] Write Protect is off
[   28.520502] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.520522] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   28.520571] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   28.520582] sd 0:0:0:0: [sda] Write Protect is off
[   28.520584] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.520602] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   28.520607]  sda: sda1 sda2
[   28.531390] Driver 'sr' needs updating - please use bus_type methods
[   28.551464] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.551544] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   28.551558] sd 0:0:1:0: [sdb] Write Protect is off
[   28.551561] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.551580] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.551625] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   28.551636] sd 0:0:1:0: [sdb] Write Protect is off
[   28.551638] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.551656] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.551660]  sdb: sdb1
[   28.560717] sd 0:0:1:0: [sdb] Attached SCSI disk
[   28.570528] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.570549] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   28.570567] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   28.570585] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   28.574184] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   28.574190] Uniform CD-ROM driver Revision: 3.20
[   28.574249] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   28.594903] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   28.594962] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   28.933777] Attempting manual resume
[   28.933781] swsusp: Resume From Partition 8:2
[   28.933783] PM: Checking swsusp image.
[   28.933966] PM: Resume from disk failed.
[   28.983287] kjournald starting.  Commit interval 5 seconds
[   28.983302] EXT3-fs: mounted filesystem with ordered data mode.
[   36.388017] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   36.473797] iTCO_vendor_support: vendor-support=0
[   36.478951] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.494905] Linux agpgart interface v0.102
[   36.530894] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.539272] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.643505] agpgart: Detected an Intel 865 Chipset.
[   36.646300] agpgart: AGP aperture is 64M @ 0xe8000000
[   37.041085] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   37.067984] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   37.068016] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.366390] Linux video capture interface: v2.00
[   37.430041] nvidia: module license 'NVIDIA' taints kernel.
[   37.819751] Intel 82802 RNG detected
[   37.925022] cx18:  Start initialization, version 1.0.0
[   37.925087] cx18-0: Initializing card #0
[   37.925092] cx18-0: Autodetected Hauppauge card
[   37.925118] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   37.925305] cx18-0: cx23418 revision 01010000 (B)
[   38.114477] tveeprom 0-0050: Hauppauge model 74041, rev C6B2, serial# 936551
[   38.114482] tveeprom 0-0050: MAC address is 00-0D-FE-0E-4A-67
[   38.114484] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   38.114487] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   38.114489] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   38.114491] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   38.114493] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   38.114496] cx18-0: Autodetected Hauppauge HVR-1600
[   38.114498] cx18-0: VBI is not yet supported
[   38.222609] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   38.222633] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   38.279129] tuner-simple 1-0061: creating new instance
[   38.279134] tuner-simple 1-0061: type set to 50 (TCL 2002N)
[   38.280087] cx18-0: Disabled encoder IDX device
[   38.280137] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   38.280140] DVB: registering new adapter (cx18)
[   38.395160] MXL5005S: Attached at address 0x63
[   38.395167] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   38.395228] cx18-0: DVB Frontend registered
[   38.395250] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   38.395269] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   38.395272] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   38.395289] cx18:  End initialization
[   38.395677] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   38.396587] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   38.821455] intel8x0_measure_ac97_clock: measured 55971 usecs
[   38.821459] intel8x0: clocking to 48000
[   39.696758] parport0: PC-style at 0x378 [PCSPP,TRISTATE,EPP]
[   39.791594] lp0: using parport0 (polling).
[   39.823235] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   40.151400] Adding 2947916k swap on /dev/sda2.  Priority:-1 extents:1 across:2947916k
[   40.826433] EXT3 FS on sda1, internal journal
[   41.749614] JFS: nTxBlock = 8082, nTxLock = 64662
[   42.537360] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.565385] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   45.565437] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   45.565605] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   45.565683] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   47.827681] NET: Registered protocol family 10
[   47.828168] lo: Disabled Privacy Extensions
[   59.933895] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   60.540435] cx18-0: loaded v4l-cx23418-cpu.fw firmware (174716 bytes)
[   60.546540] cx18-0: FW version: 0.0.71.0 (Release 2006/12/29)
[   61.875818] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   62.519097] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.520083] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   62.537571] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   65.040245] NET: Registered protocol family 17
[   66.021947] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   66.021964] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   66.021997] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   78.627400] eth0: no IPv6 routers present
[   92.158401] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[   92.158407] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  530.148133] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  530.148139] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  677.346510] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  677.346516] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  756.008532] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  756.008538] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  841.245343] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  841.245349] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  950.718994] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  950.719000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1010.408892] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1010.408898] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1106.671584] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1106.671590] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1198.745267] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1198.745273] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1258.189803] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1258.189809] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1443.377004] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1443.377010] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1503.535191] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1503.535197] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1563.159007] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1563.159012] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1622.543451] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1622.543457] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1682.983229] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1682.983234] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1743.247827] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1743.247833] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1802.842232] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1802.842238] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1866.080200] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1866.080206] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1925.702945] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1925.702950] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1931.509259] mythtv-setup.re[6253]: segfault at 000000b8 eip b65cfe91 esp afce8d80 error 4
[ 1985.293317] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1985.293323] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2045.697475] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2045.697481] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 2107.184922] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 2107.184928] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
```

---

### Post by azmanam on 2008-07-20
OOOOHHH!

Named all the various input connections for reference as i scrolled through them with 'c' in watch TV mode.

Went into Watch TV. Got Snow.  I'm pretty sure I was in MPEGTuner1, which corresponded to MPEG-2 capture card, and Tuner 1 from Input connections (i think).  On a hunch, switched coax from ATSC jack to TV jack, AND I SAW A TV SHOW!!!  CSI-NY on CBS (it was a repeat...).  Changed the channel, and it was... still CBS.  Aparently, the only thing I can watch is CBS.

Scrolled through with 'c' and only the MPEG options were coming up.  Then got to MPEGComposite2, which was the last of the 5 options, and it's stuck there.  I can hit c all i want, but it just refreshes the MPEGComposite2 option.

how can I get back to MPEGTuner1?

I can hit m to go to menu, in the switch input option, the Analog ones show up, and 2 DVB ones show up (which is odd, because there was only 1 dvb option in the input connections list). Additionally, there's some cx11 option.  Selecting the DVB ones goes to black, then gives the 'you should have a lock by now' error.  I can escape back to frontend menu.  selecting either the cx11 option or the analog tuner1 option goes to black and appears to hang.  Hitting escape does nothing for easily 20-30 seconds, then goes to frontend menu.

---

### Post by azmanam on 2008-07-20
Went into Capture Cards menu, and noticed that for the MPEG card, Composite2 was selected as default input.  Changed to Tuner1.  Scanning for channels in input connections menu crashes backednd setup.

Go back into WatchTV.  I can see the picture, but again, all I get is CBS (which is not the lowest numbered TV station for my cable.  I think it might be of the 4 networks, though. (CBS=5, ABC=11, NBC=17, FOX=50))  Attempting channels 11, 17, or 50 all show... CBS.

(edited to add more information)

---

### Post by flammon on 2008-07-21
Yes, that's all it was, just some unlucky timing on the download. The latest version fixes the X64 build problems that I had.

---

### Post by azmanam on 2008-07-22
I fired up the box this morning, and WatchTV this time went to PBS - cable channel 4 (I'm not sure if it has an over-the-air channel).  This is different from last time when I could only watch CBS.  Changing channel again remains at PBS.  To be clear, I don't have my remote configured yet (one step at a time), so I am controlling everything from my keyboard.  If I use the up and down arrows, It scrolls though the truncated program guide.  I hit enter to attempt to change channels.  Also, manually typing the numbers 1 and 2 to change to channel 12 and pressing enter remains on PBS.

I went into backend setup, input connections, MPEG card.  External Channel Change Command is blank, as is Preset Tuner to Channel.  I put 3 in for Preset Tuner to Channel (thinking it might be something like the TV needs to be on 3 for the VCR to work, even though I don't think this is an analogous situation).  Go back to WatchTV... and CBS plays.  Now, CBS is cable channel THREE.

Back into backend setup, and I put in ... oh ... 11 for Preset Tuner to Channel.  Back to WatchTV.  I get cable channel ELEVEN!

So, the tuner card is capable of distinguishing channels.  Do I need some code or something in External Channel Change Command?  Is it time to configure the remote and see if that helps?  Anyone have ideas on how to change channels like a normal person without going into backend setup every time?

---

### Post by azmanam on 2008-07-24
alright.  NO CLUE what I did, but my system is functional now.

Actually, I have some clue.  Messing with it the other day, I managed to take a couple steps backward.  I did something with mysql, but I'm not really sure what, and I couldn't get into the frontend or the backend.  I couldn't connect to mythconverg database (I think).  I uninstalled all the mysql programs with synaptec, as well as all the myth/mythfrontend/mythbackend programs.  Reboot.  Then I reinstalled the mysql programs.  Reboot.  Then I reinstalled the myth/front/backend programs.  Reboot.  All my settings were maintained in the backend (that is, the drivers were still recognized, etc). 

So I was about to start a new thread asking for help with my one channel at a time problem.  For completeness, I was testing the various capture card settings, and the different ones either caused livetv to hang or gave a 'you should be able to lock' signal.  So i changed it back to mpeg2 just so I could jot down all my settings.  And it started working.  I can change channels and everything.  I had to go back in and tell the video to use us-cable not default, but it's working!

Thanks for all your help to date.  I say to date, because I'm sure I'll manage to screw something up along the way, and I'm sure I'll be back!

---

