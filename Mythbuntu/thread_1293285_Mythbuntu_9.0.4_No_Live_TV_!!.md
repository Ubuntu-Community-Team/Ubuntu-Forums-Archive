---
title: "Mythbuntu 9.0.4 No Live TV !!"
date: 2009-10-16
forum: Mythbuntu
---

### Post by mars76 on 2009-10-16
HI All,

  I have installed mythbuntu 9.0.4 on a new Hard Drive and i have PVR-150 Tuner Card. After completing the installation the Live TV deos't work.

  When i installed i have created a user "sateesh" ( which is not mythtv ) and i am logging in as that user to start mythtv.

It looks like another user mythtv is also created (which belongs to group mythtv) and is used primarily by mythbackend ( as i opted for default settings during installation)

 Here are my mythlogs.

```

==> /var/log/mythtv/mythbackend.log <==
2009-10-16 20:43:37.406 MainServer::HandleAnnounce Monitor
2009-10-16 20:43:37.407 adding: sateesh-pvr as a client (events: 0)
2009-10-16 20:43:37.409 MainServer::HandleAnnounce Monitor
2009-10-16 20:43:37.410 adding: sateesh-pvr as a client (events: 1)
2009-10-16 20:54:07.723 Using runtime prefix = /usr
2009-10-16 20:54:07.740 Empty LocalHostName.
2009-10-16 20:54:07.741 Using localhost value of sateesh-pvr
2009-10-16 20:54:07.747 New DB connection, total: 1
2009-10-16 20:54:07.753 Connected to database 'mythconverg' at host: localhost
2009-10-16 20:54:07.754 Closing DB connection named 'DBManager0'
2009-10-16 20:54:07.757 Connected to database 'mythconverg' at host: localhost
2009-10-16 20:54:07.762 New DB connection, total: 2
2009-10-16 20:54:07.766 Connected to database 'mythconverg' at host: localhost
2009-10-16 20:54:07.787 Current Schema Version: 1214
Starting up as the master server.
2009-10-16 20:54:07.800 mythbackend: MythBackend started as master server
2009-10-16 20:54:07.812 New DB connection, total: 3
2009-10-16 20:54:07.814 Connected to database 'mythconverg' at host: localhost
2009-10-16 20:54:07.915 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-10-16 20:54:07.946 ChannelBase(1) Warning: Setting start channel 'Please add' failed, 
            selected to 'Please add' on input 'Tuner 1' instead.
2009-10-16 20:54:07.953 New DB scheduler connection
2009-10-16 20:54:07.954 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2009-10-16 20:54:07.986 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-10-16 20:54:07.987 Main::Registering HttpStatus Extension
2009-10-16 20:54:07.994 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-10-16 20:54:08.002 Enabled verbose msgs:  important general
2009-10-16 20:54:08.015 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-16 20:54:10.982 Reschedule requested for id -1.
2009-10-16 20:54:11.006 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-10-16 20:54:11.009 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-10-16 20:54:11.011 Seem to be woken up by USER
2009-10-16 20:54:17.807 mythbackend: Running housekeeping thread
2009-10-16 20:55:27.982 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-16 20:59:47.294 MainServer::HandleAnnounce Monitor
2009-10-16 20:59:47.299 adding: sateesh-pvr as a client (events: 0)
2009-10-16 20:59:47.301 MainServer::HandleAnnounce Monitor
2009-10-16 20:59:47.302 adding: sateesh-pvr as a client (events: 1)
2009-10-16 20:59:47.306 Reschedule requested for id -1.
2009-10-16 20:59:47.313 MythSocket(b32032d0:-1): writeStringList: Error, socket went unconnected.
2009-10-16 20:59:47.332 Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2009-10-16 20:59:47.338 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2009-10-16 21:04:35.229 Using runtime prefix = /usr
2009-10-16 21:04:35.372 Empty LocalHostName.
2009-10-16 21:04:35.373 Using localhost value of sateesh-pvr
2009-10-16 21:04:35.387 New DB connection, total: 1
2009-10-16 21:04:35.393 Connected to database 'mythconverg' at host: localhost
2009-10-16 21:04:35.395 Closing DB connection named 'DBManager0'
2009-10-16 21:04:35.409 Connected to database 'mythconverg' at host: localhost
2009-10-16 21:04:35.411 New DB connection, total: 2
2009-10-16 21:04:35.422 Connected to database 'mythconverg' at host: localhost
2009-10-16 21:04:35.425 Current Schema Version: 1214
Starting up as the master server.
2009-10-16 21:04:35.434 mythbackend: MythBackend started as master server
2009-10-16 21:04:35.444 New DB connection, total: 3
2009-10-16 21:04:35.449 Connected to database 'mythconverg' at host: localhost
2009-10-16 21:04:35.551 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-10-16 21:04:35.553 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-10-16 21:04:35.662 New DB scheduler connection
2009-10-16 21:04:35.663 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2009-10-16 21:04:35.690 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-10-16 21:04:35.693 Main::Registering HttpStatus Extension
2009-10-16 21:04:35.700 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-10-16 21:04:35.709 Enabled verbose msgs:  important general
2009-10-16 21:04:35.717 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-16 21:04:38.686 Reschedule requested for id -1.
2009-10-16 21:04:38.709 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-10-16 21:04:38.711 scheduler: Scheduled items: Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-10-16 21:04:38.714 Seem to be woken up by USER
2009-10-16 21:04:45.439 mythbackend: Running housekeeping thread
2009-10-16 21:05:55.686 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-10-16 21:07:08.729 MainServer::HandleAnnounce Monitor
2009-10-16 21:07:08.733 adding: sateesh-pvr as a client (events: 0)
2009-10-16 21:07:08.735 MainServer::HandleAnnounce Monitor
2009-10-16 21:07:08.735 adding: sateesh-pvr as a client (events: 1)
2009-10-16 21:07:08.745 Reschedule requested for id -1.
2009-10-16 21:07:08.767 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-10-16 21:10:42.061 MainServer::HandleAnnounce Monitor
2009-10-16 21:10:42.066 adding: sateesh-pvr as a client (events: 0)
2009-10-16 21:10:42.067 MainServer::HandleAnnounce Monitor
2009-10-16 21:10:42.068 adding: sateesh-pvr as a client (events: 1)
2009-10-16 21:10:42.072 MainServer::HandleAnnounce Playback
2009-10-16 21:10:42.074 adding: sateesh-pvr as a client (events: 0)
2009-10-16 21:10:42.078 TVRec(1): Changing from None to WatchingLiveTV
2009-10-16 21:10:42.083 TVRec(1): HW Tuner: 1->1
2009-10-16 21:10:42.181 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-10-16 21:10:42.183 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-10-16 21:10:42.185 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-10-16 21:10:42.188 TVRec(1): Changing from WatchingLiveTV to None
2009-10-16 21:10:44.128 MainServer::HandleAnnounce Playback
2009-10-16 21:10:44.133 adding: sateesh-pvr as a client (events: 0)
2009-10-16 21:10:44.138 TVRec(1): Changing from None to WatchingLiveTV
2009-10-16 21:10:44.142 TVRec(1): HW Tuner: 1->1
2009-10-16 21:10:44.240 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-10-16 21:10:44.242 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-10-16 21:10:44.245 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-10-16 21:10:44.248 TVRec(1): Changing from WatchingLiveTV to None

```
And here is mythfontend log

