---
title: "Changed recording profile now no livetv"
date: 2009-01-07
forum: Mythbuntu
---

### Post by singedwings on 2009-01-07
My setup was working fine, except for recordings having the edges of the screen chopped off. So in the tv settings section I edited the recording profile for livetv. I changed the width and height settings from 720x576 to 768x576 (PAL dimensions as suggested by the info on screen).

Now I get no livetv, even if I change the setting back to how it was. Please help!

```
The error listed is at the bottom of my terminal output:-

2009-01-07 15:42:38.428 Using runtime prefix = /usr
2009-01-07 15:42:38.746 XScreenSaver support enabled
2009-01-07 15:42:38.747 DPMS is active.
2009-01-07 15:42:38.748 Empty LocalHostName.
2009-01-07 15:42:38.748 Using localhost value of tellybox
2009-01-07 15:42:38.756 New DB connection, total: 1
2009-01-07 15:42:38.762 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:42:38.764 Closing DB connection named 'DBManager0'
2009-01-07 15:42:38.766 Total desktop dim: 1024x768, over 1 screen[s].
2009-01-07 15:42:38.766 Primary screen 0.
2009-01-07 15:42:38.767 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:42:38.769 Using screen 0, 1024x768 at 0,0
2009-01-07 15:42:38.795 New DB connection, total: 2
2009-01-07 15:42:38.796 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:42:38.800 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-07 15:42:38.800 Enabled verbose msgs:  important general
2009-01-07 15:42:39.362 No theme dir: /home/tv/.mythtv/themes/G.A.N.T
2009-01-07 15:42:39.364 Total desktop dim: 1024x768, over 1 screen[s].
2009-01-07 15:42:39.364 Primary screen 0.
2009-01-07 15:42:39.365 Using screen 0, 1024x768 at 0,0
2009-01-07 15:42:39.366 No theme dir: /home/tv/.mythtv/themes/G.A.N.T
2009-01-07 15:42:39.366 Switching to square mode (G.A.N.T)
2009-01-07 15:42:39.386 Using the OpenGL painter
2009-01-07 15:42:39.388 lirc init success using configuration file: /home/tv/.mythtv/lircrc
2009-01-07 15:42:39.388 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc
2009-01-07 15:42:40.409 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-07 15:42:40.446 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-07 15:42:40.490 Registering Internal as a media playback plugin.
2009-01-07 15:42:40.586 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-07 15:42:40.642 Using NV NPOT texture extension
2009-01-07 15:42:40.782 MythMusic adding CD-Writer: 4,0,0 -- DVD-ROM DDU1615 
2009-01-07 15:42:40.853 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-01-07 15:42:40.949 No theme dir: /home/tv/.mythtv/themes/G.A.N.T
2009-01-07 15:42:42.690 Connecting to backend server: 192.168.0.5:6543 (try 1 of 5)
2009-01-07 15:42:42.691 Using protocol version 40
2009-01-07 15:42:42.717 TV: Attempting to change from None to WatchingLiveTV
2009-01-07 15:42:42.718 Using protocol version 40
2009-01-07 15:42:53.373 RingBuf(/var/lib/mythtv/recordings/118_20090107154245.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/118_20090107154245.mpg'.
2009-01-07 15:42:53.386 New DB connection, total: 3
2009-01-07 15:42:53.392 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:42:53.416 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/118_20090107154245.mpg
2009-01-07 15:42:53.416 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-01-07 15:42:53.443 DPMS Deactivated 
2009-01-07 15:42:58.182 TV Error: LiveTV not successfully started
```



