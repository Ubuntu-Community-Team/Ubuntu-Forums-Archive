---
title: "Myth Frontend lost connection to backend"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by spylvas on 2007-12-14
Hi,

I had a working frontend/backend myth set up in my ubuntu 7.10 until one day it just stopped to work and all I get is "
Could not connect to the master backend server - - is it running......" 

I didn't change anything or install any new apps. There was some updates I downloaded.

I have tried restart my backend, but it doesn't make any different what so ever.

Here are logs:

Backend

2007-12-14 19:30:03.036 TVRec(1): Changing from None to RecordingOnly
2007-12-14 19:30:03.050 TVRec(1): HW Tuner: 1->1
2007-12-14 19:30:03.316 Started recording: Scrubs "My T.C.W.": channel 1010 on cardid 1, sourceid 1
2007-12-14 19:30:03.323 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-12-14 19:40:40.437 Using runtime prefix = /usr
2007-12-14 19:40:40.490 New DB connection, total: 1
2007-12-14 19:40:40.499 Connected to database 'mythconverg' at host: localhost
2007-12-14 19:40:40.503 Current Schema Version: 1160
Starting up as the master server.
2007-12-14 19:40:40.550 New DB connection, total: 2
2007-12-14 19:40:40.553 Connected to database 'mythconverg' at host: localhost
2007-12-14 19:40:40.556 EITHelper: localtime offset -8:00:00 
2007-12-14 19:40:40.562 New DB connection, total: 3
2007-12-14 19:40:40.563 Connected to database 'mythconverg' at host: localhost
2007-12-14 19:40:40.721 New DB scheduler connection
2007-12-14 19:40:40.722 Connected to database 'mythconverg' at host: localhost
2007-12-14 19:40:42.136 Main::Registering HttpStatus Extension
2007-12-14 19:40:42.150 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-14 19:40:42.151 Enabled verbose msgs:  important general
2007-12-14 19:40:42.184 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-12-14 19:40:42.186 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2007-12-14 19:40:42.780 Reschedule requested for id -1.
2007-12-14 19:40:44.003 Scheduled 130 items in 1.2 = 0.83 match + 0.39 place
2007-12-14 19:40:44.009 Recording starts soon, AUTO-Startup assumed
2007-12-14 19:40:44.125 TVRec(1): Changing from None to RecordingOnly
2007-12-14 19:40:44.134 TVRec(1): HW Tuner: 1->1
2007-12-14 19:40:44.326 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-12-14 19:40:44.328 Started recording: Scrubs "My T.C.W.": channel 1010 on cardid 1, sourceid 1


Frontend

Starting mythfrontend.real..
2007-12-14 19:38:01.633 Current Schema Version: 1160
2007-12-14 19:38:01.670 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-14 19:38:01.671 Enabled verbose msgs:  important general
2007-12-14 19:38:02.781 Total desktop dim: 1280x1024, with 1 screen[s].
2007-12-14 19:38:02.783 Using screen 0, 1280x1024 at 0,0
2007-12-14 19:38:02.784 Switching to square mode (blue)
2007-12-14 19:38:02.844 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-12-14 19:38:03.803 Joystick disabled.
2007-12-14 19:38:04.231 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-12-14 19:38:04.368 Registering Internal as a media playback plugin.
2007-12-14 19:38:05.121 Using NV NPOT texture extension
2007-12-14 19:38:08.710 New DB connection, total: 2
2007-12-14 19:38:08.710 Connected to database 'mythconverg' at host: localhost
2007-12-14 19:38:08.762 Connecting to backend server: 192.168.11.4:6543 (try 1 of 5)
2007-12-14 19:38:11.768 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2007-12-14 19:38:15.259 TV: Attempting to change from None to None
2007-12-14 19:38:16.676 Connecting to backend server: 192.168.11.4:6543 (try 1 of 5)
2007-12-14 19:38:19.680 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
Starting mythfrontend.real..
2007-12-14 19:40:50.446 Current Schema Version: 1160
2007-12-14 19:40:50.447 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-14 19:40:50.447 Enabled verbose msgs:  important general
2007-12-14 19:40:50.864 Total desktop dim: 1280x1024, with 1 screen[s].
2007-12-14 19:40:50.866 Using screen 0, 1280x1024 at 0,0
2007-12-14 19:40:50.866 Switching to square mode (blue)
2007-12-14 19:40:50.881 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-12-14 19:40:51.565 Joystick disabled.
2007-12-14 19:40:52.023 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-12-14 19:40:52.141 Registering Internal as a media playback plugin.
2007-12-14 19:40:52.422 Using NV NPOT texture extension
2007-12-14 19:40:53.455 New DB connection, total: 2
2007-12-14 19:40:53.456 Connected to database 'mythconverg' at host: localhost
2007-12-14 19:40:53.478 Connecting to backend server: 192.168.11.4:6543 (try 1 of 5)
2007-12-14 19:40:56.481 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2007-12-14 19:40:57.501 TV: Attempting to change from None to None
2007-12-14 19:40:58.000 Connecting to backend server: 192.168.11.4:6543 (try 1 of 5)
2007-12-14 19:41:01.005 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2007-12-14 19:41:12.052 Connecting to backend server: 192.168.11.4:6543 (try 1 of 5)
2007-12-14 19:41:15.057 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.


In the logs I have restarted backend once and started frontend twice. I cannot really figured out what is wrong in my set up by myself.

---

