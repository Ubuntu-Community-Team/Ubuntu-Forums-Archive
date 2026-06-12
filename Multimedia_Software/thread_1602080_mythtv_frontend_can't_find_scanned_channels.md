---
title: "mythtv frontend can't find scanned channels"
date: 2010-10-21
forum: Multimedia Software
---

### Post by parminides on 2010-10-21
I can't get mythtv to play television with my Hauppauge HVR-850 tv card. I was able to view tv in mplayer, so I know that the card is working.

The tv signal is broadcast only (no cable).

I had to set the card type to DVB DTV capture card (v3.x) to get mythtv-setup to successfully scan. I was able to successfully scan both with a "full scan" and with a channels.conf file that I had generated earlier when tinkering tv in mplayer.

Unfortunately, the mythtv frontend failed to play any live tv. It said "Error: MythTV is using all inputs, but there are no active recordings?"

Selections from /var/log/mythtv/mythbackend.log:

```

2010-10-21 07:36:48.500 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
2010-10-21 07:37:00.775 ChannelBase(7) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2010-10-21 07:37:00.803 TVRec(8) Error: Problem finding starting channel, setting to default of '3'.
2010-10-21 07:37:00.812 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:02.211 DVBChan(8:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-10-21 07:37:02.220 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?

```

Selection from /var/log/mythtv/mythfrontend.log:

```

2010-10-21 07:37:29.464 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)

```

The last part of /var/log/mythtv/mythbackend.log is...

```

2010-10-21 07:36:04.729 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-10-21 07:36:04.763 Using runtime prefix = /usr
2010-10-21 07:36:04.786 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 07:36:04.795 Empty LocalHostName.
2010-10-21 07:36:04.802 Using localhost value of MusicCityNoise
2010-10-21 07:36:04.823 New DB connection, total: 1
2010-10-21 07:36:04.828 Unable to connect to database!
2010-10-21 07:36:04.836 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-10-21 07:36:04.845 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-10-21 07:36:04.853 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.
.2010-10-21 07:36:04.946 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
...............................................................................
2010-10-21 07:36:06.935 UPnPautoconf() - No UPnP backends found
2010-10-21 07:36:06.952 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-10-21 07:36:07.186 Deleting UPnP client...
2010-10-21 07:36:07.194 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-10-21 07:36:43.560 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-10-21 07:36:43.809 Using runtime prefix = /usr
2010-10-21 07:36:44.270 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 07:36:44.429 Empty LocalHostName.
2010-10-21 07:36:44.576 Using localhost value of MusicCityNoise
2010-10-21 07:36:44.851 New DB connection, total: 1
2010-10-21 07:36:44.954 Unable to connect to database!
2010-10-21 07:36:45.004 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-10-21 07:36:45.072 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-10-21 07:36:45.159 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.2010-10-21 07:36:45.372 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

SSDP::PerformSearch - did not write entire buffer.
...............................................................................
2010-10-21 07:36:47.708 UPnPautoconf() - No UPnP backends found
2010-10-21 07:36:47.729 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-10-21 07:36:47.779 Deleting UPnP client...
2010-10-21 07:36:47.787 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-10-21 07:36:48.193 Failed to init MythContext, exiting.
2010-10-21 07:36:48.239 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-10-21 07:36:48.240 Using runtime prefix = /usr
2010-10-21 07:36:48.245 Using configuration directory = /home/mythtv/.mythtv
2010-10-21 07:36:48.254 Empty LocalHostName.
2010-10-21 07:36:48.262 Using localhost value of MusicCityNoise
2010-10-21 07:36:48.275 New DB connection, total: 1
2010-10-21 07:36:48.300 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:36:48.320 Closing DB connection named 'DBManager0'
2010-10-21 07:36:48.329 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:36:48.362 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 07:36:48.396 MythBackend: Starting up as the master server.
2010-10-21 07:36:48.420 New DB connection, total: 2
2010-10-21 07:36:48.437 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:36:48.500 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
2010-10-21 07:37:00.775 ChannelBase(7) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2010-10-21 07:37:00.803 TVRec(8) Error: Problem finding starting channel, setting to default of '3'.
2010-10-21 07:37:00.812 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:00.870 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:00.928 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:00.987 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.045 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.103 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.162 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.220 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.278 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.337 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.395 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.737 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.795 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.853 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.912 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:01.970 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:02.028 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:02.087 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:02.145 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:02.203 DVBChan(8:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-10-21 07:37:02.211 DVBChan(8:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-10-21 07:37:02.220 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2010-10-21 07:37:02.230 New DB connection, total: 3
d2010-10-21 07:37:02.237 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:37:02.243 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-10-21 07:37:02.253 Main::Registering HttpStatus Extension
2010-10-21 07:37:02.261 Enabled verbose msgs:  important general
2010-10-21 07:37:02.291 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-21 07:37:31.971 MainServer::ANN Monitor
2010-10-21 07:37:32.022 adding: MusicCityNoise as a client (events: 0)
2010-10-21 07:37:32.085 MainServer::ANN Monitor
2010-10-21 07:37:32.116 adding: MusicCityNoise as a client (events: 1)
2010-10-21 07:38:22.232 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

The last part of /var/log/mythtv/mythfrontend.log is...

```