```

==> /var/log/mythtv/mythfrontend.log <==
2009-10-16 20:42:08.613 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-16 20:42:08.664 Registering Internal as a media playback plugin.
2009-10-16 20:42:08.834 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-16 20:42:09.178 Failed to run 'cdrecord --scanbus'
2009-10-16 20:42:09.180 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-10-16 20:42:09.181 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-10-16 20:42:09.198 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-16 20:42:09.332 No theme dir: /home/sateesh/.mythtv/themes/Mythbuntu-8.04
2009-10-16 20:42:13.106 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-16 20:42:13.107 Using protocol version 40
2009-10-16 20:42:13.135 TV: Attempting to change from None to WatchingLiveTV
2009-10-16 20:42:13.135 Using protocol version 40
2009-10-16 20:42:13.373 GetEntryAt(-1) failed.
2009-10-16 20:42:13.403 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-10-16 20:42:13.403 TV Error: LiveTV not successfully started
2009-10-16 20:42:13.403 TV Error: LiveTV not successfully started
2009-10-16 20:42:13.475 TV: Deleting TV Chain in destructor
2009-10-16 20:42:13.532 DPMS Deactivated 
2009-10-16 20:42:13.533 DPMS Reactivated.
2009-10-16 20:42:58.291 Received a remote 'Clear Cache' request
2009-10-16 20:43:02.532 Loading from: /usr/share/mythtv/themes/default/appear-ui.xml
2009-10-16 20:43:06.176 Received a remote 'Clear Cache' request
2009-10-16 20:43:11.814 Deleting UPnP client...

```Could some one pls point out what went wrong..

