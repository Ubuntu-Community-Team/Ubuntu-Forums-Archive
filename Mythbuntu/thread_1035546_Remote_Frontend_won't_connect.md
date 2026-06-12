---
title: "Remote Frontend won't connect"
date: 2009-01-09
forum: Mythbuntu
---

### Post by quasifly on 2009-01-09
Cannot get my computer in my bedroom to connect to my Mythbunto 8.10 Backend/Frontend in my living room. Im trying to connect using the Mythbuntu 8.10 Live CD. I've been trying for a couple of weeks with no luck. Let me know if there is any other logs or files or info that would be helpful. Here is my mysql.txt :

DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'

---

### Post by ~~MAINFRAIME²~~ on 2009-01-09
Did you setup the backend to allow remote connections?
If not open the backend setup goto general and enter the correct IP of your box and not 127.0.0.1

---

### Post by quasifly on 2009-01-09
> **~~MAINFRAIME²~~ said:**
> Did you setup the backend to allow remote connections?
If not open the backend setup goto general and enter the correct IP of your box and not 127.0.0.1

Thanks. How do I figure out the IP address of my box?

---

### Post by andrewc6l on 2009-01-09
From a command shell on the backend, type:

ifconfig

You'll see a bunch of stuff that starts something like this:

eth0      Link encap:Ethernet  HWaddr 00:13:2A:06:BD:9C
          inet addr:192.168.33.22  Bcast:192.168.33.255 Mask:255.255.254.0

The "inet addr:192.168.33.22" is the IP address. Each network card will have its own, and there will be another one for the loopback interface (lo = 127.0.0.1).

---

### Post by quasifly on 2009-01-11
Here's what I get:

aaron@aaron-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:cf:41:b8 
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fecf:41b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66183 errors:0 dropped:0 overruns:1 frame:0
          TX packets:13019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23465395 (23.4 MB)  TX bytes:1676372 (1.6 MB)
          Interrupt:5 Base address:0xc00

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:824702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:320075303 (320.0 MB)  TX bytes:320075303 (320.0 MB)

---------------------------

So I went to backend setup went to general and changed my IP address to 192.168.2.104
Is this correct?

Next I did this:

**aaron@aaron-desktop:~$ sudo dpkg-reconfigure mythtv-database**

to set up the database. Then I tried to log on my remote frontend using the live CD. No luck. Any suggestions?

Thanks

> **andrewc6l said:**
> From a command shell on the backend, type:

ifconfig

You'll see a bunch of stuff that starts something like this:

eth0      Link encap:Ethernet  HWaddr 00:13:2A:06:BD:9C
          inet addr:192.168.33.22  Bcast:192.168.33.255 Mask:255.255.254.0

The "inet addr:192.168.33.22" is the IP address. Each network card will have its own, and there will be another one for the loopback interface (lo = 127.0.0.1).

---

### Post by SiHa on 2009-01-11
did you set a PIN in the backend setup? (Second page of general setup,I think)

It's slightly counter-intuitive, in that if you don't want to use a PIN to allow remote frontend access, you have to specify **0000**.

---

### Post by quasifly on 2009-01-11
Yeah, I already set the pin to 0000 
Im not really sure what the pin is, though. Im still unable to connect.

> **SiHa said:**
> did you set a PIN in the backend setup? (Second page of general setup,I think)

It's slightly counter-intuitive, in that if you don't want to use a PIN to allow remote frontend access, you have to specify **0000**.

---

### Post by quasifly on 2009-01-12
Is there anything else I could post that might help solve this for me? I'm not sure if it is a password thing, or router settings, or something else. Let me know if as I am fairly lost at this point.

Thanks

---

### Post by larsolav on 2009-01-12
You may have already done this, but I just want to make sure: On the backend, in Mythbuntu control centre, did you set the backend to allow frontend access, I think it may be under the "advanced" or something section, something about enabling remote MySQL access...
Also, in the backend setup, I believe the IP address has to be listed in both places under General:

> General
If you will be deploying multiple backends, or if your backend is on one system and you're running the frontend on another machine then do not use the "127.0.0.1" IP address.

NOTE: If you modify the 127.0.0.1 address and use a "real" IP address, you must use real IP addresses in both fields, otherwise your frontend machines will generate "Unexpected response to MYTH_PROTO_VERSION" errors.
[http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1]("http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1") 
 

Sorry to have bothered you if you already knew this...
Good luck

---

### Post by quasifly on 2009-01-15
I had the backend set to allow frontend access under control center. I have the IP address in backend setup set in both places to: 192.168.2.104

I did finally get the remote frontend to connect using:

mythtv
C1RFOK1E
mythconverg
192.168.2.104

I can watch Live TV but no recorded TV. All of the recordings show up like they usually do (even the video preview) but when I try to play one, the screen goes black for a second or two and then it returns me back to the Watch Recordings menu.

I did a little research and found this:

[http://ubuntuforums.org/showthread.php?t=943929]("http://ubuntuforums.org/showthread.php?t=943929")

I tried to log myth frontend. This is what I typed:

buntu@ubuntu:~$ mythfrontend -l ~/mythfrontend.log
2009-01-15 19:04:32.627 Using runtime prefix = /usr
2009-01-15 19:04:33.147 XScreenSaver support enabled
2009-01-15 19:04:33.148 DPMS is active.
2009-01-15 19:04:33.148 Empty LocalHostName.
2009-01-15 19:04:33.148 Using localhost value of ubuntu
2009-01-15 19:04:33.148 Testing network connectivity to 192.168.2.104
2009-01-15 19:04:33.161 New DB connection, total: 1
2009-01-15 19:04:33.204 Unable to connect to database!
2009-01-15 19:04:33.205 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'ubuntu' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-01-15 19:04:33.256 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

2009-01-15 19:04:33.483 UPnPautoconf() - Found one UPnP backend
2009-01-15 19:04:33.527 Testing network connectivity to 192.168.2.104
2009-01-15 19:04:33.532 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 19:04:33.533 Closing DB connection named 'DBManager0'
2009-01-15 19:04:33.535 Primary screen 0.
2009-01-15 19:04:33.536 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 19:04:33.537 Using screen 0, 1280x960 at 0,0

----------------------

And here is my mythfrontend.log:

2009-01-15 18:19:18.808 New DB connection, total: 2
2009-01-15 18:19:18.810 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 18:19:18.814 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-15 18:19:18.814 Enabled verbose msgs:  important general
2009-01-15 18:19:22.575 No theme dir: /home/ubuntu/.mythtv/themes/G.A.N.T
2009-01-15 18:19:22.577 Primary screen 0.
2009-01-15 18:19:22.577 Using screen 0, 2048x1536 at 0,0
2009-01-15 18:19:22.577 No theme dir: /home/ubuntu/.mythtv/themes/G.A.N.T
2009-01-15 18:19:22.578 Switching to square mode (G.A.N.T)
2009-01-15 18:19:22.753 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-15 18:19:22.754 lirc_init failed for mythtv, see preceding messages
2009-01-15 18:19:22.754 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ubuntu/.mythtv/joystickmenurc
2009-01-15 18:20:22.646 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-15 18:20:22.838 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-15 18:20:22.929 Registering Internal as a media playback plugin.
2009-01-15 18:20:23.376 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-15 18:20:24.695 Failed to run 'cdrecord --scanbus'
2009-01-15 18:20:24.700 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-15 18:20:24.702 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-15 18:20:24.759 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.108:5060 NAT address 192.168.2.108
SIP: Cannot register; proxy, username or password not set
2009-01-15 18:20:25.250 No theme dir: /home/ubuntu/.mythtv/themes/G.A.N.T
2009-01-15 18:20:30.246 Connecting to backend server: 192.168.2.104:6543 (try 1 of 5)
2009-01-15 18:20:30.247 Using protocol version 40
2009-01-15 18:20:30.300 TV: Attempting to change from None to WatchingLiveTV
2009-01-15 18:20:30.301 Using protocol version 40
2009-01-15 18:20:33.261 New DB connection, total: 3
2009-01-15 18:20:33.263 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 18:20:33.307 DPMS Deactivated 
2009-01-15 18:20:34.033 AFD: Opened codec 0x906cf70, id(MPEG2VIDEO) type(Video)
2009-01-15 18:20:34.033 AFD: codec MP2 has 2 channels
2009-01-15 18:20:34.033 AFD: Opened codec 0x906c620, id(MP2) type(Audio)
2009-01-15 18:20:34.417 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-15 18:20:34.417 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-01-15 18:20:34.480 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-01-15 18:20:34.528 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-01-15 18:20:34.528 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-01-15 18:20:34.528 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x90ac6b8) visual(0x90ac618) 
                        XJ_depth(24) WxH(2048x1536) bpl(6144)