```
My frontend log:-

Starting mythfrontend.real..
2009-01-07 15:36:43.092 New DB connection, total: 2
2009-01-07 15:36:43.093 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:36:43.097 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-07 15:36:43.097 Enabled verbose msgs:  important general
2009-01-07 15:36:44.207 No theme dir: /home/tv/.mythtv/themes/G.A.N.T
2009-01-07 15:36:44.209 Total desktop dim: 1024x768, over 1 screen[s].
2009-01-07 15:36:44.210 Primary screen 0.
2009-01-07 15:36:44.210 Using screen 0, 1024x768 at 0,0
2009-01-07 15:36:44.211 No theme dir: /home/tv/.mythtv/themes/G.A.N.T
2009-01-07 15:36:44.211 Switching to square mode (G.A.N.T)
2009-01-07 15:36:44.231 Using the OpenGL painter
2009-01-07 15:36:44.232 lirc init success using configuration file: /home/tv/.mythtv/lircrc
2009-01-07 15:36:44.233 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc
2009-01-07 15:36:45.187 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-07 15:36:45.219 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-07 15:36:45.308 Registering Internal as a media playback plugin.
2009-01-07 15:36:45.573 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-07 15:36:45.896 Using NV NPOT texture extension
2009-01-07 15:36:46.014 MythMusic adding CD-Writer: 4,0,0 -- DVD-ROM DDU1615 
2009-01-07 15:36:46.077 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-01-07 15:36:46.291 No theme dir: /home/tv/.mythtv/themes/G.A.N.T
2009-01-07 15:36:48.573 Connecting to backend server: 192.168.0.5:6543 (try 1 of 5)
2009-01-07 15:36:48.574 Using protocol version 40
2009-01-07 15:36:48.584 TV: Attempting to change from None to WatchingLiveTV
2009-01-07 15:36:48.585 Using protocol version 40
2009-01-07 15:36:53.781 New DB connection, total: 3
2009-01-07 15:36:53.782 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:36:53.806 DPMS Deactivated 
2009-01-07 15:36:54.698 AFD: Opened codec 0x8c1fff0, id(MPEG2VIDEO) type(Video)
2009-01-07 15:36:54.699 AFD: codec MP2 has 2 channels
2009-01-07 15:36:54.699 AFD: Opened codec 0x8c206f0, id(MP2) type(Audio)
2009-01-07 15:36:54.811 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-07 15:36:54.815 Opening ALSA audio device 'default'.
2009-01-07 15:36:54.831 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-01-07 15:36:54.887 Mixer unable to find control PCM
2009-01-07 15:36:54.887 Mixer unable to find control PCM
2009-01-07 15:36:54.887 Mixer unable to find control PCM
2009-01-07 15:36:54.887 Mixer unable to find control PCM
2009-01-07 15:36:54.888 Mixer unable to find control PCM
2009-01-07 15:36:54.888 Mixer unable to find control PCM
2009-01-07 15:36:54.889 Mixer unable to find control PCM
2009-01-07 15:36:54.964 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-07 15:36:55.042 OSD Theme Dimensions W: 1280 H: 720
2009-01-07 15:36:55.608 TV: Changing from None to WatchingLiveTV
2009-01-07 15:36:55.615 Realtime priority would require SUID as root.
2009-01-07 15:36:55.736 Video timing method: USleep with busy wait
2009-01-07 15:37:17.069 Mixer unable to find control PCM
2009-01-07 15:37:17.069 Mixer unable to find control PCM
2009-01-07 15:37:18.228 NVP: prebuffering pause
2009-01-07 15:37:18.341 WriteAudio: buffer underrun
2009-01-07 15:37:20.279 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:37:21.659 New DB connection, total: 4
2009-01-07 15:37:21.662 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:22.356 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:37:23.269 Mixer unable to find control PCM
2009-01-07 15:37:23.269 Mixer unable to find control PCM
2009-01-07 15:37:33.504 Mixer unable to find control PCM
2009-01-07 15:37:33.504 Mixer unable to find control PCM
2009-01-07 15:37:33.815 NVP: prebuffering pause
2009-01-07 15:37:33.917 WriteAudio: buffer underrun
2009-01-07 15:37:35.879 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:37:37.948 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:37:39.601 Mixer unable to find control PCM
2009-01-07 15:37:39.601 Mixer unable to find control PCM
2009-01-07 15:37:42.620 Mixer unable to find control PCM
2009-01-07 15:37:42.620 Mixer unable to find control PCM
2009-01-07 15:37:42.988 NVP: prebuffering pause
2009-01-07 15:37:43.035 WriteAudio: buffer underrun
2009-01-07 15:37:45.148 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:37:47.197 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:37:48.763 Mixer unable to find control PCM
2009-01-07 15:37:48.764 Mixer unable to find control PCM
2009-01-07 15:38:35.517 TV: Attempting to change from WatchingLiveTV to None
2009-01-07 15:38:36.303 NVP: prebuffering pause
2009-01-07 15:38:36.378 WriteAudio: buffer underrun
2009-01-07 15:38:36.587 RingBuf(/var/lib/mythtv/recordings/110_20090107153745.mpg): Waited 1.0 seconds for data to become available...
2009-01-07 15:38:36.587 Checking to see if there's a new livetv program to switch to..
2009-01-07 15:38:37.589 RingBuf(/var/lib/mythtv/recordings/110_20090107153745.mpg): Waited 2.0 seconds for data to become available...
2009-01-07 15:38:37.589 Checking to see if there's a new livetv program to switch to..
2009-01-07 15:38:37.903 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:39.504 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:39.590 RingBuf(/var/lib/mythtv/recordings/110_20090107153745.mpg): Waited 4.0 seconds for data to become available...
2009-01-07 15:38:39.590 Checking to see if there's a new livetv program to switch to..
2009-01-07 15:38:41.104 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:42.705 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:43.592 RingBuf(/var/lib/mythtv/recordings/110_20090107153745.mpg): Waited 8.0 seconds for data to become available...
2009-01-07 15:38:43.592 Checking to see if there's a new livetv program to switch to..
2009-01-07 15:38:44.305 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:45.906 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:47.506 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:49.106 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:50.707 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:38:51.593 RingBuf(/var/lib/mythtv/recordings/110_20090107153745.mpg) Error: Waited 16 seconds for data, aborting.
2009-01-07 15:38:51.718 TV: Changing from WatchingLiveTV to None
2009-01-07 15:38:51.743 DPMS Reactivated.
2009-01-07 15:39:01.075 TV: Attempting to change from None to WatchingLiveTV
2009-01-07 15:39:01.076 Using protocol version 40
2009-01-07 15:39:06.091 DPMS Deactivated 
2009-01-07 15:39:07.073 AFD: Opened codec 0x8d4a5a0, id(MPEG2VIDEO) type(Video)
2009-01-07 15:39:07.073 AFD: codec MP2 has 2 channels
2009-01-07 15:39:07.073 AFD: Opened codec 0x8f04c40, id(MP2) type(Audio)
2009-01-07 15:39:07.134 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-07 15:39:07.134 Opening ALSA audio device 'default'.
2009-01-07 15:39:07.138 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-01-07 15:39:07.157 Mixer unable to find control PCM
2009-01-07 15:39:07.157 Mixer unable to find control PCM
2009-01-07 15:39:07.157 Mixer unable to find control PCM
2009-01-07 15:39:07.157 Mixer unable to find control PCM
2009-01-07 15:39:07.158 Mixer unable to find control PCM
2009-01-07 15:39:07.158 Mixer unable to find control PCM
2009-01-07 15:39:07.158 Mixer unable to find control PCM
2009-01-07 15:39:07.196 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-07 15:39:07.268 OSD Theme Dimensions W: 1280 H: 720
2009-01-07 15:39:07.648 TV: Changing from None to WatchingLiveTV
2009-01-07 15:39:07.655 Realtime priority would require SUID as root.
2009-01-07 15:39:07.757 Video timing method: USleep with busy wait
2009-01-07 15:39:14.325 Mixer unable to find control PCM
2009-01-07 15:39:14.325 Mixer unable to find control PCM
2009-01-07 15:39:15.381 NVP: prebuffering pause
2009-01-07 15:39:15.461 WriteAudio: buffer underrun
2009-01-07 15:39:17.431 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:39:19.486 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:39:20.421 Mixer unable to find control PCM
2009-01-07 15:39:20.421 Mixer unable to find control PCM
2009-01-07 15:39:30.664 Mixer unable to find control PCM
2009-01-07 15:39:30.665 Mixer unable to find control PCM
2009-01-07 15:39:31.578 NVP: prebuffering pause
2009-01-07 15:39:31.624 WriteAudio: buffer underrun
2009-01-07 15:39:33.631 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:39:35.686 NVP: Prebuffer wait timed out 10 times.
2009-01-07 15:39:36.765 Mixer unable to find control PCM
2009-01-07 15:39:36.765 Mixer unable to find control PCM
2009-01-07 15:39:47.484 TV: Attempting to change from WatchingLiveTV to None
2009-01-07 15:39:47.908 TV: Changing from WatchingLiveTV to None
2009-01-07 15:39:47.988 DPMS Reactivated.
2009-01-07 15:41:30.399 Received a remote 'Clear Cache' request
2009-01-07 15:41:35.570 TV: Attempting to change from None to WatchingLiveTV
2009-01-07 15:41:35.571 Using protocol version 40
2009-01-07 15:41:46.284 RingBuf(/var/lib/mythtv/recordings/118_20090107154138.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/118_20090107154138.mpg'.
2009-01-07 15:41:46.290 DPMS Deactivated 
2009-01-07 15:41:46.309 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/118_20090107154138.mpg
2009-01-07 15:41:46.309 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-01-07 15:41:51.113 TV Error: LiveTV not successfully started
2009-01-07 15:41:51.207 DPMS Reactivated.
2009-01-07 15:42:14.569 Deleting UPnP client...
```


