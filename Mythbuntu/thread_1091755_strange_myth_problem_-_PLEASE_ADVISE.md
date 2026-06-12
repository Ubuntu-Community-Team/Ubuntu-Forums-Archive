---
title: "strange myth problem - PLEASE ADVISE"
date: 2009-03-09
forum: Mythbuntu
---

### Post by Lexje on 2009-03-09
Hi forum,

I'm having this strange issue:
My install:
Hauppauge PVR-150 TV card
Ubuntu 8.10
Mythbuntu added from Mythbuntu website
Located in Belgium, xmltv-grab-be does not work anymore, so far no problem.

Install finished without a single problem.
Addition of mythbuntu finished without any problem.
I added mc2xml to fill program listing.
Enabled mythweb, and could verify that program listing was filled.
Also verified that channels correspond with my provider's settings (in BE this may vary according to cable provider)

Now, when I program a recording via mythweb, the recording gets regstered with mythbuntu allright, and a nuv file is created in /var/lib/mythtv/recordings/, however nothing gets recorded, and the file sits at a size of 66848 bytes.
```
erwin@mythbuntu:/var/lib/mythtv/recordings$ ls -la
total 84
drwxrwsr-x 2 mythtv mythtv  4096 2009-03-09 22:45 .
drwxr-xr-x 3 root   root    4096 2009-03-09 22:03 ..
-rw-r--r-- 1 mythtv mythtv 66848 2009-03-09 22:34 204250_20090309223500.nuv
-rw-rw-rw- 1 mythtv mythtv    69 2009-03-09 22:45 204250_20090309223500.nuv.png
```

Here's my logfile content:
mythbackend
```
2009-03-09 22:34:35.238 Reschedule requested for id 1.
2009-03-09 22:34:35.288 Scheduled 1 items in 0.0 = 0.01 match + 0.04 place
2009-03-09 22:34:35.306 TVRec(1): ASK_RECORDING 1 0 0 0
2009-03-09 22:34:35.370 TVRec(1): Changing from None to RecordingOnly
2009-03-09 22:34:35.385 TVRec(1): HW Tuner: 1->1
2009-03-09 22:34:35.490 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and se
tup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-03-09 22:34:35.491 NVR(/dev/video0) Error: Unknown audio codec
2009-03-09 22:34:35.521 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-03-09 22:34:35.526 Started recording: De Laatste Show: channel 204250 on cardid 1, sourceid 1
2009-03-09 22:34:35.855 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-03-09 22:34:41.674 MainServer::HandleAnnounce Monitor
2009-03-09 22:34:41.677 adding: mythbuntu as a client (events: 0)
2009-03-09 22:45:00.086 TVRec(1): Changing from RecordingOnly to None
2009-03-09 22:45:00.101 Reschedule requested for id 0.
2009-03-09 22:45:00.101 Finished recording De Laatste Show: channel 204250
2009-03-09 22:45:00.135 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-03-09 22:45:00.143 Finished recording De Laatste Show: channel 204250
2009-03-09 22:45:00.330 Using runtime prefix = /usr
2009-03-09 22:45:00.333 Empty LocalHostName.
2009-03-09 22:45:00.334 Using localhost value of mythbuntu
2009-03-09 22:45:00.346 New DB connection, total: 1

```

mythfrontend
```
Starting mythfrontend.real..
2009-03-09 22:31:06.704 New DB connection, total: 2
2009-03-09 22:31:06.705 Connected to database 'mythconverg' at host: localhost
2009-03-09 22:31:06.709 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-09 22:31:06.709 Enabled verbose msgs:  important general
2009-03-09 22:31:07.400 No theme dir: /home/erwin/.mythtv/themes/G.A.N.T
2009-03-09 22:31:07.403 Primary screen 0.
2009-03-09 22:31:07.403 Using screen 0, 1280x1024 at 0,0
2009-03-09 22:31:07.404 No theme dir: /home/erwin/.mythtv/themes/G.A.N.T
2009-03-09 22:31:07.405 Switching to square mode (G.A.N.T)
2009-03-09 22:31:07.432 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-09 22:31:07.433 lirc_init failed for mythtv, see preceding messages
2009-03-09 22:31:07.433 JoystickMenuClient Error: Joystick disabled - Failed to read /home/erwin/.mythtv/joystickmenurc
2009-03-09 22:31:08.618 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-03-09 22:31:08.809 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-09 22:31:08.898 Registering Internal as a media playback plugin.
2009-03-09 22:31:08.964 No theme dir: /home/erwin/.mythtv/themes/G.A.N.T
2009-03-09 22:31:12.705 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-09 22:31:12.706 Using protocol version 40
2009-03-09 22:31:12.724 TV: Attempting to change from None to WatchingLiveTV
2009-03-09 22:31:12.726 Using protocol version 40
2009-03-09 22:31:14.132 DPMS Deactivated 
2009-03-09 22:31:54.063 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-03-09 22:31:54.063 TV Error: LiveTV not successfully started
2009-03-09 22:31:54.095 TV: Deleting TV Chain in destructor
2009-03-09 22:31:54.097 DPMS Reactivated.

```

I'll be glad to read your suggestions!!
Thanks,

Erwin

---

### Post by tgm4883 on 2009-03-09
> **Lexje said:**
> Hi forum,

I'm having this strange issue:
My install:
Hauppauge PVR-150 TV card
Ubuntu 8.10
Mythbuntu added from Mythbuntu website
Located in Belgium, xmltv-grab-be does not work anymore, so far no problem.