2009-01-15 18:20:34.528 VideoOutputXv Error: Failed to create X buffers.
2009-01-15 18:20:34.547 GLVid, Error: Fatal error
2009-01-15 18:20:34.551 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-01-15 18:20:34.551 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***
2009-01-15 18:20:34.583 OSD Theme Dimensions W: 640 H: 480
2009-01-15 18:20:35.423 TV: Changing from None to WatchingLiveTV
2009-01-15 18:20:35.424 New DB connection, total: 4
2009-01-15 18:20:35.424 Realtime priority would require SUID as root.
2009-01-15 18:20:35.426 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 18:20:35.429 Failed to approve 'bobdeint' deinterlacer
2009-01-15 18:20:35.429 Couldn't load deinterlace filter 
2009-01-15 18:20:35.431 Video timing method: USleep with busy wait
2009-01-15 18:20:40.055 VideoOutputXv Error: 
***
* Your system is not capable of displaying the
* full framerate at 2048x1536 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

2009-01-15 18:21:10.529 NVP: prebuffering pause
2009-01-15 18:21:12.285 NVP: Prebuffer wait timed out 10 times.
2009-01-15 18:21:17.378 NVP: prebuffering pause
2009-01-15 18:21:22.655 NVP: prebuffering pause
2009-01-15 18:22:32.705 NVP: prebuffering pause
2009-01-15 18:23:33.239 NVP: prebuffering pause
2009-01-15 18:23:59.418 TV: Attempting to change from WatchingLiveTV to None
2009-01-15 18:24:00.049 TV: Changing from WatchingLiveTV to None
2009-01-15 18:24:00.118 DPMS Reactivated.
2009-01-15 18:24:19.552 Loading from: /usr/share/mythtv/themes/default/appear-ui.xml
2009-01-15 18:25:12.266 Received a remote 'Clear Cache' request
2009-01-15 18:32:05.137 TV: Attempting to change from None to WatchingLiveTV
2009-01-15 18:32:05.138 Using protocol version 40
2009-01-15 18:32:07.242 DPMS Deactivated 
2009-01-15 18:32:07.937 AFD: Opened codec 0xb3158c40, id(MPEG2VIDEO) type(Video)
2009-01-15 18:32:07.937 AFD: codec MP2 has 2 channels
2009-01-15 18:32:07.937 AFD: Opened codec 0xb310bb70, id(MP2) type(Audio)
2009-01-15 18:32:08.123 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-15 18:32:08.123 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-01-15 18:32:08.167 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-01-15 18:32:08.213 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-01-15 18:32:08.213 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-01-15 18:32:08.213 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xb3157790) visual(0xb315b710) 
                        XJ_depth(24) WxH(2048x1536) bpl(6144)
2009-01-15 18:32:08.213 VideoOutputXv Error: Failed to create X buffers.
2009-01-15 18:32:08.227 GLVid, Error: Fatal error
2009-01-15 18:32:08.231 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-01-15 18:32:08.231 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***
2009-01-15 18:32:08.262 OSD Theme Dimensions W: 640 H: 480
2009-01-15 18:32:08.489 TV: Changing from None to WatchingLiveTV
2009-01-15 18:32:08.493 Realtime priority would require SUID as root.
2009-01-15 18:32:08.504 Failed to approve 'bobdeint' deinterlacer
2009-01-15 18:32:08.504 Couldn't load deinterlace filter 
2009-01-15 18:32:08.506 Video timing method: USleep with busy wait
2009-01-15 18:32:13.014 VideoOutputXv Error: 
***
* Your system is not capable of displaying the
* full framerate at 2048x1536 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