Starting mythfrontend.real..
2010-10-21 07:37:28.764 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-10-21 07:37:28.764 Using runtime prefix = /usr
2010-10-21 07:37:28.764 Using configuration directory = /home/clarkb/.mythtv
2010-10-21 07:37:29.113 Empty LocalHostName.
2010-10-21 07:37:29.113 Using localhost value of MusicCityNoise
2010-10-21 07:37:29.119 New DB connection, total: 1
2010-10-21 07:37:29.121 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:37:29.122 Closing DB connection named 'DBManager0'
2010-10-21 07:37:29.150 ScreenSaverX11Private: Gnome screen saver support enabled
2010-10-21 07:37:29.151 DPMS is active.
2010-10-21 07:37:29.168 Primary screen: 0.
2010-10-21 07:37:29.169 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:37:29.170 Using screen 0, 1680x1050 at 0,0
2010-10-21 07:37:29.234 Desktop video mode: 1680x1050 60.412 Hz
2010-10-21 07:37:29.330 MythUI Image Cache size set to 20971520 bytes
2010-10-21 07:37:29.371 AudioPulseUtil: Suspend Success
2010-10-21 07:37:29.372 Enabled verbose msgs:  important general
2010-10-21 07:37:29.405 Primary screen: 0.
2010-10-21 07:37:29.405 Using screen 0, 1680x1050 at 0,0
2010-10-21 07:37:29.451 Using theme base resolution of 1280x720
2010-10-21 07:37:29.464 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-10-21 07:37:29.464 JoystickMenuThread Error: Joystick disabled - Failed to read /home/clarkb/.mythtv/joystickmenurc
2010-10-21 07:37:29.504 Using Frameless Window
2010-10-21 07:37:29.504 Using Full Screen Window
2010-10-21 07:37:29.849 Using the Qt painter
2010-10-21 07:37:30.060 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-10-21 07:37:30.158 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-10-21 07:37:30.215 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-10-21 07:37:30.215 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-10-21 07:37:30.219 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-21 07:37:30.253 New DB connection, total: 2
2010-10-21 07:37:30.253 New DB connection, total: 3
2010-10-21 07:37:30.253 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:37:30.253 Connected to database 'mythconverg' at host: localhost
2010-10-21 07:37:30.972 Registering Internal as a media playback plugin.
2010-10-21 07:37:30.998 No plugins directory /usr/lib/mythtv/plugins
2010-10-21 07:37:31.004 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-21 07:37:31.005 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-21 07:37:31.005 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-21 07:37:31.006 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-21 07:37:31.006 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-21 07:37:31.007 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-21 07:37:31.008 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-10-21 07:37:31.084 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-10-21 07:37:31.086 Found mainmenu.xml for theme 'Mythbuntu'
2010-10-21 07:37:31.970 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-10-21 07:37:31.971 Using protocol version 56
2010-10-21 07:37:40.876 AudioPulseUtil: Resume Success
2010-10-21 07:37:40.876 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

```

---

### Post by parminides on 2010-10-21
I don't know what I did to fix it. I tried so many different things. I do remember that at the end it had a blank screen in mythtv until I rebooted!

---

