---
title: "Mythbuntu Blank Screen Live TV"
date: 2007-11-25
forum: Mythbuntu
---

### Post by nongeek on 2007-11-25
I have been searching forums and documentation till my eyes have blurred but cannot find a solution to this problem.

I am setting up a Mythbuntu box as I am sure many have (using newest stable version). installs fine, database appears to work fine, channel grabber from schedule direct updates fine, everything seems to work until I try to watch live TV. Hit the button and the screen goes blank, on occasion it will kick back to the menu but more often then not I must case switch reboot. 

I am using a Hauppauge PVR-150 card. In the setup, I ensure that I select the correct card,  MPEG -2 encoder card (PVR-x50, PVR-500) as found in other posts. I have tried setting it up as both  Tuner 1 for coaxial input, and also as composite (not at same time). Every time I scan it appears to read and pick up channels normally, all looks good so far. I Have tried various frequency tables starting with us-bcast through all the different cable tables, still no TV. 

Here is the kicker. I can open and watch the stream using VLC, and change channels using the cable box remote. so I know the card woks fine. After a Mythtv crash,  I can open the Mythtv "recording" folder and find a file about 1-2 seconds long that coincides with live tv before it crashes with a good quality recording that can be played by mplayer. This tells me that something is trying to work. 

Checked all the permissions on /var/lib/mythtv/recordings folders, and also on mythconverg database to be thorough.

I have found other posts in various forums describing the same problem but there were no reply posts with a solution. Did not find any How to guides (including the one at Ubuntu Help) or documentation that has a solution, or even deals with this particular issue.

Any pointer in the right direction would be appreciated.

---

### Post by newlinux on 2007-11-25
You should look in your front and backend logs to see what errors are ocurring. They should be located in:

/var/log/mythtv/

If you post the relevant sections perhaps we can find out more what is going on.

---

### Post by nongeek on 2007-11-25
I was looking at the logs and the only thing that jumps out is;

Backend log

QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error.

On the frontend log

SIP: Cannot register; proxy, username or password not set

and

2007-11-25 19:07:36.864 VideoOutputXv: XvMCTex: Init failed
2007-11-25 19:07:36.866 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'

Not totally sure what I am looking at so here are both logs from the last attempt;

Frontend

Starting mythfrontend.real..
2007-11-25 19:07:18.069 Current Schema Version: 1160
2007-11-25 19:07:18.071 mythfrontend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2007-11-25 19:07:18.071 Enabled verbose msgs:  important general
2007-11-25 19:07:20.765 Total desktop dim: 1280x768, with 1 screen[s].
2007-11-25 19:07:20.768 Using screen 0, 1280x768 at 0,0
2007-11-25 19:07:20.769 Switching to square mode (Mythbuntu)
2007-11-25 19:07:21.404 Using the Qt painter
2007-11-25 19:07:21.947 Joystick disabled.
2007-11-25 19:07:21.951 New DB connection, total: 2
2007-11-25 19:07:21.955 Connected to database 'mythconverg' at host: localhost
2007-11-25 19:07:26.697 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2007-11-25 19:07:26.889 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-25 19:07:27.097 Registering Internal as a media playback plugin.
2007-11-25 19:07:27.339 Registering MythDVD DVD Media Handler as a media handler ext()
2007-11-25 19:07:27.342 Registering MythDVD VCD Media Handler as a media handler ext()
2007-11-25 19:07:27.530 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-11-25 19:07:27.530 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-11-25 19:07:29.044 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-11-25 19:07:29.045 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.142:5060 NAT address 192.168.0.142
SIP: Cannot register; proxy, username or password not set
2007-11-25 19:07:34.133 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-11-25 19:07:34.145 Using protocol version 31
2007-11-25 19:07:34.162 TV: Attempting to change from None to WatchingLiveTV
2007-11-25 19:07:34.163 Using protocol version 31
2007-11-25 19:07:36.195 DPMS Deactivated 
2007-11-25 19:07:36.496 AFD: Opened codec 0x85ed990, id(MPEG2VIDEO) type(Video)
2007-11-25 19:07:36.552 AFD: Opened codec 0x85edcd0, id(MP2) type(Audio)
2007-11-25 19:07:36.683 Opening ALSA audio device 'default'.
2007-11-25 19:07:36.864 VideoOutputXv: XvMCTex: Init failed
2007-11-25 19:07:36.866 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'