Thanks
mars

---

### Post by tgm4883 on 2009-10-17
```
2009-10-16 20:54:07.915 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-10-16 20:54:07.946 ChannelBase(1) Warning: Setting start channel 'Please add' failed, 
            selected to 'Please add' on input 'Tuner 1' instead.

```

---

### Post by mars76 on 2009-10-17
Hi,

  I have reconfigured the mythfrontend and ran the mythfilldatbase again and now i am getting a different error message.. Live TV still doesn't work.

```

009-10-17 09:58:04.832 TVRec(1): Changing from None to WatchingLiveTV
2009-10-17 09:58:04.839 TVRec(1): HW Tuner: 1->1
2009-10-17 09:58:04.936 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-10-17 09:58:04.938 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-10-17 09:58:04.939 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-10-17 09:58:04.940 TVRec(1): Changing from WatchingLiveTV to None
2009-10-17 09:58:18.754 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```THis is the only error i see in the mythbackend logs  and my mythfrontend logs are listed below:

```

==> /var/log/mythtv/mythfrontend.log <==
2009-10-17 08:57:53.992 TV Error: LiveTV not successfully started
2009-10-17 08:57:53.993 TV Error: LiveTV not successfully started
2009-10-17 08:57:54.023 TV: Deleting TV Chain in destructor
2009-10-17 08:57:54.080 DPMS Deactivated 
2009-10-17 08:57:54.080 DPMS Reactivated.
No LSB modules are available.
WARNING: you should run this program as super-user.
2009-10-17 09:43:05.240 Event socket closed. No connection to the backend.
2009-10-17 09:52:38.313 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-17 09:52:38.313 Using protocol version 40
2009-10-17 09:52:38.326 TV: Attempting to change from None to WatchingLiveTV
2009-10-17 09:52:38.327 Using protocol version 40
2009-10-17 09:52:38.448 GetEntryAt(-1) failed.
2009-10-17 09:52:38.448 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-10-17 09:52:38.448 TV Error: LiveTV not successfully started
2009-10-17 09:52:38.449 TV Error: LiveTV not successfully started
2009-10-17 09:52:38.529 TV: Deleting TV Chain in destructor
2009-10-17 09:52:38.585 DPMS Deactivated 
2009-10-17 09:52:38.585 DPMS Reactivated.
2009-10-17 09:52:48.888 Deleting UPnP client...

```Thanks
mars

---

### Post by mars76 on 2009-10-17
It seems i have made some progress how ever i still can't get the Live TV Working..When i click on LiveTV it shows a blank screen for few seconds and returns to the main screen.

I have checked the permissions on the directory (default) for recording the shows and i have changed them to 777 and now here is my log looks like.

The ivtv driver seems to be not working . I am using the 1.4.0 version of the driver..

```

2009-10-17 10:56:23.536 TVRec(1): Changing from None to WatchingLiveTV
2009-10-17 10:56:23.542 TVRec(1): HW Tuner: 1->1
2009-10-17 10:56:24.777 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-10-17 10:56:24.784 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
            is not supported by ivtv driver, using 48000 Hz instead.
2009-10-17 10:56:29.855 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-10-17 10:56:31.323 TVRec(1): Changing from WatchingLiveTV to None
2009-10-17 10:56:34.960 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-10-17 10:56:35.069 Finished recording Teenage Mutant Ninja Turtles: channel 2003
2009-10-17 10:56:35.075 scheduler: Finished recording: Teenage Mutant Ninja Turtles: channel 2003

```Driver Info

```

dmesg |grep ivtv
[   10.622123] ivtv:  Start initialization, version 1.4.0
[   10.622197] ivtv0: Initializing card #0
[   10.622199] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   10.622798] ivtv 0000:05:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.670302] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   10.784097] cx25840 0-0044: cx25  0-21 found @ 0x88 (ivtv i2c driver #0)
[   10.788011] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   10.788049] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   10.919941] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   10.919981] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   10.920035] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   10.920075] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   10.920077] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   10.920112] ivtv:  End initialization
[   26.916012] ivtv 0000:05:03.0: firmware: requesting v4l-cx2341x-enc.fw
[   26.985330] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   27.184154] ivtv0: Encoder revision: 0x02060039

```