2009-01-15 18:34:37.597 NVP: prebuffering pause
2009-01-15 18:34:45.110 NVP: prebuffering pause
2009-01-15 18:55:08.022 TV: Attempting to change from WatchingLiveTV to None
2009-01-15 18:55:08.483 TV: Changing from WatchingLiveTV to None
2009-01-15 18:55:08.523 DPMS Reactivated.
Destroying SipFsm object 
2009-01-15 18:55:11.600 Deleting UPnP client...
2009-01-15 19:04:33.583 New DB connection, total: 2
2009-01-15 19:04:33.584 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 19:04:33.593 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-15 19:04:33.593 Enabled verbose msgs:  important general
2009-01-15 19:04:34.237 No theme dir: /home/ubuntu/.mythtv/themes/G.A.N.T
2009-01-15 19:04:34.238 Primary screen 0.
2009-01-15 19:04:34.238 Using screen 0, 1280x960 at 0,0
2009-01-15 19:04:34.239 No theme dir: /home/ubuntu/.mythtv/themes/G.A.N.T
2009-01-15 19:04:34.239 Switching to square mode (G.A.N.T)
2009-01-15 19:04:34.256 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-15 19:04:34.256 lirc_init failed for mythtv, see preceding messages
2009-01-15 19:04:34.256 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ubuntu/.mythtv/joystickmenurc
2009-01-15 19:04:34.487 Removing stale cache dir: /home/ubuntu/.mythtv/themecache/G.A.N.T.2048.1536
2009-01-15 19:04:34.493 Removing stale cache dir: /home/ubuntu/.mythtv/themecache/G.A.N.T.2048.1536/bkg
2009-01-15 19:04:34.497 Removing stale cache dir: /home/ubuntu/.mythtv/themecache/G.A.N.T.2048.1536/keyboard
2009-01-15 19:04:34.511 Removing stale cache dir: /home/ubuntu/.mythtv/themecache/G.A.N.T.2048.1536/title
2009-01-15 19:04:34.513 Removing stale cache dir: /home/ubuntu/.mythtv/themecache/G.A.N.T.2048.1536/type
2009-01-15 19:04:34.514 Removing stale cache dir: /home/ubuntu/.mythtv/themecache/G.A.N.T.2048.1536/watermark
2009-01-15 19:05:01.758 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-15 19:05:01.837 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-15 19:05:01.893 Registering Internal as a media playback plugin.
2009-01-15 19:05:02.013 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-15 19:05:02.038 Failed to run 'cdrecord --scanbus'
2009-01-15 19:05:02.040 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-15 19:05:02.042 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-15 19:05:02.089 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.108:5060 NAT address 192.168.2.108
SIP: Cannot register; proxy, username or password not set
2009-01-15 19:05:02.217 No theme dir: /home/ubuntu/.mythtv/themes/G.A.N.T
2009-01-15 19:05:08.750 Connecting to backend server: 192.168.2.104:6543 (try 1 of 5)
2009-01-15 19:05:08.751 Using protocol version 40
2009-01-15 19:05:08.760 TV: Attempting to change from None to WatchingLiveTV
2009-01-15 19:05:08.761 Using protocol version 40
2009-01-15 19:05:11.591 New DB connection, total: 3
2009-01-15 19:05:11.592 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 19:05:11.668 DPMS Deactivated 
2009-01-15 19:05:12.432 AFD: Opened codec 0xb3133bd0, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:12.432 AFD: codec MP2 has 2 channels
2009-01-15 19:05:12.432 AFD: Opened codec 0xb3110560, id(MP2) type(Audio)
2009-01-15 19:05:12.497 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-15 19:05:12.497 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-01-15 19:05:12.543 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-01-15 19:05:12.593 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-01-15 19:05:12.593 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2009-01-15 19:05:12.593 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xaebe1118) visual(0xaebdd288) 
                        XJ_depth(24) WxH(1280x960) bpl(3840)
