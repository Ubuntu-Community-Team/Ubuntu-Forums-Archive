---
title: "Slow frontend"
date: 2010-12-26
forum: Mythbuntu
---

### Post by macaronij on 2010-12-26
Hi all!
sorry for my english
my problem is that my frontend start _very_ slow
i have mythbuntu 10.04 as backend+frontend and works GREAT
then i have another frontend whit ubuntu 10.04 in a very new pc
the tv and recordings works BUT when i start the program (mythtv) it has a SIGNIFICANT delay... about 1 min
the recordings can be watch inmediatly but live TV takes another minute...the first time i watch it. If i quit then re-select live tv i can see it very fast.

** IT IS NORMAL?**
** if not: how can i solve it?**

---

### Post by ian dobson on 2010-12-26
Hi,

Have a look in your frontend log file (/var/log/mythtv/frontend.log) and have a look where the delays are happening.

LiveTV startup is slow, the backend needs to tune to the channel, start writing the data to the disk, and when enough data is on the disk the frontend can start reading/displaying it. 

Regards
Ian Dobson

---

### Post by macaronij on 2010-12-26
i paste the log, the first bold is when i start the program, the second when i'm waiting for live tv


Starting mythfrontend.real..
2010-12-27 01:23:41.970 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-12-27 01:23:41.992 Using runtime prefix = /usr
2010-12-27 01:23:41.992 Using configuration directory = /home/fgsofia/.mythtv
2010-12-27 01:23:42.765 Empty LocalHostName.
2010-12-27 01:23:42.765 Using localhost value of fgsofia
2010-12-27 01:23:42.765 Testing network connectivity to '192.168.0.105'
2010-12-27 01:23:42.844 New DB connection, total: 1
[B]2010-12-27 01:23:52.895 Unable to connect to database!
2010-12-27 01:23:52.895 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'192.168.0.106' (using password: YES)[/B]