---

### Post by mars76 on 2009-10-17
Hi All,
 
  I have updated my ivtv driver to bleeding edge driver and still getting the same error:

```

2009-10-17 10:56:24.777 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-10-17 10:56:24.784 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
            is not supported by ivtv driver, using 48000 Hz instead.
2009-10-17 10:56:29.855 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-10-17 10:56:31.323 TVRec(1): Changing from WatchingLiveTV to None
2009-10-17 10:56:34.960 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding

```Driver Info

```

dmesg |grep ivtv
[   10.691990] ivtv: Start initialization, version 1.4.1
[   10.692071] ivtv0: Initializing card 0
[   10.692073] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   10.692117] ivtv 0000:05:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.739651] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   10.845519] cx25840 0-0044: cx23887 A/V decoder found @ 0x88 (ivtv i2c driver #0)
[   10.961818] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   11.015154] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   11.329495] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   11.329528] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   11.329550] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   11.329571] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   11.329573] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   11.329588] ivtv: End initialization
[   28.692011] ivtv 0000:05:03.0: firmware: requesting v4l-cx2341x-enc.fw
[   28.763503] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   28.960142] ivtv0: Encoder revision: 0x02060039

```Thanks
mars

---

### Post by mars76 on 2009-10-17
Hi ,

  I restarted my machine and i am not getting the driver error ..I am getting the following Error:

```

2009-10-17 15:24:30.193 TVRec(1): Changing from None to WatchingLiveTV
2009-10-17 15:24:30.199 TVRec(1): HW Tuner: 1->1
2009-10-17 15:24:30.295 Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
2009-10-17 15:24:30.296 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2009-10-17 15:24:30.297 TVRec(1) Error: Failed to set channel to 1. Reverting to kState_None
2009-10-17 15:24:30.298 TVRec(1): Changing from WatchingLiveTV to None

```I have modified in the settings of Channel Editor to use channel 181 and it seems the software is unable to change the channell..

```

2009-10-17 15:39:03.935 New DB connection, total: 3
2009-10-17 15:39:03.937 Connected to database 'mythconverg' at host: localhost
2009-10-17 15:39:04.033 Channel(/dev/video0) Error: GetCurrentChannelNum(181): Failed to find Channel
2009-10-17 15:39:04.038 Channel(/dev/video0)::TuneTo(181): Error, failed to find channel.

```I coudn't make the "Scan for Channels" working as it always shows 0% signal Strength. I opted for Looking Channels from Source and it populated all the channel info which i can browse in the Channel Editor.

I am using MSE Version of PVR-150 which comes with a Remote and USB Based IR Blaster. As i didn't see any other errors in the frontend or backend log i assume these are working properly..

Thanks
mars

---

### Post by GuiGuy on 2009-10-17
> **mars76 said:**
> HI All,

  I have installed mythbuntu 9.0.4 on a new Hard Drive and i have PVR-150 Tuner Card. After completing the installation the Live TV deos't work.

I sense your frustration, so at the risk of adding to it can we presume all is well in the backend?

---

### Post by mars76 on 2009-10-17
Hi,

  Thanks for your reply..

  Yes i don't think there is any thing wrong with the mythbackend..

  As i have installed the mythweb i can see the status of mythtv overall and i didn't find any thing wrong.

  I am able to schedule a program using mythweb, how ever if the channel changer won't work i guess it will not record.

  Also i am using the IR Blaster SMK USB Dongle. I am not sure whether it is the problem with the IR Blaster when i use the Remote the Blaster receiver shows a red flash..

  Also how does the Capture cards that won't come with IR Blaster work ?? If i schedule a recording then how does mythtv changes the channel in the STB. I assume IR Blaster is mandatory unless the STB itself is connected to the mythtv either using a USB or Component cable..

 The IR Blaster is similar to the one posted here ( there is another part where this gets plugged into and it is connected to mythtv box using USB Port)

[http://www.irblaster.info/tivo_irblaster_small.jpg](http://www.irblaster.info/tivo_irblaster_small.jpg)

I will keep posting my findings...

Thanks
mars

---