2009-01-15 19:05:12.594 VideoOutputXv Error: Failed to create X buffers.
2009-01-15 19:05:12.610 GLVid, Error: Fatal error
2009-01-15 19:05:12.614 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-01-15 19:05:12.614 VideoOutputXv: Falling back to X shared memory video output.
			      *** May be slow ***
2009-01-15 19:05:12.646 OSD Theme Dimensions W: 640 H: 480
2009-01-15 19:05:12.948 TV: Changing from None to WatchingLiveTV
2009-01-15 19:05:12.949 New DB connection, total: 4
2009-01-15 19:05:12.949 Realtime priority would require SUID as root.
2009-01-15 19:05:12.950 Connected to database 'mythconverg' at host: 192.168.2.104
2009-01-15 19:05:12.953 Failed to approve 'bobdeint' deinterlacer
2009-01-15 19:05:12.953 Couldn't load deinterlace filter 
2009-01-15 19:05:12.954 Video timing method: USleep with busy wait
2009-01-15 19:05:36.102 TV: Attempting to change from WatchingLiveTV to None
2009-01-15 19:05:36.620 TV: Changing from WatchingLiveTV to None
2009-01-15 19:05:36.705 DPMS Reactivated.
2009-01-15 19:05:44.003 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T/ui.xml
2009-01-15 19:05:47.459 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:47.459 AFD: codec MP2 has 2 channels
2009-01-15 19:05:47.459 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:05:49.925 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:49.926 AFD: codec MP2 has 2 channels
2009-01-15 19:05:49.926 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:05:51.442 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:51.442 AFD: codec MP2 has 2 channels
2009-01-15 19:05:51.443 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:05:52.454 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:52.454 AFD: codec MP2 has 2 channels
2009-01-15 19:05:52.454 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:05:55.422 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:55.422 AFD: codec MP2 has 2 channels
2009-01-15 19:05:55.422 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:05:56.246 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:56.247 AFD: codec MP2 has 2 channels
2009-01-15 19:05:56.247 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:05:57.425 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:05:57.425 AFD: codec MP2 has 2 channels
2009-01-15 19:05:57.426 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
2009-01-15 19:06:00.957 GetRecordBasename found no entry
2009-01-15 19:06:00.968 TV: Attempting to change from None to WatchingPreRecorded
2009-01-15 19:06:00.969 GetRecordBasename found no entry
2009-01-15 19:06:07.469 RingBuf(/var/lib/mythtv/recordings/): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/'.
2009-01-15 19:06:08.697 AFD: Opened codec 0xa18cc50, id(MPEG2VIDEO) type(Video)
2009-01-15 19:06:08.698 AFD: codec MP2 has 2 channels
2009-01-15 19:06:08.698 AFD: Opened codec 0xa4c8330, id(MP2) type(Audio)
Destroying SipFsm object 
2009-01-15 19:06:18.159 Deleting UPnP client...

--------------------------------------------------
 
Anybody have any ideas or suggestions?

Thanks again.

---

### Post by larsolav on 2009-01-15
Maybe on your bedroom frontend you can try to change the playback profile? Maybe try the normal or CPU- (or something like that)profiles?

---

### Post by quasifly on 2009-01-15
> **larsolav said:**
> Maybe on your bedroom frontend you can try to change the playback profile? Maybe try the normal or CPU- (or something like that)profiles?

Tried CPU-- and still can't watch recorded TV. Live TV still works.

---

### Post by quasifly on 2009-01-15
Ok got it working. I had to correct the timezone. I remember reading that somewhere. Thanks to all who helped. Next Im going to try to get it working on a full install of the mythbuntu frontend instead of the live CD. Ive been having problems with that but Im feeling more confident now.

---