```
My backend log:-

2009-01-07 07:40:45.699 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 07:41:13.170 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 07:41:13.175 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 07:55:45.732 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 08:10:45.767 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 08:11:17.178 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 08:11:17.183 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 08:25:45.798 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 08:40:45.828 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 08:41:19.186 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 08:41:19.192 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 08:55:45.862 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 09:10:45.895 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 09:11:23.194 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 09:11:23.199 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 09:25:45.929 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 09:40:45.963 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 09:41:27.202 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 09:41:27.207 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 09:55:45.997 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 10:10:46.031 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 10:11:28.209 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 10:11:28.216 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 10:25:46.067 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 10:40:46.098 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 10:41:34.218 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 10:41:34.224 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 10:55:46.133 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 11:10:46.168 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 11:11:41.226 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 11:11:41.229 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 11:25:46.204 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 11:40:46.239 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 11:41:44.232 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 11:41:44.240 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 11:55:46.273 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 12:10:46.307 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 12:11:47.242 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 12:11:47.248 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 12:25:46.340 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 12:40:46.375 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 12:41:53.250 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 12:41:53.256 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 12:55:46.409 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 13:10:46.443 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 13:11:53.258 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 13:11:53.264 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 13:25:46.477 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 13:30:04.209 MainServer::HandleAnnounce Monitor
2009-01-07 13:30:04.215 adding: tellybox as a client (events: 0)
2009-01-07 13:30:08.471 MainServer::HandleAnnounce Monitor
2009-01-07 13:30:08.475 adding: tellybox as a client (events: 0)
2009-01-07 13:30:13.330 MainServer::HandleAnnounce Monitor
2009-01-07 13:30:13.335 adding: tellybox as a client (events: 0)
2009-01-07 13:30:46.893 MainServer::HandleAnnounce Monitor
2009-01-07 13:30:46.899 adding: tellybox as a client (events: 0)
2009-01-07 13:30:47.013 MythSocket(8e58f60:-1): writeStringList: Error, socket went unconnected.
2009-01-07 13:30:54.330 Reschedule requested for id 0.
2009-01-07 13:30:54.527 Scheduled 3 items in 0.2 = 0.01 match + 0.19 place
2009-01-07 13:31:08.618 MainServer::HandleAnnounce Monitor
2009-01-07 13:31:08.714 adding: tellybox as a client (events: 0)
2009-01-07 13:31:16.084 Reschedule requested for id 0.
2009-01-07 13:31:16.121 Scheduled 3 items in 0.0 = 0.02 match + 0.02 place
2009-01-07 13:31:29.132 MainServer::HandleAnnounce Monitor
2009-01-07 13:31:29.160 adding: tellybox as a client (events: 0)
2009-01-07 13:36:12.369 MainServer::HandleAnnounce Monitor
2009-01-07 13:36:12.376 adding: tellybox as a client (events: 0)
2009-01-07 14:35:36.398 Using runtime prefix = /usr
2009-01-07 14:35:36.405 Empty LocalHostName.
2009-01-07 14:35:36.407 Using localhost value of tellybox
2009-01-07 14:35:36.428 New DB connection, total: 1
2009-01-07 14:35:36.434 Connected to database 'mythconverg' at host: localhost
2009-01-07 14:35:36.435 Closing DB connection named 'DBManager0'
2009-01-07 14:35:36.438 Connected to database 'mythconverg' at host: localhost
2009-01-07 14:35:36.442 New DB connection, total: 2
2009-01-07 14:35:36.445 Connected to database 'mythconverg' at host: localhost
2009-01-07 14:35:36.452 Current Schema Version: 1214
Starting up as the master server.
2009-01-07 14:35:36.474 New DB connection, total: 3
2009-01-07 14:35:36.476 Connected to database 'mythconverg' at host: localhost
2009-01-07 14:35:37.579 ret_pid(0) child(14392) status(0x0)
2009-01-07 14:35:38.583 ret_pid(0) child(14392) status(0x0)
2009-01-07 14:35:39.584 ret_pid(14392) child(14392) status(0x0)
2009-01-07 14:35:39.588 External Tuning program exited with no error
2009-01-07 14:35:39.617 New DB scheduler connection
2009-01-07 14:35:39.619 Connected to database 'mythconverg' at host: localhost
2009-01-07 14:35:40.884 Main::Registering HttpStatus Extension
2009-01-07 14:35:40.888 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-07 14:35:40.889 Enabled verbose msgs:  important general
2009-01-07 14:35:40.895 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 14:35:42.624 Reschedule requested for id -1.
2009-01-07 14:35:42.742 Scheduled 3 items in 0.1 = 0.08 match + 0.04 place
2009-01-07 14:35:42.751 Seem to be woken up by USER
2009-01-07 14:35:49.677 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 14:35:49.685 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 14:36:59.626 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 14:51:59.680 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 15:05:52.688 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 15:05:52.690 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 15:06:59.723 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 15:17:23.503 MainServer::HandleAnnounce Monitor
2009-01-07 15:17:26.154 adding: tellybox as a client (events: 0)
2009-01-07 15:17:26.156 MainServer::HandleAnnounce Monitor
2009-01-07 15:17:26.157 adding: tellybox as a client (events: 1)
2009-01-07 15:17:26.159 Reschedule requested for id -1.
2009-01-07 15:17:26.284 Scheduled 3 items in 0.1 = 0.01 match + 0.12 place
2009-01-07 15:21:59.767 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 15:31:44.560 MainServer::HandleAnnounce Monitor
2009-01-07 15:31:44.568 adding: tellybox as a client (events: 0)
2009-01-07 15:31:49.277 MainServer::HandleAnnounce Monitor
2009-01-07 15:31:49.282 adding: tellybox as a client (events: 0)
2009-01-07 15:32:01.418 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:01.423 adding: tellybox as a client (events: 0)
2009-01-07 15:32:09.092 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:09.099 adding: tellybox as a client (events: 0)
2009-01-07 15:32:09.926 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:09.929 adding: tellybox as a client (events: 0)
2009-01-07 15:32:15.772 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:15.774 adding: tellybox as a client (events: 0)
2009-01-07 15:32:17.431 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:17.435 adding: tellybox as a client (events: 0)
2009-01-07 15:32:18.539 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:18.542 adding: tellybox as a client (events: 0)
2009-01-07 15:32:19.615 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:19.618 adding: tellybox as a client (events: 0)
2009-01-07 15:32:20.272 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:20.276 adding: tellybox as a client (events: 0)
2009-01-07 15:32:21.633 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:21.637 adding: tellybox as a client (events: 0)
2009-01-07 15:32:21.697 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:21.697 adding: tellybox as a client (events: 0)
2009-01-07 15:32:23.074 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:23.081 adding: tellybox as a client (events: 0)
2009-01-07 15:32:23.263 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:23.266 adding: tellybox as a client (events: 0)
2009-01-07 15:32:23.378 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:23.380 adding: tellybox as a client (events: 0)
2009-01-07 15:32:23.415 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:23.417 adding: tellybox as a client (events: 0)
2009-01-07 15:32:24.918 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:24.920 adding: tellybox as a client (events: 0)
2009-01-07 15:32:45.161 MainServer::HandleAnnounce Monitor
2009-01-07 15:32:45.164 adding: tellybox as a client (events: 0)
2009-01-07 15:33:07.793 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:07.796 adding: tellybox as a client (events: 0)
2009-01-07 15:33:37.653 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:37.657 adding: tellybox as a client (events: 0)
2009-01-07 15:33:45.326 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:45.329 adding: tellybox as a client (events: 0)
2009-01-07 15:33:46.958 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:46.961 adding: tellybox as a client (events: 0)
2009-01-07 15:33:48.397 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:48.404 adding: tellybox as a client (events: 0)
2009-01-07 15:33:48.462 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:48.463 adding: tellybox as a client (events: 0)
2009-01-07 15:33:49.156 MainServer::HandleAnnounce Monitor
2009-01-07 15:33:49.160 adding: tellybox as a client (events: 0)
2009-01-07 15:35:13.570 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:13.571 adding: tellybox as a client (events: 0)
2009-01-07 15:35:19.152 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:19.155 adding: tellybox as a client (events: 0)
2009-01-07 15:35:24.900 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:24.901 adding: tellybox as a client (events: 0)
2009-01-07 15:35:29.932 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:29.937 adding: tellybox as a client (events: 0)
2009-01-07 15:35:32.487 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:32.491 adding: tellybox as a client (events: 0)
2009-01-07 15:35:33.170 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:33.174 adding: tellybox as a client (events: 0)
2009-01-07 15:35:34.835 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:34.839 adding: tellybox as a client (events: 0)
2009-01-07 15:35:35.005 MainServer::HandleAnnounce Monitor
2009-01-07 15:35:35.009 adding: tellybox as a client (events: 0)
2009-01-07 15:35:57.693 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 15:35:57.699 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 15:36:06.581 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:06.587 adding: tellybox as a client (events: 0)
2009-01-07 15:36:11.746 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:11.747 adding: tellybox as a client (events: 0)
2009-01-07 15:36:17.831 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:17.832 adding: tellybox as a client (events: 0)
2009-01-07 15:36:22.478 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:22.481 adding: tellybox as a client (events: 0)
2009-01-07 15:36:25.951 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:25.955 adding: tellybox as a client (events: 0)
2009-01-07 15:36:25.984 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:25.985 adding: tellybox as a client (events: 0)
2009-01-07 15:36:28.861 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:28.865 adding: tellybox as a client (events: 0)
2009-01-07 15:36:28.897 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:28.898 adding: tellybox as a client (events: 0)
2009-01-07 15:36:29.602 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:29.608 adding: tellybox as a client (events: 0)
2009-01-07 15:36:48.574 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:48.575 adding: tellybox as a client (events: 0)
2009-01-07 15:36:48.577 MainServer::HandleAnnounce Monitor
2009-01-07 15:36:48.578 adding: tellybox as a client (events: 1)
2009-01-07 15:36:48.586 MainServer::HandleAnnounce Playback
2009-01-07 15:36:48.587 adding: tellybox as a client (events: 0)
2009-01-07 15:36:48.591 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:36:48.598 TVRec(1): HW Tuner: 1->1
2009-01-07 15:36:49.641 ret_pid(0) child(14833) status(0x0)
2009-01-07 15:36:50.644 ret_pid(0) child(14833) status(0x0)
2009-01-07 15:36:51.645 ret_pid(14833) child(14833) status(0x0)
2009-01-07 15:36:51.648 External Tuning program exited with no error
2009-01-07 15:36:52.846 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2009-01-07 15:36:52.847 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:36:59.813 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-07 15:37:17.099 TVRec(1): HW Tuner: 1->1
2009-01-07 15:37:18.310 ret_pid(0) child(14848) status(0x0)
2009-01-07 15:37:19.314 ret_pid(0) child(14848) status(0x0)
2009-01-07 15:37:20.317 ret_pid(14848) child(14848) status(0x0)
2009-01-07 15:37:20.321 External Tuning program exited with no error
2009-01-07 15:37:20.346 Finished recording Cold Case "Churchgoing People": channel 106
2009-01-07 15:37:21.467 Finished recording Cold Case "Churchgoing People": channel 106
2009-01-07 15:37:21.609 TVRec(1): RingBufferChanged()
2009-01-07 15:37:21.617 Finished recording Cold Case "Churchgoing People": channel 106
2009-01-07 15:37:21.632 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-07 15:37:21.734 Using runtime prefix = /usr
2009-01-07 15:37:21.738 Empty LocalHostName.
2009-01-07 15:37:21.739 Using localhost value of tellybox
2009-01-07 15:37:21.749 New DB connection, total: 1
2009-01-07 15:37:21.756 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:21.758 Closing DB connection named 'DBManager0'
2009-01-07 15:37:21.761 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:21.766 New DB connection, total: 2
2009-01-07 15:37:21.775 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:21.784 Current Schema Version: 1214
2009-01-07 15:37:24.270 AFD: Opened codec 0x98f07d0, id(MPEG2VIDEO) type(Video)
2009-01-07 15:37:24.288 AFD: codec MP2 has 2 channels
2009-01-07 15:37:24.289 AFD: Opened codec 0x98f1c80, id(MP2) type(Audio)
2009-01-07 15:37:24.442 Preview: Grabbed preview '/var/lib/mythtv/recordings/106_20090107153651.mpg' 720x576@64s
2009-01-07 15:37:33.616 TVRec(1): HW Tuner: 1->1
2009-01-07 15:37:34.722 ret_pid(0) child(14859) status(0x0)
2009-01-07 15:37:35.725 ret_pid(0) child(14859) status(0x0)
2009-01-07 15:37:36.728 ret_pid(14859) child(14859) status(0x0)
2009-01-07 15:37:36.731 External Tuning program exited with no error
2009-01-07 15:37:36.769 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:37:37.820 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:37:37.921 TVRec(1): RingBufferChanged()
2009-01-07 15:37:37.928 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:37:37.946 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-07 15:37:38.077 Using runtime prefix = /usr
2009-01-07 15:37:38.084 Empty LocalHostName.
2009-01-07 15:37:38.085 Using localhost value of tellybox
2009-01-07 15:37:38.095 New DB connection, total: 1
2009-01-07 15:37:38.101 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:38.104 Closing DB connection named 'DBManager0'
2009-01-07 15:37:38.106 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:38.111 New DB connection, total: 2
2009-01-07 15:37:38.113 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:38.119 Current Schema Version: 1214
2009-01-07 15:37:40.595 AFD: Opened codec 0x871d840, id(MPEG2VIDEO) type(Video)
2009-01-07 15:37:40.607 AFD: codec MP2 has 2 channels
2009-01-07 15:37:40.608 AFD: Opened codec 0x871ecf0, id(MP2) type(Audio)
2009-01-07 15:37:40.761 Preview: Grabbed preview '/var/lib/mythtv/recordings/110_20090107153720.mpg' 720x576@64s
2009-01-07 15:37:42.726 TVRec(1): HW Tuner: 1->1
2009-01-07 15:37:43.837 ret_pid(0) child(14870) status(0x0)
2009-01-07 15:37:44.843 ret_pid(0) child(14870) status(0x0)
2009-01-07 15:37:45.847 ret_pid(14870) child(14870) status(0x0)
2009-01-07 15:37:45.851 External Tuning program exited with no error
2009-01-07 15:37:45.878 Finished recording Ray Mears's Extreme Survival "Australian Outback": channel 111
2009-01-07 15:37:46.919 Finished recording Ray Mears's Extreme Survival "Australian Outback": channel 111
2009-01-07 15:37:47.042 TVRec(1): RingBufferChanged()
2009-01-07 15:37:47.049 Finished recording Ray Mears's Extreme Survival "Australian Outback": channel 111
2009-01-07 15:37:47.073 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-07 15:37:47.167 Using runtime prefix = /usr
2009-01-07 15:37:47.170 Empty LocalHostName.
2009-01-07 15:37:47.171 Using localhost value of tellybox
2009-01-07 15:37:47.181 New DB connection, total: 1
2009-01-07 15:37:47.187 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:47.190 Closing DB connection named 'DBManager0'
2009-01-07 15:37:47.193 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:47.199 New DB connection, total: 2
2009-01-07 15:37:47.201 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:37:47.207 Current Schema Version: 1214
2009-01-07 15:37:49.705 AFD: Opened codec 0x8b3c060, id(MPEG2VIDEO) type(Video)
2009-01-07 15:37:49.716 AFD: codec MP2 has 2 channels
2009-01-07 15:37:49.717 AFD: Opened codec 0x8b3d510, id(MP2) type(Audio)
2009-01-07 15:37:49.877 Preview: Grabbed preview '/var/lib/mythtv/recordings/111_20090107153736.mpg' 720x576@64s
2009-01-07 15:38:35.577 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:38:35.954 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:38:59.855 Expiring 14 MBytes for 106 @ Wed Jan 7 15:00:00 2009 => Cold Case "Churchgoing People"
2009-01-07 15:39:01.077 MainServer::HandleAnnounce Playback
2009-01-07 15:39:01.083 adding: tellybox as a client (events: 0)
2009-01-07 15:39:01.086 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:39:01.094 TVRec(1): HW Tuner: 1->1
2009-01-07 15:39:02.133 ret_pid(0) child(14887) status(0x0)
2009-01-07 15:39:03.139 ret_pid(0) child(14887) status(0x0)
2009-01-07 15:39:04.140 ret_pid(14887) child(14887) status(0x0)
2009-01-07 15:39:04.143 External Tuning program exited with no error
2009-01-07 15:39:04.154 New DB connection, total: 4
2009-01-07 15:39:04.155 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:05.217 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2009-01-07 15:39:05.219 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:39:14.430 TVRec(1): HW Tuner: 1->1
2009-01-07 15:39:15.556 ret_pid(0) child(15024) status(0x0)
2009-01-07 15:39:16.562 ret_pid(0) child(15024) status(0x0)
2009-01-07 15:39:17.565 ret_pid(15024) child(15024) status(0x0)
2009-01-07 15:39:17.568 External Tuning program exited with no error
2009-01-07 15:39:17.584 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:39:18.662 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:39:18.751 TVRec(1): RingBufferChanged()
2009-01-07 15:39:18.760 Finished recording The Brittas Empire "An Inspector Calls": channel 110
2009-01-07 15:39:18.776 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-07 15:39:18.921 Using runtime prefix = /usr
2009-01-07 15:39:18.927 Empty LocalHostName.
2009-01-07 15:39:18.928 Using localhost value of tellybox
2009-01-07 15:39:18.938 New DB connection, total: 1
2009-01-07 15:39:18.945 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:18.947 Closing DB connection named 'DBManager0'
2009-01-07 15:39:18.949 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:18.954 New DB connection, total: 2
2009-01-07 15:39:18.958 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:18.964 Current Schema Version: 1214
2009-01-07 15:39:21.468 AFD: Opened codec 0x8325840, id(MPEG2VIDEO) type(Video)
2009-01-07 15:39:21.479 AFD: codec MP2 has 2 channels
2009-01-07 15:39:21.480 AFD: Opened codec 0x8326cf0, id(MP2) type(Audio)
2009-01-07 15:39:21.652 Preview: Grabbed preview '/var/lib/mythtv/recordings/110_20090107153904.mpg' 720x576@64s
2009-01-07 15:39:30.771 TVRec(1): HW Tuner: 1->1
2009-01-07 15:39:31.909 ret_pid(0) child(15036) status(0x0)
2009-01-07 15:39:32.913 ret_pid(0) child(15036) status(0x0)
2009-01-07 15:39:33.914 ret_pid(15036) child(15036) status(0x0)
2009-01-07 15:39:33.917 External Tuning program exited with no error
2009-01-07 15:39:33.951 Finished recording Ray Mears's Extreme Survival "Australian Outback": channel 111
2009-01-07 15:39:34.997 Finished recording Ray Mears's Extreme Survival "Australian Outback": channel 111
2009-01-07 15:39:35.113 TVRec(1): RingBufferChanged()
2009-01-07 15:39:35.122 Finished recording Ray Mears's Extreme Survival "Australian Outback": channel 111
2009-01-07 15:39:35.136 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-07 15:39:35.255 Using runtime prefix = /usr
2009-01-07 15:39:35.260 Empty LocalHostName.
2009-01-07 15:39:35.261 Using localhost value of tellybox
2009-01-07 15:39:35.272 New DB connection, total: 1
2009-01-07 15:39:35.278 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:35.280 Closing DB connection named 'DBManager0'
2009-01-07 15:39:35.282 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:35.286 New DB connection, total: 2
2009-01-07 15:39:35.290 Connected to database 'mythconverg' at host: localhost
2009-01-07 15:39:35.295 Current Schema Version: 1214
2009-01-07 15:39:37.785 AFD: Opened codec 0x8e7a060, id(MPEG2VIDEO) type(Video)
2009-01-07 15:39:37.796 AFD: codec MP2 has 2 channels
2009-01-07 15:39:37.797 AFD: Opened codec 0x8e7b510, id(MP2) type(Audio)
2009-01-07 15:39:37.934 Preview: Grabbed preview '/var/lib/mythtv/recordings/111_20090107153917.mpg' 720x576@64s
2009-01-07 15:39:47.512 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:39:47.871 Finished recording The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!": channel 118
2009-01-07 15:40:59.868 Expiring 7 MBytes for 110 @ Wed Jan 7 15:00:00 2009 => The Brittas Empire "An Inspector Calls"
2009-01-07 15:40:59.881 Expiring 2 MBytes for 111 @ Wed Jan 7 15:20:00 2009 => Ray Mears's Extreme Survival "Australian Outback"
2009-01-07 15:40:59.883 Expiring 29 MBytes for 110 @ Wed Jan 7 15:00:00 2009 => The Brittas Empire "An Inspector Calls"
2009-01-07 15:40:59.888 Expiring 5 MBytes for 110 @ Wed Jan 7 15:00:00 2009 => The Brittas Empire "An Inspector Calls"
2009-01-07 15:41:35.571 MainServer::HandleAnnounce Playback
2009-01-07 15:41:35.575 adding: tellybox as a client (events: 0)
2009-01-07 15:41:35.578 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:41:35.585 TVRec(1): HW Tuner: 1->1
2009-01-07 15:41:36.627 ret_pid(0) child(15052) status(0x0)
2009-01-07 15:41:37.631 ret_pid(0) child(15052) status(0x0)
2009-01-07 15:41:38.634 ret_pid(15052) child(15052) status(0x0)
2009-01-07 15:41:38.637 External Tuning program exited with no error
2009-01-07 15:41:39.775 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:41:45.336 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:41:46.311 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:41:50.892 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:41:51.103 Finished recording The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!": channel 118
2009-01-07 15:42:42.692 MainServer::HandleAnnounce Monitor
2009-01-07 15:42:42.706 adding: tellybox as a client (events: 0)
2009-01-07 15:42:42.712 MainServer::HandleAnnounce Monitor
2009-01-07 15:42:42.713 adding: tellybox as a client (events: 1)
2009-01-07 15:42:42.719 MainServer::HandleAnnounce Playback
2009-01-07 15:42:42.720 adding: tellybox as a client (events: 0)
2009-01-07 15:42:42.726 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:42:42.732 TVRec(1): HW Tuner: 1->1
2009-01-07 15:42:43.775 ret_pid(0) child(15109) status(0x0)
2009-01-07 15:42:44.778 ret_pid(0) child(15109) status(0x0)
2009-01-07 15:42:45.781 ret_pid(15109) child(15109) status(0x0)
2009-01-07 15:42:45.782 External Tuning program exited with no error
2009-01-07 15:42:46.863 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:42:52.404 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:42:53.418 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:42:57.960 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:42:58.171 Finished recording The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!": channel 118
2009-01-07 15:42:59.895 Expiring 7 MBytes for 111 @ Wed Jan 7 15:20:00 2009 => Ray Mears's Extreme Survival "Australian Outback"
2009-01-07 15:42:59.907 Expiring 7 MBytes for 118 @ Wed Jan 7 14:35:00 2009 => The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!"
2009-01-07 15:44:19.715 MainServer::HandleAnnounce Playback
2009-01-07 15:44:19.719 adding: tellybox as a client (events: 0)
2009-01-07 15:44:19.722 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:44:19.735 TVRec(1): HW Tuner: 1->1
2009-01-07 15:44:20.775 ret_pid(0) child(15123) status(0x0)
2009-01-07 15:44:21.776 ret_pid(0) child(15123) status(0x0)
2009-01-07 15:44:22.779 ret_pid(15123) child(15123) status(0x0)
2009-01-07 15:44:22.781 External Tuning program exited with no error
2009-01-07 15:44:23.915 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:44:29.484 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:44:30.458 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:44:35.040 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:44:35.251 Finished recording The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!": channel 118
2009-01-07 15:44:59.923 Expiring 0 MBytes for 118 @ Wed Jan 7 14:35:00 2009 => The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!"
2009-01-07 15:44:59.928 Expiring 0 MBytes for 118 @ Wed Jan 7 14:35:00 2009 => The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!"
2009-01-07 15:46:59.940 Expiring 0 MBytes for 118 @ Wed Jan 7 14:35:00 2009 => The Jeremy Kyle Show "You've Cheated Four Times but Asked Me to Do a Lie Detector Test!"
2009-01-07 15:48:06.871 MainServer::HandleAnnounce Playback
2009-01-07 15:48:06.875 adding: tellybox as a client (events: 0)
2009-01-07 15:48:06.878 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:48:06.890 TVRec(1): HW Tuner: 1->1
2009-01-07 15:48:07.932 ret_pid(0) child(15137) status(0x0)
2009-01-07 15:48:08.935 ret_pid(0) child(15137) status(0x0)
2009-01-07 15:48:09.938 ret_pid(15137) child(15137) status(0x0)
2009-01-07 15:48:09.939 External Tuning program exited with no error
2009-01-07 15:48:11.068 MPEGRec(/dev/video0) Warning: Stream type 'MPEG-2 TS'
			is not supported by ivtv driver, using 'MPEG-2 PS' instead.
2009-01-07 15:48:11.071 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:48:16.620 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:48:17.616 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:48:22.176 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:48:22.387 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:49:35.853 MainServer::HandleAnnounce Playback
2009-01-07 15:49:35.857 adding: tellybox as a client (events: 0)
2009-01-07 15:49:35.859 TVRec(1): Changing from None to WatchingLiveTV

2009-01-07 15:49:35.863 TVRec(1): HW Tuner: 1->1
2009-01-07 15:49:36.911 ret_pid(0) child(15148) status(0x0)
2009-01-07 15:49:37.914 ret_pid(0) child(15148) status(0x0)
2009-01-07 15:49:38.918 ret_pid(15148) child(15148) status(0x0)
2009-01-07 15:49:38.921 External Tuning program exited with no error
2009-01-07 15:49:39.993 MPEGRec(/dev/video0) Warning: Stream type 'MPEG-2 TS'
			is not supported by ivtv driver, using 'MPEG-2 PS' instead.
2009-01-07 15:49:39.995 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:49:45.536 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:49:46.523 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:49:51.092 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:49:51.302 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:50:59.962 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 15:51:39.540 MainServer::HandleAnnounce Playback
2009-01-07 15:51:39.551 adding: tellybox as a client (events: 0)
2009-01-07 15:51:39.553 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:51:39.559 TVRec(1): HW Tuner: 1->1
2009-01-07 15:51:40.600 ret_pid(0) child(15160) status(0x0)
2009-01-07 15:51:41.603 ret_pid(0) child(15160) status(0x0)
2009-01-07 15:51:42.606 ret_pid(15160) child(15160) status(0x0)
2009-01-07 15:51:42.610 External Tuning program exited with no error
2009-01-07 15:51:43.750 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:51:49.308 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:51:50.294 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:51:54.860 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:51:55.070 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:51:59.975 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 15:53:30.718 MainServer::HandleAnnounce Playback
2009-01-07 15:53:30.723 adding: tellybox as a client (events: 0)
2009-01-07 15:53:30.726 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:53:30.737 TVRec(1): HW Tuner: 1->1
2009-01-07 15:53:31.778 ret_pid(0) child(15171) status(0x0)
2009-01-07 15:53:32.782 ret_pid(0) child(15171) status(0x0)
2009-01-07 15:53:33.785 ret_pid(15171) child(15171) status(0x0)
2009-01-07 15:53:33.788 External Tuning program exited with no error
2009-01-07 15:53:34.899 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:53:40.460 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:53:41.430 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:53:46.020 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:53:46.231 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:54:00.008 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 15:54:00.020 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 15:54:48.616 MainServer::HandleAnnounce Playback
2009-01-07 15:54:48.620 adding: tellybox as a client (events: 0)
2009-01-07 15:54:48.623 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:54:48.633 TVRec(1): HW Tuner: 1->1
2009-01-07 15:54:49.676 ret_pid(0) child(15185) status(0x0)
2009-01-07 15:54:50.677 ret_pid(0) child(15185) status(0x0)
2009-01-07 15:54:51.681 ret_pid(15185) child(15185) status(0x0)
2009-01-07 15:54:51.684 External Tuning program exited with no error
2009-01-07 15:54:52.824 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:54:58.380 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:54:59.366 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:55:03.936 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:55:04.146 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:56:00.026 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 15:56:00.036 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 15:57:29.978 MainServer::HandleAnnounce Playback
2009-01-07 15:57:29.983 adding: tellybox as a client (events: 0)
2009-01-07 15:57:29.985 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:57:29.998 TVRec(1): HW Tuner: 1->1
2009-01-07 15:57:31.039 ret_pid(0) child(15198) status(0x0)
2009-01-07 15:57:32.040 ret_pid(0) child(15198) status(0x0)
2009-01-07 15:57:33.043 ret_pid(15198) child(15198) status(0x0)
2009-01-07 15:57:33.045 External Tuning program exited with no error
2009-01-07 15:57:34.179 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:57:39.740 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:57:40.724 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:57:45.296 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:57:45.507 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:58:28.947 MainServer::HandleAnnounce Playback
2009-01-07 15:58:28.951 adding: tellybox as a client (events: 0)
2009-01-07 15:58:28.953 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:58:28.965 TVRec(1): HW Tuner: 1->1
2009-01-07 15:58:30.009 ret_pid(0) child(15209) status(0x0)
2009-01-07 15:58:31.012 ret_pid(0) child(15209) status(0x0)
2009-01-07 15:58:32.015 ret_pid(15209) child(15209) status(0x0)
2009-01-07 15:58:32.018 External Tuning program exited with no error
2009-01-07 15:58:33.130 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:58:38.668 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:58:39.659 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 15:58:44.224 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:58:44.434 Finished recording The Ricki Lake Show: channel 118
2009-01-07 15:59:46.124 MainServer::HandleAnnounce Playback
2009-01-07 15:59:46.131 adding: tellybox as a client (events: 0)
2009-01-07 15:59:46.139 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 15:59:46.143 TVRec(1): HW Tuner: 1->1
2009-01-07 15:59:47.183 ret_pid(0) child(15220) status(0x0)
2009-01-07 15:59:48.186 ret_pid(0) child(15220) status(0x0)
2009-01-07 15:59:49.189 ret_pid(15220) child(15220) status(0x0)
2009-01-07 15:59:49.192 External Tuning program exited with no error
2009-01-07 15:59:50.306 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 15:59:55.868 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 15:59:56.836 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 16:00:00.047 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:00:00.058 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:00:01.424 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:00:01.638 Finished recording The Ricki Lake Show: channel 118
2009-01-07 16:00:41.802 MainServer::HandleAnnounce Playback
2009-01-07 16:00:41.807 adding: tellybox as a client (events: 0)
2009-01-07 16:00:41.809 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 16:00:41.821 TVRec(1): HW Tuner: 1->1
2009-01-07 16:00:42.861 ret_pid(0) child(15233) status(0x0)
2009-01-07 16:00:43.864 ret_pid(0) child(15233) status(0x0)
2009-01-07 16:00:44.868 ret_pid(15233) child(15233) status(0x0)
2009-01-07 16:00:44.871 External Tuning program exited with no error
2009-01-07 16:00:46.007 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 16:00:51.564 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:00:52.547 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 16:00:57.116 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:00:57.326 Finished recording The Ricki Lake Show: channel 118
2009-01-07 16:02:00.064 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:02:00.078 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:02:20.019 MainServer::HandleAnnounce Playback
2009-01-07 16:02:20.021 adding: tellybox as a client (events: 0)
2009-01-07 16:02:20.024 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 16:02:20.037 TVRec(1): HW Tuner: 1->1
2009-01-07 16:02:21.080 ret_pid(0) child(15246) status(0x0)
2009-01-07 16:02:22.083 ret_pid(0) child(15246) status(0x0)
2009-01-07 16:02:23.084 ret_pid(15246) child(15246) status(0x0)
2009-01-07 16:02:23.087 External Tuning program exited with no error
2009-01-07 16:02:24.223 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 16:02:29.780 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:02:30.768 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 16:02:35.336 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:02:35.547 Finished recording The Ricki Lake Show: channel 118
2009-01-07 16:04:00.084 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:04:05.452 MainServer::HandleAnnounce Playback
2009-01-07 16:04:05.453 adding: tellybox as a client (events: 0)
2009-01-07 16:04:05.455 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 16:04:05.459 TVRec(1): HW Tuner: 1->1
2009-01-07 16:04:06.503 ret_pid(0) child(15258) status(0x0)
2009-01-07 16:04:07.504 ret_pid(0) child(15258) status(0x0)
2009-01-07 16:04:08.508 ret_pid(15258) child(15258) status(0x0)
2009-01-07 16:04:08.511 External Tuning program exited with no error
2009-01-07 16:04:09.651 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 16:04:15.208 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:04:16.198 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 16:04:20.764 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:04:20.975 Finished recording The Ricki Lake Show: channel 118
2009-01-07 16:06:00.096 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:06:00.702 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-01-07 16:06:00.708 UPnpMedia: BuildMediaMap Done. Found 0 objects
2009-01-07 16:07:00.114 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-07 16:12:56.305 MainServer::HandleAnnounce Monitor
2009-01-07 16:12:56.311 adding: tellybox as a client (events: 0)
2009-01-07 16:12:56.313 MainServer::HandleAnnounce Monitor
2009-01-07 16:12:56.314 adding: tellybox as a client (events: 1)
2009-01-07 16:12:56.331 MainServer::HandleAnnounce Playback
2009-01-07 16:12:56.332 adding: tellybox as a client (events: 0)
2009-01-07 16:12:56.334 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 16:12:56.345 TVRec(1): HW Tuner: 1->1
2009-01-07 16:12:57.388 ret_pid(0) child(15422) status(0x0)
2009-01-07 16:12:58.391 ret_pid(0) child(15422) status(0x0)
2009-01-07 16:12:59.395 ret_pid(15422) child(15422) status(0x0)
2009-01-07 16:12:59.398 External Tuning program exited with no error
2009-01-07 16:13:00.513 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 16:13:06.048 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:13:07.072 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 16:13:11.608 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:13:11.818 Finished recording The Ricki Lake Show: channel 118
2009-01-07 16:14:00.152 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:16:35.539 MainServer::HandleAnnounce Playback
2009-01-07 16:16:35.541 adding: tellybox as a client (events: 0)
2009-01-07 16:16:35.545 TVRec(1): Changing from None to WatchingLiveTV
2009-01-07 16:16:35.559 TVRec(1): HW Tuner: 1->1
2009-01-07 16:16:36.598 ret_pid(0) child(15435) status(0x0)
2009-01-07 16:16:37.599 ret_pid(0) child(15435) status(0x0)
2009-01-07 16:16:38.603 ret_pid(15435) child(15435) status(0x0)
2009-01-07 16:16:38.606 External Tuning program exited with no error
2009-01-07 16:16:39.747 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-07 16:16:45.312 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:16:46.294 TVRec(1): Changing from WatchingLiveTV to None
2009-01-07 16:16:50.868 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-07 16:16:51.079 Finished recording The Ricki Lake Show: channel 118
2009-01-07 16:18:00.162 Expiring 0 MBytes for 118 @ Wed Jan 7 15:45:00 2009 => The Ricki Lake Show
2009-01-07 16:22:00.182 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

---

### Post by singedwings on 2009-01-09
bump

---

### Post by singedwings on 2009-01-14
bump please anyone!?

---

### Post by singedwings on 2009-01-24
bump

---

### Post by joho500 on 2009-01-25
I'm not sure what caused your problem but I see in your logs that ivtv driver is not responding. I - and several other people - had that problem after upgrading to 8.10. You might install the bleeding edge driver. Look at this post: [http://www.uluga.ubuntuforums.org/showpost.php?p=6096932&postcount=6]("http://www.uluga.ubuntuforums.org/showpost.php?p=6096932&postcount=6")

Joost

---

### Post by singedwings on 2009-01-27
Thank you, thank you, thank you. Updating to the new driver has solved this problem. joho500 you are a star.:D

---

### Post by joho500 on 2009-01-28
You're welcome and thank you. Always nice to hear. ;)

---

