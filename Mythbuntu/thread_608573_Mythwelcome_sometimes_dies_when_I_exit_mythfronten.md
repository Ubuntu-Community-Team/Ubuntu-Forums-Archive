---
title: "Mythwelcome sometimes dies when I exit mythfrontend"
date: 2007-11-10
forum: Mythbuntu
---

### Post by skg on 2007-11-10
Hi

I have enabled mythwelcome in /etc/mythtv/session-settings on my newly installed mythbuntu system. (AMD64)

Sometime when I exit mythfrontend dies mythwelcome too. I have not been able to establish a pattern to find the problem.

There is nothing suspicious i /var/log/mythtv/mythwelcome.log

Does anybody have a clue how to solve this?

Regards
Stefan

---

### Post by superm1 on 2007-11-10
Well check and see if possibly any crash reports showed up in /var/crash.

Apport would normally send a notification for them, but its's possible it didn't.

---

### Post by beamish on 2007-11-11
I have the same problem, and there appears to be a crash report; says it's a segmentation violation (signal 11). It usually crashes after mythtfrontend has been started for the first time. I exit mythfrontend, and mythwelcome briefly flashes up, then dies. Nothing in the logs; doing some more investigation. Running latest Mythbuntu AMD64.

---

### Post by skg on 2007-11-12
There is nothing new in /var/crash and nothing related to mythwelcome

---

### Post by EmuMannen on 2008-01-03
I have the same problem (running latest Mythbuntu AMD64)...

---

### Post by rpr on 2008-01-15
I have exact the same problem.
And the strangest part is that mythwelcome isn't really gone because my mediacenter will shutdown after 30 when mythtv won't record.

But it leaves no icon on the upper bar

Checked all the mythtv logs and no error to find.
I activated the mythfrontend using the config file in /etc/mythtv/session

just said mythwelcome = true or something like that.

Running i386 version!

---

### Post by rpr on 2008-01-15
> **superm1 said:**
> Well check and see if possibly any crash reports showed up in /var/crash.

Apport would normally send a notification for them, but its's possible it didn't.