2010-12-27 01:23:52.898 UPnPautoconf() - Found one UPnP backend
2010-12-27 01:23:53.011 Testing network connectivity to '192.168.0.105'
2010-12-27 01:23:53.013 Closing DB connection named 'DBManager0'
2010-12-27 01:24:03.054 Connected to database 'mythconverg' at host: 192.168.0.105
2010-12-27 01:24:03.054 Closing DB connection named 'DBManager0'
2010-12-27 01:24:03.074 ScreenSaverX11Private: Gnome screen saver support enabled
2010-12-27 01:24:03.074 DPMS is active.
2010-12-27 01:24:03.075 Primary screen: 0.
2010-12-27 01:24:13.083 Connected to database 'mythconverg' at host: 192.168.0.105
2010-12-27 01:24:13.084 Using screen 0, 1920x1200 at 0,0
2010-12-27 01:24:13.117 Desktop video mode: 1920x1200 59.952 Hz
2010-12-27 01:24:13.148 MythUI Image Cache size set to 20971520 bytes
2010-12-27 01:24:13.163 AudioPulseUtil: Suspend Success
2010-12-27 01:24:13.164 Enabled verbose msgs:  important general
2010-12-27 01:24:13.212 Primary screen: 0.
2010-12-27 01:24:13.213 Using screen 0, 1920x1200 at 0,0
2010-12-27 01:24:13.228 Using theme base resolution of 1280x720
2010-12-27 01:24:13.249 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No existe el archivo o directorio (2)
2010-12-27 01:24:13.249 JoystickMenuThread Error: Joystick disabled - Failed to read /home/fgsofia/.mythtv/joystickmenurc
2010-12-27 01:24:13.334 Using Frameless Window
2010-12-27 01:24:13.334 Using Full Screen Window
2010-12-27 01:24:13.561 Using the Qt painter
2010-12-27 01:24:13.827 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-27 01:24:14.017 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-27 01:24:14.035 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-27 01:24:14.075 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-27 01:24:14.748 Registering Internal as a media playback plugin.
2010-12-27 01:24:14.749 No plugins directory /usr/lib/mythtv/plugins
2010-12-27 01:24:14.755 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-27 01:24:14.755 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-27 01:24:14.755 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-27 01:24:14.759 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-27 01:24:15.023 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-27 01:24:15.025 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-27 01:24:15.249 MythContext: Connecting to backend server: 192.168.0.105:6543 (try 1 of 1)
2010-12-27 01:24:15.250 Using protocol version 56
2010-12-27 01:24:32.938 TV: Attempting to change from None to WatchingLiveTV
2010-12-27 01:24:32.938 MythContext: Connecting to backend server: 192.168.0.105:6543 (try 1 of 1)
2010-12-27 01:24:32.939 Using protocol version 56
2010-12-27 01:24:32.964 Spawning LiveTV Recorder -- begin
2010-12-27 01:24:33.318 Spawning LiveTV Recorder -- end
2010-12-27 01:24:33.326 ProgramInfo(): Updated pathname '':'' -> '1089_20101227012433.nuv'
2010-12-27 01:24:33.341 We have a playbackURL(myth://192.168.0.105:6543/1089_20101227012433.nuv) & cardtype(V4L)
2010-12-27 01:24:33.399 We have a RingBuffer
2010-12-27 01:24:33.695 AO: Using resampler. From: 44100 to 48000
2010-12-27 01:24:33.703 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-27 01:24:33.704 Opening ALSA audio device 'default'.
2010-12-27 01:24:33.904 AO: Using resampler. From: 44100 to 48000
2010-12-27 01:24:33.904 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-27 01:24:33.904 Opening ALSA audio device 'default'.
2010-12-27 01:24:34.177 AO: Using resampler. From: 44100 to 48000
2010-12-27 01:24:34.177 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-27 01:24:34.177 Opening ALSA audio device 'default'.
2010-12-27 01:24:34.315 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-12-27 01:24:34.325 New DB connection, total: 2
2010-12-27 01:24:34.330 OSD Theme Dimensions W: 1280 H: 720
2010-12-27 01:24:34.803 New DB connection, total: 3
2010-12-27 01:24:34.804 New DB connection, total: 4
[B]2010-12-27 01:24:37.118 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:39.131 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:41.144 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:43.157 NVP(0): Timed out waiting for free video buffers.[/B]
[B]2010-12-27 01:24:44.331 Connected to database 'mythconverg' at host: 192.168.0.105
2010-12-27 01:24:44.335 ProgramInfo(): Updated pathname '':'' -> '1089_20101227012433.nuv'
2010-12-27 01:24:44.339 TV: Changing from None to WatchingLiveTV
2010-12-27 01:24:44.339 TV: State is LiveTV & mctx == ctx
2010-12-27 01:24:44.341 TV: UpdateOSDInput done
2010-12-27 01:24:44.341 TV: UpdateLCD done
2010-12-27 01:24:44.341 TV: ITVRestart done
2010-12-27 01:24:44.364 ScreenSaverX11Private: DPMS Deactivated 1
2010-12-27 01:24:45.170 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:47.183 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:49.196 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:51.209 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:53.222 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:54.336 Connected to database 'mythconverg' at host: 192.168.0.105
2010-12-27 01:24:54.338 Realtime priority would require SUID as root.
2010-12-27 01:24:55.235 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:57.248 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:24:59.261 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:25:01.274 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:25:03.288 NVP(0): Timed out waiting for free video buffers.
2010-12-27 01:25:04.341 Connected to database 'mythconverg' at host: 192.168.0.105
2010-12-27 01:25:04.343 Video timing method: USleep with busy wait[/B]

---

### Post by 4dognight on 2010-12-27
Are you using a wireless connection to your backend from the frontend?

---

### Post by macaronij on 2010-12-27
> **4dognight said:**
> Are you using a wireless connection to your backend from the frontend?

No.

The frontend is in 192.168.0.106 and backend in 192.168.0.105

It seems the frontend first try to connect to the localhost THEN to the backend, in "config->general" i'm sure i have the backend IP address

The second delay is when i choose live tv... i dunno if all the "**Timed out waiting for free video buffers." **are normal

---

### Post by 4dognight on 2010-12-27
2010-12-27 01:24:15.250 Using protocol version 56
2010-12-27 01:24:32.938 TV: Attempting to change from None to WatchingLiveTV

This is a 17 second delay. Can you post the same time frame from the backend log.

---

### Post by macaronij on 2010-12-28
EDIT: sorry i think this is what you need
the backend log when i start my slow frontend

2010-12-29 07:38:28.871 MainServer::ANN Monitor
2010-12-29 07:38:28.897 adding: fgsofia as a client (events: 0)
2010-12-29 07:38:28.906 MainServer::ANN Monitor
2010-12-29 07:38:28.914 adding: fgsofia as a client (events: 1)
2010-12-29 07:38:34.629 MainServer::ANN Playback
2010-12-29 07:38:34.643 adding: fgsofia as a client (events: 0)
2010-12-29 07:38:34.653 TVRec(1): Changing from None to WatchingLiveTV
2010-12-29 07:38:34.663 TVRec(1): HW Tuner: 1->1
2010-12-29 07:38:34.899 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:34.920 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2010-12-29 07:38:34.926 NVR(/dev/video0) Error: Unknown audio codec
2010-12-29 07:38:34.978 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-12-29 07:38:34.986 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:35.003 MainServer::ANN Playback
2010-12-29 07:38:35.043 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:35.060 adding: fgsofia as a client (events: 0)
2010-12-29 07:38:35.077 MainServer::HandleAnnounce FileTransfer
2010-12-29 07:38:35.085 adding: fgsofia as a remote file transfer
2010-12-29 07:38:35.104 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:35.121 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:35.179 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:35.877 RecBase(1:/dev/video0): GetKeyframePositions(0,9223372036854775807,#1) out of 1
2010-12-29 07:38:36.209 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.279 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.336 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.393 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.450 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.507 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.563 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:38:36.643 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:39:31.773 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:39:31.790 TVRec(1): Changing from WatchingLiveTV to None
2010-12-29 07:39:31.799 ProgramInfo(1126_20101229073834.nuv), Error: Unknown type, recording width was 0
2010-12-29 07:39:32.037 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:39:32.049 Finished recording Unknown: channel 1126
2010-12-29 07:39:32.085 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:39:32.233 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'
2010-12-29 07:39:32.241 ProgramInfo(): Updated pathname '':'' -> '1126_20101229073834.nuv'

---

### Post by macaronij on 2011-01-01
still nothing........

---

### Post by ian dobson on 2011-01-01
Hi,

What tuner are you using? The nuv video format is normally only used for old analog tuners that don't have a hardware encoder.

Regards
Ian Dobson

---

### Post by macaronij on 2011-02-21
> **ian dobson said:**
> Hi,

What tuner are you using? The nuv video format is normally only used for old analog tuners that don't have a hardware encoder.

Regards
Ian Dobson

I am using two "old analog tuners that don't have a hardware encoder", but my main question is why the frontend start SO slwo, even before liveTV. Both computers are pretty new, so that is not the problem.

1 minute to connect to the database? it is normal?? in that minute the frontend doesn t start. I just have to wait......
A new log from the start to the conection

Starting mythfrontend.real..
2011-02-21 21:11:22.865 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2011-02-21 21:11:22.903 Using runtime prefix = /usr
2011-02-21 21:11:22.903 Using configuration directory = /home/fgsofia/.mythtv
2011-02-21 21:11:23.633 Empty LocalHostName.
2011-02-21 21:11:23.633 Using localhost value of fgsofia
2011-02-21 21:11:23.634 Testing network connectivity to '192.168.0.105'
2011-02-21 21:11:23.771 New DB connection, total: 1
2011-02-21 21:11:33.808 Unable to connect to database!
2011-02-21 21:11:33.808 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'192.168.0.106' (using password: YES)


2011-02-21 21:11:33.941 UPnPautoconf() - Found one UPnP backend
2011-02-21 21:11:34.157 Testing network connectivity to '192.168.0.105'
2011-02-21 21:11:34.160 Closing DB connection named 'DBManager0'
2011-02-21 21:11:44.199 Connected to database 'mythconverg' at host: 192.168.0.105
2011-02-21 21:11:44.200 Closing DB connection named 'DBManager0'
2011-02-21 21:11:44.228 ScreenSaverX11Private: Gnome screen saver support enabled
2011-02-21 21:11:44.228 DPMS is active.
2011-02-21 21:11:44.258 Primary screen: 0.
2011-02-21 21:11:54.267 Connected to database 'mythconverg' at host: 192.168.0.105
2011-02-21 21:11:54.268 Using screen 0, 1920x1200 at 0,0
2011-02-21 21:11:54.334 Desktop video mode: 1920x1200 59.952 Hz
2011-02-21 21:11:54.450 MythUI Image Cache size set to 20971520 bytes
2011-02-21 21:11:54.476 AudioPulseUtil: Suspend Success
2011-02-21 21:11:54.476 Enabled verbose msgs:  important general
2011-02-21 21:11:54.538 Primary screen: 0.
2011-02-21 21:11:54.539 Using screen 0, 1920x1200 at 0,0
2011-02-21 21:11:54.579 Using theme base resolution of 1280x720
2011-02-21 21:11:54.601 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No existe el archivo o directorio (2)
2011-02-21 21:11:54.601 JoystickMenuThread Error: Joystick disabled - Failed to read /home/fgsofia/.mythtv/joystickmenurc
2011-02-21 21:11:54.674 Using Frameless Window
2011-02-21 21:11:54.674 Using Full Screen Window
2011-02-21 21:11:55.142 Using the Qt painter
2011-02-21 21:11:55.679 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2011-02-21 21:11:55.850 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-02-21 21:11:55.861 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-02-21 21:11:55.874 Current MythTV Schema Version (DBSchemaVer): 1254
2011-02-21 21:11:56.002 New DB connection, total: 2
2011-02-21 21:11:56.666 Registering Internal as a media playback plugin.
2011-02-21 21:11:56.677 No plugins directory /usr/lib/mythtv/plugins
2011-02-21 21:11:56.696 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-21 21:11:56.696 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-21 21:11:56.696 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-21 21:11:56.699 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2011-02-21 21:11:56.808 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-02-21 21:11:56.828 Found mainmenu.xml for theme 'MythCenter-wide'
2011-02-21 21:12:06.011 Connected to database 'mythconverg' at host: 192.168.0.105

---

### Post by macaronij on 2011-02-21
Why i get this error?


2011-02-21 21:11:33.808 Unable to connect to database!
2011-02-21 21:11:33.808 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'192.168.0.106' (using password: YES)


and later it connect?

---

### Post by hpladds on 2011-09-06
Any luck with this? I have a very similar problem.

---

### Post by ian dobson on 2011-09-06
Hi,

Maybe try adding a short delay (sleep 5) to the mythfrontend script. So that mysql/network has a chance to startup before the frontend process starts.

Regards
Ian Dobson

---