And the Backend log

Starting up as the master server.
2007-11-25 19:07:00.924 New DB connection, total: 2
2007-11-25 19:07:00.941 Connected to database 'mythconverg' at host: localhost
2007-11-25 19:07:00.949 EITHelper: localtime offset -6:00:00 
2007-11-25 19:07:01.173 New DB connection, total: 3
2007-11-25 19:07:01.201 Connected to database 'mythconverg' at host: localhost
2007-11-25 19:07:01.745 New DB scheduler connection
2007-11-25 19:07:01.751 Connected to database 'mythconverg' at host: localhost
2007-11-25 19:07:01.871 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-11-25 19:07:02.150 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-11-25 19:07:03.552 Main::Registering HttpStatus Extension
2007-11-25 19:07:03.587 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-11-25 19:07:03.879 Reschedule requested for id -1.
2007-11-25 19:07:03.888 mythbackend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2007-11-25 19:07:04.275 Enabled verbose msgs:  important general
2007-11-25 19:07:04.419 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-11-25 19:07:04.609 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2007-11-25 19:07:04.786 Scheduled 0 items in 0.7 = 0.63 match + 0.03 place
2007-11-25 19:07:04.866 Seem to be woken up by USER
2007-11-25 19:07:34.147 MainServer::HandleAnnounce Monitor
2007-11-25 19:07:34.152 adding: myth as a client (events: 0)
2007-11-25 19:07:34.154 MainServer::HandleAnnounce Monitor
2007-11-25 19:07:34.155 adding: myth as a client (events: 1)
2007-11-25 19:07:34.164 MainServer::HandleAnnounce Playback
2007-11-25 19:07:34.179 adding: myth as a client (events: 0)
2007-11-25 19:07:34.189 TVRec(1): Changing from None to WatchingLiveTV
2007-11-25 19:07:34.193 TVRec(1): HW Tuner: 1->1
2007-11-25 19:08:45.660 Using runtime prefix = /usr
2007-11-25 19:08:45.882 New DB connection, total: 1
2007-11-25 19:08:45.891 Connected to database 'mythconverg' at host: localhost
2007-11-25 19:08:45.933 Current Schema Version: 1160

I am using an ATI Radeon card using open source drivers. If I try and use the "restricted" drivers that come with Mythbuntu, all I get is a blank screen on bootup.

VLC picks up and displays the stream fine, its just myth where I seem to have the problem.

Once again thanks in advance for any help or direction you can provide.

---

### Post by nongeek on 2007-11-25
Well, on a flyer I changed out my ATI Radeon video card and put in an old Nvidia 
GEForce 4 MX420. Reloaded and presto it all worked. Left everything except configuration at default, no sweat.

Had an issue of VLC stealing the sound even after it was closed, but a reboot fixed that.

Would still like to figure out the Radeon issue at some point, but for now I am happy to be able to play around with MythTV and see what it can do before building a custom system.

:)

---

### Post by fblauer on 2008-01-23
My machine reboots when I try to run watch live tv. 
I have an ATI video card
Here is my log:

2008-01-23 00:49:22.479 Using runtime prefix = /usr
2008-01-23 00:49:22.516 New DB connection, total: 1
2008-01-23 00:49:22.548 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:49:22.590 Current Schema Version: 1160
Starting up as the master server.
2008-01-23 00:49:22.661 New DB connection, total: 2
2008-01-23 00:49:22.663 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:49:22.667 EITHelper: localtime offset -5:00:00 
2008-01-23 00:49:22.677 New DB connection, total: 3
2008-01-23 00:49:22.679 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:49:22.846 New DB scheduler connection
2008-01-23 00:49:22.847 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:49:24.193 Main::Registering HttpStatus Extension
2008-01-23 00:49:24.196 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-01-23 00:49:24.196 Enabled verbose msgs:  important general
2008-01-23 00:49:24.198 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-01-23 00:49:24.205 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-01-23 00:49:24.864 Reschedule requested for id -1.
2008-01-23 00:49:25.018 Scheduled 0 items in 0.2 = 0.13 match + 0.03 place
2008-01-23 00:49:25.035 Seem to be woken up by USER
2008-01-23 00:49:29.327 MainServer::HandleAnnounce Monitor
2008-01-23 00:49:29.339 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 00:49:29.340 MainServer::HandleAnnounce Monitor
2008-01-23 00:49:29.341 adding: HP_MEDIAPC as a client (events: 1)
2008-01-23 00:49:29.346 MainServer::HandleAnnounce Playback
2008-01-23 00:49:29.347 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 00:49:29.349 TVRec(1): Changing from None to WatchingLiveTV
2008-01-23 00:49:29.353 TVRec(1): HW Tuner: 1->1
2008-01-23 00:49:29.569 Unknown video codec
2008-01-23 00:49:29.573 Please go into the TV Settings, Recording Profiles and
2008-01-23 00:49:29.573 setup the four 'Software Encoders' profiles.
2008-01-23 00:49:29.574 Assuming RTjpeg for now.
2008-01-23 00:49:29.575 NVR: Error, unknown audio codec
2008-01-23 00:49:29.591 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-01-23 00:50:09.599 TVRec(1): Changing from WatchingLiveTV to None
2008-01-23 00:50:09.626 Finished recording Unknown: channel 1134
2008-01-23 00:51:37.953 Using runtime prefix = /usr
2008-01-23 00:51:38.000 New DB connection, total: 1
2008-01-23 00:51:38.012 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:51:38.053 Current Schema Version: 1160
Starting up as the master server.
2008-01-23 00:51:38.064 New DB connection, total: 2
2008-01-23 00:51:38.067 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:51:38.087 EITHelper: localtime offset -5:00:00 
2008-01-23 00:51:38.094 New DB connection, total: 3
2008-01-23 00:51:38.123 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:51:38.285 New DB scheduler connection
2008-01-23 00:51:38.286 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:51:39.621 Main::Registering HttpStatus Extension
2008-01-23 00:51:39.623 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-01-23 00:51:39.642 Enabled verbose msgs:  important general
2008-01-23 00:51:39.643 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-01-23 00:51:39.646 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-01-23 00:51:40.295 Reschedule requested for id -1.
2008-01-23 00:51:40.442 Scheduled 0 items in 0.1 = 0.12 match + 0.02 place
2008-01-23 00:51:40.450 Seem to be woken up by USER
2008-01-23 00:51:47.040 MainServer::HandleAnnounce Monitor
2008-01-23 00:51:47.046 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 00:51:47.063 MainServer::HandleAnnounce Monitor
2008-01-23 00:51:47.064 adding: HP_MEDIAPC as a client (events: 1)
2008-01-23 00:51:47.072 MainServer::HandleAnnounce Playback
2008-01-23 00:51:47.101 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 00:51:47.104 TVRec(1): Changing from None to WatchingLiveTV
2008-01-23 00:51:47.110 TVRec(1): HW Tuner: 1->1
2008-01-23 00:51:47.404 Unknown video codec
2008-01-23 00:51:47.408 Please go into the TV Settings, Recording Profiles and
2008-01-23 00:51:47.409 setup the four 'Software Encoders' profiles.
2008-01-23 00:51:47.410 Assuming RTjpeg for now.
2008-01-23 00:51:47.411 NVR: Error, unknown audio codec
2008-01-23 00:51:47.453 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-01-23 00:52:27.479 TVRec(1): Changing from WatchingLiveTV to None
2008-01-23 00:52:27.502 Finished recording Unknown: channel 1134
2008-01-23 00:54:15.513 Using runtime prefix = /usr
2008-01-23 00:54:15.550 New DB connection, total: 1
2008-01-23 00:54:15.595 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:54:15.632 Current Schema Version: 1160
Starting up as the master server.
2008-01-23 00:54:15.648 New DB connection, total: 2
2008-01-23 00:54:15.650 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:54:15.654 EITHelper: localtime offset -5:00:00 
2008-01-23 00:54:15.663 TVRec(1) Error: Start channel invalid, setting to '10' on input Tuner 1 instead.
2008-01-23 00:54:15.665 DVBChan(0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-01-23 00:54:15.672 New DB connection, total: 3
2008-01-23 00:54:15.679 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:54:16.914 Main::Registering HttpStatus Extension
2008-01-23 00:54:16.918 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-01-23 00:54:16.960 Enabled verbose msgs:  important general
2008-01-23 00:54:16.963 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2008-01-23 00:54:16.966 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2008-01-23 00:54:23.931 MainServer::HandleAnnounce Monitor
2008-01-23 00:54:23.986 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 00:54:23.987 MainServer::HandleAnnounce Monitor
2008-01-23 00:54:23.988 adding: HP_MEDIAPC as a client (events: 1)
2008-01-23 00:54:35.680 Expiring Unknown from Wed Jan 23 00:46:04 2008, 0 MBytes, forced expire (LiveTV recording)
2008-01-23 00:54:35.688 Expiring Unknown from Wed Jan 23 00:49:29 2008, 0 MBytes, forced expire (LiveTV recording)
2008-01-23 00:54:35.710 Expiring Unknown from Wed Jan 23 00:51:47 2008, 0 MBytes, forced expire (LiveTV recording)
2008-01-23 00:55:19.089 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2008-01-23 00:55:39.855 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2008-01-23 00:55:43.058 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2008-01-23 00:57:26.055 Using runtime prefix = /usr
2008-01-23 00:57:26.091 New DB connection, total: 1
2008-01-23 00:57:26.133 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:57:26.138 Current Schema Version: 1160
Starting up as the master server.
2008-01-23 00:57:26.174 New DB connection, total: 2
2008-01-23 00:57:26.189 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:57:26.193 EITHelper: localtime offset -5:00:00 
2008-01-23 00:57:26.199 TVRec(1) Error: Start channel invalid, setting to '10' on input Tuner 1 instead.
2008-01-23 00:57:26.202 New DB connection, total: 3
2008-01-23 00:57:26.204 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:57:26.224 ChannelBase: Could not find input: DVBInput on card when setting channel 10

2008-01-23 00:57:26.239 ChannelBase: Could not find input: DVBInput on card when setting channel 2

2008-01-23 00:57:26.240 TVRec(1) Error: Setting start channel '10' failed, 
			and backup '2' failed as well.
2008-01-23 00:57:26.254 New DB scheduler connection
2008-01-23 00:57:26.281 Connected to database 'mythconverg' at host: localhost
2008-01-23 00:57:27.622 Main::Registering HttpStatus Extension
2008-01-23 00:57:27.625 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-01-23 00:57:27.626 Enabled verbose msgs:  important general
2008-01-23 00:57:27.627 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2008-01-23 00:57:27.629 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2008-01-23 00:57:28.288 Reschedule requested for id -1.
2008-01-23 00:57:28.433 Scheduled 0 items in 0.1 = 0.12 match + 0.02 place
2008-01-23 00:57:28.440 Seem to be woken up by USER
2008-01-23 00:57:43.775 MainServer::HandleAnnounce Monitor
2008-01-23 00:57:43.777 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 00:57:43.795 MainServer::HandleAnnounce Monitor
2008-01-23 00:57:43.796 adding: HP_MEDIAPC as a client (events: 1)
2008-01-23 01:02:25.426 MainServer::HandleAnnounce Playback
2008-01-23 01:02:25.429 adding: HP_MEDIAPC as a client (events: 0)
2008-01-23 01:02:25.432 TVRec(1): Changing from None to WatchingLiveTV
2008-01-23 01:02:25.454 TVRec(1) Error: Start channel invalid, setting to '10' on input Tuner 1 instead.
2008-01-23 01:02:25.455 TVRec(1): HW Tuner: 1->0
2008-01-23 01:02:25.474 ChannelBase: Could not find input: DVBInput on card when setting channel 10

2008-01-23 01:02:25.475 TVRec(1) Error: Failed to set channel to 10.
2008-01-23 01:02:25.518 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Wed Jan 23 01:02:25 2008) endts(Wed Jan 23 01:02:25 2008)
             recstartts(Wed Jan 23 01:02:25 2008) recendts(Wed Jan 23 01:02:25 2008)
             title()
2008-01-23 01:02:27.208 TVRec(1): Changing from WatchingLiveTV to None
2008-01-23 01:02:27.550 Finished recording : channel 4294967295

---

### Post by newlinux on 2008-01-23
you need to give us a little more information about your setup. What kind of tuner card are you using? How did you setup your tuner card, video source, DVB/V4L/etc. Does scanning for channels work?

---