Install finished without a single problem.
Addition of mythbuntu finished without any problem.
I added mc2xml to fill program listing.
Enabled mythweb, and could verify that program listing was filled.
Also verified that channels correspond with my provider's settings (in BE this may vary according to cable provider)

Now, when I program a recording via mythweb, the recording gets regstered with mythbuntu allright, and a nuv file is created in /var/lib/mythtv/recordings/, however nothing gets recorded, and the file sits at a size of 66848 bytes.
```
erwin@mythbuntu:/var/lib/mythtv/recordings$ ls -la
total 84
drwxrwsr-x 2 mythtv mythtv  4096 2009-03-09 22:45 .
drwxr-xr-x 3 root   root    4096 2009-03-09 22:03 ..
-rw-r--r-- 1 mythtv mythtv 66848 2009-03-09 22:34 204250_20090309223500.nuv
-rw-rw-rw- 1 mythtv mythtv    69 2009-03-09 22:45 204250_20090309223500.nuv.png
```

Here's my logfile content:
mythbackend
```
2009-03-09 22:34:35.238 Reschedule requested for id 1.
2009-03-09 22:34:35.288 Scheduled 1 items in 0.0 = 0.01 match + 0.04 place
2009-03-09 22:34:35.306 TVRec(1): ASK_RECORDING 1 0 0 0
2009-03-09 22:34:35.370 TVRec(1): Changing from None to RecordingOnly
2009-03-09 22:34:35.385 TVRec(1): HW Tuner: 1->1
2009-03-09 22:34:35.490 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and se
tup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-03-09 22:34:35.491 NVR(/dev/video0) Error: Unknown audio codec
2009-03-09 22:34:35.521 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-03-09 22:34:35.526 Started recording: De Laatste Show: channel 204250 on cardid 1, sourceid 1
2009-03-09 22:34:35.855 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-03-09 22:34:41.674 MainServer::HandleAnnounce Monitor
2009-03-09 22:34:41.677 adding: mythbuntu as a client (events: 0)
2009-03-09 22:45:00.086 TVRec(1): Changing from RecordingOnly to None
2009-03-09 22:45:00.101 Reschedule requested for id 0.
2009-03-09 22:45:00.101 Finished recording De Laatste Show: channel 204250
2009-03-09 22:45:00.135 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-03-09 22:45:00.143 Finished recording De Laatste Show: channel 204250
2009-03-09 22:45:00.330 Using runtime prefix = /usr
2009-03-09 22:45:00.333 Empty LocalHostName.
2009-03-09 22:45:00.334 Using localhost value of mythbuntu
2009-03-09 22:45:00.346 New DB connection, total: 1

```

mythfrontend
```
Starting mythfrontend.real..
2009-03-09 22:31:06.704 New DB connection, total: 2
2009-03-09 22:31:06.705 Connected to database 'mythconverg' at host: localhost
2009-03-09 22:31:06.709 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-09 22:31:06.709 Enabled verbose msgs:  important general
2009-03-09 22:31:07.400 No theme dir: /home/erwin/.mythtv/themes/G.A.N.T
2009-03-09 22:31:07.403 Primary screen 0.
2009-03-09 22:31:07.403 Using screen 0, 1280x1024 at 0,0
2009-03-09 22:31:07.404 No theme dir: /home/erwin/.mythtv/themes/G.A.N.T
2009-03-09 22:31:07.405 Switching to square mode (G.A.N.T)
2009-03-09 22:31:07.432 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-09 22:31:07.433 lirc_init failed for mythtv, see preceding messages
2009-03-09 22:31:07.433 JoystickMenuClient Error: Joystick disabled - Failed to read /home/erwin/.mythtv/joystickmenurc
2009-03-09 22:31:08.618 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-03-09 22:31:08.809 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-09 22:31:08.898 Registering Internal as a media playback plugin.
2009-03-09 22:31:08.964 No theme dir: /home/erwin/.mythtv/themes/G.A.N.T
2009-03-09 22:31:12.705 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-09 22:31:12.706 Using protocol version 40
2009-03-09 22:31:12.724 TV: Attempting to change from None to WatchingLiveTV
2009-03-09 22:31:12.726 Using protocol version 40
2009-03-09 22:31:14.132 DPMS Deactivated 
2009-03-09 22:31:54.063 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-03-09 22:31:54.063 TV Error: LiveTV not successfully started
2009-03-09 22:31:54.095 TV: Deleting TV Chain in destructor
2009-03-09 22:31:54.097 DPMS Reactivated.

```

I'll be glad to read your suggestions!!
Thanks,

Erwin

Looks like you set your pvr-150 card up as a software encoder instead of a hardware encoder.  Fix this in mythtv-setup and you should be golden.

---

### Post by Lexje on 2009-03-09
tgm, 

Thanks for your advice,
Just to know for the future: How exactly do you distinguish this card is setup as a software encoder£?

Thanks a lot!!

Erwin

---

### Post by tgm4883 on 2009-03-09
> **Lexje said:**
> tgm, 

Thanks for your advice,
Just to know for the future: How exactly do you distinguish this card is setup as a software encoder£?

Thanks a lot!!

Erwin

```
2009-03-09 22:34:35.490 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and se
tup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-03-09 22:34:35.491 NVR(/dev/video0) Error: Unknown audio codec

```

That pointed to being the card setup incorrectly.  Also, with a pvr-150, you should have .mpg's, not .nuv's

---

### Post by Lexje on 2009-03-10
Thanks a lot for really helping out!!

Erwin

---