and /var/crash stays clear.
Very annoying problem :(

---

### Post by gurge on 2008-03-02
Hi,

I have the same Problem. AMD64, Mythbuntu 7.10. 

Have somebody found a solution?

---

### Post by Rickytoo on 2008-03-11
I'm experiencing the same problem (running Mythbuntu 7.10). I don't think Mythwelcome is crashing, googling Mythwelcome and focus  reveals  posts that seem to be related. Below is my 'diary' of events showing the problem which relates to MythWelcome and Backend logs. Apart from mythwelcome screen not showing, everything behaves as expected. Any guidance appreciated.

Diary:
09:30 Power up - frontend ruuning
09:35 Exit frontend - no mythwelcome screen, normal desktop
(09:37) System shuts down, power off
09:40 Power up - frontend running
09:45 Exit frontend - no mythwelcome screen, desktop running. Launch frontend (through applications). Exit frontend, mythwelcome screen shows. Start frontend (from mythwelcome). Exiting frontend from this point generally seems to show mythwelcome screen.

Mythwelcome log:
[html]2008-03-08 09:32:15.336 Using runtime prefix = /usr
2008-03-08 09:32:15.419 Gnome-Screensaver support enabled
2008-03-08 09:32:15.419 DPMS is active.
2008-03-08 09:32:15.428 New DB connection, total: 1
2008-03-08 09:32:15.432 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:15.433 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:32:15.438 Using screen 0, 1024x768 at 0,0
2008-03-08 09:32:15.613 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:32:15.614 Using screen 0, 1024x768 at 0,0
2008-03-08 09:32:15.615 Switching to square mode (Mythbuntu)
2008-03-08 09:32:15.763 Using the Qt painter
2008-03-08 09:32:16.308 Joystick disabled.
2008-03-08 09:32:16.396 New DB connection, total: 2
2008-03-08 09:32:16.396 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:16.562 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2008-03-08 09:32:16.783 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:32:16.804 Using protocol version 31
2008-03-08 09:32:18.005 mythshutdown --startup returned: 1
2008-03-08 09:32:18.438 Using runtime prefix = /usr
2008-03-08 09:32:18.448 Gnome-Screensaver support enabled
2008-03-08 09:32:18.448 DPMS is active.
2008-03-08 09:32:18.457 New DB connection, total: 1
2008-03-08 09:32:18.461 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:18.461 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:32:18.463 Using screen 0, 1024x768 at 0,0
2008-03-08 09:32:18.467 Current Schema Version: 1160
2008-03-08 09:32:18.468 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-08 09:32:18.468 Enabled verbose msgs:  important general
2008-03-08 09:32:19.326 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:32:19.327 Using screen 0, 1024x768 at 0,0
2008-03-08 09:32:19.328 Switching to square mode (Mythbuntu)
2008-03-08 09:32:19.339 Using the Qt painter
2008-03-08 09:32:19.699 Joystick disabled.
2008-03-08 09:32:21.232 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-08 09:32:21.267 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-08 09:32:21.332 Registering Internal as a media playback plugin.
2008-03-08 09:32:21.432 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-08 09:32:21.432 Registering MythDVD VCD Media Handler as a media handler ext()
2008-03-08 09:32:21.480 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-03-08 09:32:21.480 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2008-03-08 09:32:21.746 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-08 09:32:21.746 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-08 09:32:21.966 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:32:21.967 Using protocol version 31
2008-03-08 09:41:40.757 Using runtime prefix = /usr
2008-03-08 09:41:40.823 Gnome-Screensaver support enabled
2008-03-08 09:41:40.823 DPMS is active.
2008-03-08 09:41:40.832 New DB connection, total: 1
2008-03-08 09:41:40.836 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:40.837 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:41:40.839 Using screen 0, 1024x768 at 0,0
2008-03-08 09:41:40.997 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:41:40.998 Using screen 0, 1024x768 at 0,0
2008-03-08 09:41:40.999 Switching to square mode (Mythbuntu)
2008-03-08 09:41:41.235 Using the Qt painter
2008-03-08 09:41:41.820 Joystick disabled.
2008-03-08 09:41:42.107 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2008-03-08 09:41:42.375 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:41:42.432 Using protocol version 31
2008-03-08 09:41:43.832 mythshutdown --startup returned: 1
2008-03-08 09:41:44.160 Using runtime prefix = /usr
2008-03-08 09:41:44.167 Gnome-Screensaver support enabled
2008-03-08 09:41:44.167 DPMS is active.
2008-03-08 09:41:44.178 New DB connection, total: 1
2008-03-08 09:41:44.182 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:44.183 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:41:44.184 Using screen 0, 1024x768 at 0,0
2008-03-08 09:41:44.188 Current Schema Version: 1160
2008-03-08 09:41:44.189 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-08 09:41:44.189 Enabled verbose msgs:  important general
2008-03-08 09:41:45.161 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:41:45.162 Using screen 0, 1024x768 at 0,0
2008-03-08 09:41:45.162 Switching to square mode (Mythbuntu)
2008-03-08 09:41:45.173 Using the Qt painter
2008-03-08 09:41:45.517 New DB connection, total: 2
2008-03-08 09:41:45.518 Joystick disabled.
2008-03-08 09:41:45.519 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:46.718 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-08 09:41:46.781 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-08 09:41:46.844 Registering Internal as a media playback plugin.
2008-03-08 09:41:46.953 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-08 09:41:46.954 Registering MythDVD VCD Media Handler as a media handler ext()
2008-03-08 09:41:47.001 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-03-08 09:41:47.001 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2008-03-08 09:41:47.288 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-08 09:41:47.288 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-08 09:41:47.496 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:41:47.497 Using protocol version 31
2008-03-08 09:45:31.449 Using runtime prefix = /usr
2008-03-08 09:45:31.457 Gnome-Screensaver support enabled
2008-03-08 09:45:31.457 DPMS is active.
2008-03-08 09:45:31.467 New DB connection, total: 1
2008-03-08 09:45:31.471 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:45:31.471 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:45:31.474 Using screen 0, 1024x768 at 0,0
2008-03-08 09:45:31.489 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:45:31.490 Using screen 0, 1024x768 at 0,0
2008-03-08 09:45:31.491 Switching to square mode (Mythbuntu)
2008-03-08 09:45:31.503 Using the Qt painter
2008-03-08 09:45:31.833 New DB connection, total: 2
2008-03-08 09:45:31.834 Joystick disabled.
2008-03-08 09:45:31.835 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:45:31.844 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2008-03-08 09:45:31.909 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:45:31.910 Using protocol version 31
2008-03-08 09:45:32.032 mythshutdown --startup returned: 1
2008-03-08 09:45:32.143 Using runtime prefix = /usr
2008-03-08 09:45:32.151 Gnome-Screensaver support enabled
2008-03-08 09:45:32.151 DPMS is active.
2008-03-08 09:45:32.160 New DB connection, total: 1
2008-03-08 09:45:32.164 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:45:32.165 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:45:32.166 Using screen 0, 1024x768 at 0,0
2008-03-08 09:45:32.170 Current Schema Version: 1160
2008-03-08 09:45:32.171 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-08 09:45:32.171 Enabled verbose msgs:  important general
2008-03-08 09:45:32.363 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:45:32.364 Using screen 0, 1024x768 at 0,0
2008-03-08 09:45:32.365 Switching to square mode (Mythbuntu)
2008-03-08 09:45:32.375 Using the Qt painter
2008-03-08 09:45:32.711 New DB connection, total: 2
2008-03-08 09:45:32.711 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:45:32.712 Joystick disabled.
2008-03-08 09:45:33.335 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-08 09:45:33.346 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-08 09:45:33.377 Registering Internal as a media playback plugin.
2008-03-08 09:45:33.399 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-08 09:45:33.399 Registering MythDVD VCD Media Handler as a media handler ext()
2008-03-08 09:45:33.415 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-03-08 09:45:33.415 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2008-03-08 09:45:33.479 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-08 09:45:33.479 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-08 09:45:33.543 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:45:33.544 Using protocol version 31
2008-03-08 09:46:11.559 MythWelcome received a SCHEDULE_CHANGE event
2008-03-08 09:46:35.873 Using runtime prefix = /usr
2008-03-08 09:46:35.881 Gnome-Screensaver support enabled
2008-03-08 09:46:35.881 DPMS is active.
2008-03-08 09:46:35.890 New DB connection, total: 1
2008-03-08 09:46:35.894 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:46:35.895 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:46:35.897 Using screen 0, 1024x768 at 0,0
2008-03-08 09:46:35.902 Current Schema Version: 1160
2008-03-08 09:46:35.903 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-08 09:46:35.903 Enabled verbose msgs:  important general
2008-03-08 09:46:36.101 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:46:36.102 Using screen 0, 1024x768 at 0,0
2008-03-08 09:46:36.102 Switching to square mode (Mythbuntu)
2008-03-08 09:46:36.113 Using the Qt painter
2008-03-08 09:46:36.414 New DB connection, total: 2
2008-03-08 09:46:36.414 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:46:36.415 Joystick disabled.
2008-03-08 09:46:37.045 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-08 09:46:37.056 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-08 09:46:37.089 Registering Internal as a media playback plugin.
2008-03-08 09:46:37.116 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-08 09:46:37.117 Registering MythDVD VCD Media Handler as a media handler ext()
2008-03-08 09:46:37.135 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-03-08 09:46:37.135 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2008-03-08 09:46:37.199 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-08 09:46:37.200 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-08 09:46:37.264 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:46:37.265 Using protocol version 31
2008-03-08 09:47:15.849 Using runtime prefix = /usr
2008-03-08 09:47:15.857 Gnome-Screensaver support enabled
2008-03-08 09:47:15.858 DPMS is active.
2008-03-08 09:47:15.867 New DB connection, total: 1
2008-03-08 09:47:15.870 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:47:15.871 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:47:15.873 Using screen 0, 1024x768 at 0,0
2008-03-08 09:47:15.878 Current Schema Version: 1160
2008-03-08 09:47:15.879 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-08 09:47:15.879 Enabled verbose msgs:  important general
2008-03-08 09:47:16.077 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-08 09:47:16.078 Using screen 0, 1024x768 at 0,0
2008-03-08 09:47:16.078 Switching to square mode (Mythbuntu)
2008-03-08 09:47:16.088 Using the Qt painter
2008-03-08 09:47:16.354 New DB connection, total: 2
2008-03-08 09:47:16.354 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:47:16.355 Joystick disabled.
2008-03-08 09:47:16.991 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-08 09:47:17.002 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-08 09:47:17.034 Registering Internal as a media playback plugin.
2008-03-08 09:47:17.061 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-08 09:47:17.061 Registering MythDVD VCD Media Handler as a media handler ext()
2008-03-08 09:47:17.079 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-03-08 09:47:17.079 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2008-03-08 09:47:17.141 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-08 09:47:17.142 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-03-08 09:47:17.199 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-08 09:47:17.200 Using protocol version 31[/html]Backend log:
[html]2008-03-08 09:32:00.580 Using runtime prefix = /usr
2008-03-08 09:32:01.033 New DB connection, total: 1
2008-03-08 09:32:01.050 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:01.207 Current Schema Version: 1160
Starting up as the master server.
2008-03-08 09:32:01.393 New DB connection, total: 2
2008-03-08 09:32:01.449 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:01.533 EITHelper: localtime offset 0:00:00 
2008-03-08 09:32:01.698 New DB connection, total: 3
2008-03-08 09:32:01.718 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:02.338 EITHelper: localtime offset 0:00:00 
2008-03-08 09:32:03.092 EITHelper: localtime offset 0:00:00 
2008-03-08 09:32:03.817 EITHelper: localtime offset 0:00:00 
2008-03-08 09:32:04.601 New DB scheduler connection
2008-03-08 09:32:04.608 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:32:04.740 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-08 09:32:04.968 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-08 09:32:06.406 Main::Registering HttpStatus Extension
2008-03-08 09:32:06.412 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-03-08 09:32:06.412 Enabled verbose msgs:  important general
2008-03-08 09:32:06.428 AutoExpire: Found 4 recorders w/max rate of 555 MiB/min
2008-03-08 09:32:06.430 AutoExpire: Required Free Space: 5.3 GB w/freq: 5 min
2008-03-08 09:32:06.443 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-08 09:32:06.742 Reschedule requested for id -1.
2008-03-08 09:32:07.797 Scheduled 0 items in 1.1 = 0.96 match + 0.10 place
2008-03-08 09:32:07.803 Seem to be woken up by USER
2008-03-08 09:32:16.871 MainServer::HandleAnnounce Monitor
2008-03-08 09:32:17.181 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:32:17.183 MainServer::HandleAnnounce Monitor
2008-03-08 09:32:17.880 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:32:21.967 MainServer::HandleAnnounce Playback
2008-03-08 09:32:21.978 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:32:21.979 MainServer::HandleAnnounce Monitor
2008-03-08 09:32:21.980 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:33:28.517 EITScanner: Now looking for EIT data on multiplex of channel 16
2008-03-08 09:33:42.281 EITScanner: Now looking for EIT data on multiplex of channel 10
2008-03-08 09:33:46.081 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:33:46.498 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:33:47.264 match[0]: -1800 'Macca's Monday Night' vs. 'FIBA Basketball'
2008-03-08 09:33:49.690 EITScanner: Now looking for EIT data on multiplex of channel 12
2008-03-08 09:33:52.005 match[0]: -8000 'Sky Text and NHS Direct' vs. 'Sky Text and NHS Direct'
2008-03-08 09:33:53.534 match[0]: 0 'Weekend Breakfast with John' vs. 'John Osborne'
2008-03-08 09:33:54.631 match[0]: -11900 'Live: Battle of Britain Build-Up' vs. 'Live: Enzo Maccarnelli v David Haye'
2008-03-08 09:33:55.053 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:33:55.470 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:33:58.396 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:33:58.834 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:34:01.036 EITScanner: Now looking for EIT data on multiplex of channel 1
2008-03-08 09:34:02.171 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:34:02.583 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:34:05.413 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:34:05.827 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:34:10.300 match[0]: 0 'Rock 'n' Roll Football with Russ' vs. 'Russ Williams'
2008-03-08 09:35:06.037 I'm idle now... shutdown will occur in 120 seconds.
2008-03-08 09:35:15.041 110 secs left to system shutdown!
2008-03-08 09:35:25.057 100 secs left to system shutdown!
2008-03-08 09:35:27.953 match[0]: 0 'AFL' vs. 'AFL NAB Cup'
2008-03-08 09:35:29.253 match[0]: 0 'Weekend Breakfast with John' vs. 'John Osborne'
2008-03-08 09:35:35.059 90 secs left to system shutdown!
2008-03-08 09:35:45.064 80 secs left to system shutdown!
2008-03-08 09:35:55.072 70 secs left to system shutdown!
2008-03-08 09:36:05.078 60 secs left to system shutdown!
2008-03-08 09:36:15.084 50 secs left to system shutdown!
2008-03-08 09:36:25.089 40 secs left to system shutdown!
2008-03-08 09:36:25.986 match[0]: 0 'Blue Square Premier Review' vs. 'Cheltenham Review'
2008-03-08 09:36:35.090 30 secs left to system shutdown!
2008-03-08 09:36:37.399 match[0]: 0 'Weekend Breakfast with John' vs. 'John Osborne'
2008-03-08 09:36:45.092 20 secs left to system shutdown!
2008-03-08 09:36:55.096 10 secs left to system shutdown!
2008-03-08 09:41:26.389 Using runtime prefix = /usr
2008-03-08 09:41:26.853 New DB connection, total: 1
2008-03-08 09:41:26.876 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:27.031 Current Schema Version: 1160
Starting up as the master server.
2008-03-08 09:41:27.268 New DB connection, total: 2
2008-03-08 09:41:27.310 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:27.383 EITHelper: localtime offset 0:00:00 
2008-03-08 09:41:27.640 New DB connection, total: 3
2008-03-08 09:41:27.650 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:28.271 EITHelper: localtime offset 0:00:00 
2008-03-08 09:41:29.010 EITHelper: localtime offset 0:00:00 
2008-03-08 09:41:29.739 EITHelper: localtime offset 0:00:00 
2008-03-08 09:41:30.470 New DB scheduler connection
2008-03-08 09:41:30.474 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:41:30.538 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-08 09:41:30.730 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-08 09:41:32.096 Main::Registering HttpStatus Extension
2008-03-08 09:41:32.138 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-03-08 09:41:32.139 Enabled verbose msgs:  important general
2008-03-08 09:41:32.137 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-03-08 09:41:32.163 AutoExpire: Found 4 recorders w/max rate of 555 MiB/min
2008-03-08 09:41:32.166 AutoExpire: Required Free Space: 5.3 GB w/freq: 5 min
2008-03-08 09:41:32.539 Reschedule requested for id -1.
2008-03-08 09:41:33.407 Scheduled 0 items in 0.9 = 0.77 match + 0.10 place
2008-03-08 09:41:33.411 Seem to be woken up by USER
2008-03-08 09:41:42.449 MainServer::HandleAnnounce Monitor
2008-03-08 09:41:43.569 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:41:43.571 MainServer::HandleAnnounce Monitor
2008-03-08 09:41:43.573 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:41:47.497 MainServer::HandleAnnounce Playback
2008-03-08 09:41:47.505 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:41:47.506 MainServer::HandleAnnounce Monitor
2008-03-08 09:41:47.507 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:42:54.310 EITScanner: Now looking for EIT data on multiplex of channel 16
2008-03-08 09:43:08.197 EITScanner: Now looking for EIT data on multiplex of channel 10
2008-03-08 09:43:15.596 EITScanner: Now looking for EIT data on multiplex of channel 12
2008-03-08 09:43:26.740 EITScanner: Now looking for EIT data on multiplex of channel 1
2008-03-08 09:45:01.743 I'm idle now... shutdown will occur in 120 seconds.
2008-03-08 09:45:10.748 110 secs left to system shutdown!
2008-03-08 09:45:20.766 100 secs left to system shutdown!
2008-03-08 09:45:30.770 90 secs left to system shutdown!
2008-03-08 09:45:31.910 MainServer::HandleAnnounce Monitor
2008-03-08 09:45:31.915 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:45:31.916 MainServer::HandleAnnounce Monitor
2008-03-08 09:45:31.917 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:45:33.544 MainServer::HandleAnnounce Playback
2008-03-08 09:45:33.583 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:45:33.585 MainServer::HandleAnnounce Monitor
2008-03-08 09:45:33.586 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:45:56.781 I'm idle now... shutdown will occur in 120 seconds.
2008-03-08 09:46:05.788 110 secs left to system shutdown!
2008-03-08 09:46:11.482 EITScanner: Added 165 EIT Events
2008-03-08 09:46:11.488 Reschedule requested for id -1.
2008-03-08 09:46:11.557 Scheduled 0 items in 0.1 = 0.06 match + 0.01 place
2008-03-08 09:46:12.559 I'm idle now... shutdown will occur in 120 seconds.
2008-03-08 09:46:15.589 match[0]: -3600 'Eredivisie Highlights' vs. 'Six Nations Special'
2008-03-08 09:46:21.571 110 secs left to system shutdown!
2008-03-08 09:46:24.446 match[0]: -1800 'Enzo Maccarnelli v David Haye' vs. 'PGA Tour Highlights'
2008-03-08 09:46:24.472 match[0]: -1800 'The Full SPL' vs. 'Eredivisie Highlights'
2008-03-08 09:46:24.887 match[0]: 0 'Back of the Net' vs. 'Enzo Maccarnelli v David Haye'
2008-03-08 09:46:31.574 100 secs left to system shutdown!
2008-03-08 09:46:37.265 MainServer::HandleAnnounce Playback
2008-03-08 09:46:37.271 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:46:37.273 MainServer::HandleAnnounce Monitor
2008-03-08 09:46:37.273 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:46:46.460 match[0]: 0 'Weekend Breakfast with John' vs. 'John Osborne'
2008-03-08 09:46:55.578 I'm idle now... shutdown will occur in 120 seconds.
2008-03-08 09:47:04.583 110 secs left to system shutdown!
2008-03-08 09:47:14.586 100 secs left to system shutdown!
2008-03-08 09:47:17.200 MainServer::HandleAnnounce Playback
2008-03-08 09:47:17.206 adding: mythtv-desktop as a client (events: 0)
2008-03-08 09:47:17.206 MainServer::HandleAnnounce Monitor
2008-03-08 09:47:17.207 adding: mythtv-desktop as a client (events: 1)
2008-03-08 09:47:55.579 EITScanner: Added 369 EIT Events
2008-03-08 09:47:56.061 EITScanner: Now looking for EIT data on multiplex of channel 700
2008-03-08 09:48:10.281 EITScanner: Added 55 EIT Events
2008-03-08 09:48:10.736 New DB connection, total: 4
2008-03-08 09:48:10.738 Connected to database 'mythconverg' at host: localhost
2008-03-08 09:48:10.741 EITScanner: Now looking for EIT data on multiplex of channel 16
2008-03-08 09:48:31.748 EITScanner: Added 373 EIT Events
2008-03-08 09:48:32.164 EITScanner: Now looking for EIT data on multiplex of channel 1
2008-03-08 09:48:48.930 EITScanner: Added 584 EIT Events
2008-03-08 09:48:48.936 Reschedule requested for id -1.
2008-03-08 09:48:49.007 Scheduled 0 items in 0.1 = 0.06 match + 0.01 place
2008-03-08 09:48:49.388 EITScanner: Now looking for EIT data on multiplex of channel 10[/html]

---

### Post by Rickytoo on 2008-03-13
Okay, I really don't know what I'm talking about. I would be really grateful if someone that does would confirm  what I'm about to say as being good or bad advice....you've been warned!

This issue seems to be one of focus. Mythwelcome  seems to have a problem with evilwm as reported here:
[[html]http://www.mythtv.org/wiki/index.php/Mythwelcome#evilwm[/html]]("http://www.mythtv.org/wiki/index.php/Mythwelcome#evilwm")
There are plenty of other examples of focus problems if you google it.

I followed this suggestion here:
[[html]http://www.mythtv.org/wiki/index.php/Opensuse_10.3#Auto_start_mythwelcome_in_gdm[/html]]("http://www.mythtv.org/wiki/index.php/Opensuse_10.3#Auto_start_mythwelcome_in_gdm")
in the section: Auto start mythwelcome in gdm
which states:
> The mythtv rpm's create an xsession configuration for you, so that you can select mythtv as your session from gdm, this way gnome is not started (faster and saver you some memory) You can select the session from the initial login screen (logout and select another session) 
gdm sessions are stored on the following locations:[LIST]
[*] Directory for xsession  configuration files = /usr/share/xsessions
[*] ~/.dmrc = stored the xsession for the current user[/LIST]If you want to add an xsession for mythwelcome;[LIST]
[*] Add a xsession by copying cp /usr/share/xsessions/mythtv.desktop /usr/share/xsessions/mythwelcm.desktop
[*] Edit /usr/share/xsessions/mythwelcm.desktop so that it executes /usr/bin/mythwelcome and the name = mythwelcm
[*] Now edit ~/.dmrc and change your session to mythwelcm[/LIST]Result, gnome is not started but mythwelcome is started 
And it appears to solve the problem!

Note: should you need to access your normal desktop, you will need to login using an appropriate session. Exiting the frontend should now give you the mythwelcome screen, Ctrl+Alt+Backspace will get you the login screen from where you can select your session.

---

### Post by moonkuh on 2008-03-13
I had the same problem and solved it :)

I solved it with this bugreport

[http://svn.mythtv.org/trac/ticket/3322#comment:2](http://svn.mythtv.org/trac/ticket/3322#comment:2)

I start my backend and mythwelcome with a script

```

#!/bin/sh
/usr/bin/mythbackend &
sleep 10
SESSION_MANAGER=""
unset SESSION_MANAGER
/usr/bin/mythwelcome
SESSION_MANAGER=""
unset SESSION_MANAGER

```

I added SESSION_MANAGER="" and unset SESSION_MANAGER bevor and after i start mythwelcome.
I don't know if it is needed two times and more, but i didn't have the time to look which of the unset or ="" helps.

The only problem with this is that the frontend starts two times, but that is something i can live with

---

### Post by ksarkies on 2008-05-01
Great advice RickyToo. Here's what I did for Ubuntu which didn't have a suitable xsession config. Create mythwelcome.desktop in /usr/share/xsession

> [Desktop Entry]
Encoding=UTF-8
Name=MythWelcome
Comment=Use this session to run MythWelcome
Exec=/usr/bin/mythwelcome
Icon=
Type=Application


then change .dmrc for the user of mythwelcome.

Ken

---

### Post by revival67 on 2008-06-05
I had the same problem with Mythwelcome, but it was solved when i fixed another problem with mytharchive.
all i did was delete the .ICEauthority on boot like mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=610856&page=2]("http://ubuntuforums.org/showthread.php?t=610856&page=2")

Can someone confirm if this is a possible solution for the problem.

Arno

---

### Post by Madusertr on 2008-06-14
Has this problem a bug report on launchpad? (I do not found one.)

I had the same problem, but the tip of moonkuh solved it for me. (Thank you)
I discoverd that my .xsession-errors contains erverytime mythwelcome dies a line
```
ICE default IO error handler doing an exit(), pid = 6120, errno = 32
``` (of course the pid change)

---

### Post by schitthoch2 on 2008-08-29
Hi there,

I have the same problem under MyythBuntu 8.04.1. What would be the cleanest solution if i want to keep my session started with XFCE as it is installed by default but resolving the problem?

I suppose it's the one proposed by ksarkies changing **/usr/share/xsession/mythwelcome.desktop** to
> 
[Desktop Entry]
Encoding=UTF-8
Name=MythWelcome
Comment=Use this session to run MythWelcome
Exec=/usr/bin/mythwelcome
Icon=
Type=Application


and then changing my users **.dmrc** to
> 
[Desktop]
Session=MythWelcome
Language=en_US.UTF-8

Using **Session=MythWelcome** because of **Name=MythWelcome** in **/usr/share/xsession/mythwelcome.desktop**.

Right?

I am a bit unsure because by default there is a **/usr/share/xsession/mythbuntu.desktop** which runs **Exec=/usr/share/mythbuntu/session.sh** and has quite a lot of mythbuntu specific commands in it. I fear loosing some of the functionality of the mythbuntu distro when customizing the startup command.

---

### Post by revival67 on 2008-08-30
All i did was deleting the .ICEauthority on boot.
I got no problems with mythwelcome anymore.


NB: you don't have to use 'vi', you can replace that with 'nano' or 'gedit' or your own fave text editor:

Code:

```
sudo vi /usr/share/mythtv/mythfrontend.sh
```

then add the following lines (I've put them near the top of the file and it works):

Code:

```
# deletes .ICEauthority which makes mytharchive NOT honour cutlist
rm /home/<user>/.ICEauthority
```

this tip is from bigtdp ( [http://ubuntuforums.org/showthread.php?t=610856&page=2](http://ubuntuforums.org/showthread.php?t=610856&page=2) )

---

### Post by Andrew U.K. on 2008-09-01
Cheers revival67 that worked for me.

---

### Post by Andrew U.K. on 2008-09-02
Actually it didn't work in the end. Sometimes it's working and sometimes not.

So I continue......

---

### Post by revival67 on 2008-09-02
shame it didn't work for you

Can you check if the file .ICEauthority exists in your /home/ directory when you got this problem. ?

Maybe it's not deleted on boot?

Good luck

---

### Post by bmwman on 2008-09-03
> 
```
# deletes .ICEauthority which makes mytharchive NOT honour cutlist
rm /home/<user>/.ICEauthority
```

I tried that and works sometimes and doesn't work other time!? Why is that happening?

---

### Post by revival67 on 2008-09-04
strange it works for me everytime.

Where did you add the line 
rm /home/<user>/.ICEauthority

My top part of /usr/share/mythtv/mythfrontend.sh looks like  
```

#!/bin/sh
# Mario Limonciello, March 2007
# partially merged with startmythtv.sh by Michael Haas, October 2007

#source our dialog functions
. /usr/share/mythtv/dialog_functions.sh

# deletes .ICEauthority resolves problems with mytharchive and mythwelcome
rm /home/arno/.ICEauthority

#find the session, dialog, and su manager we will be using for display
find_session
find_dialog
find_su

#check that we are in the mythtv group
check_groups
```

Can you do: ```
ls -A .ICEauthority
```
in your Terminal.
If everything works well it should give you:
```
ls: cannot access .ICEauthority: No such file or directory

```

How are you logged in as a regular user, or as user mythtv.
I am logged in as user arno, not as user mythtv.

If this doesn't help maybe you should try the solution of moonkuh.

Arno

---

### Post by bmwman on 2008-09-04
It works more often than it crashes so I think it's not that crusial. Is there a way to make the Mythwelcome to check if I have Azureus or Amarok running before shutdown and prevent it if they're running?

Thanks.

---

