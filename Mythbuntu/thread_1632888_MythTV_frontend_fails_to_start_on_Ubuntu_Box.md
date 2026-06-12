---
title: "MythTV frontend fails to start on Ubuntu Box"
date: 2010-11-28
forum: Mythbuntu
---

### Post by sprogmeister on 2010-11-28
I have installed and used MythTV on a ubuntu machine (used as front and backend) and it worked fine until I mad adjustments, as described: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php). Having played with the system utilities it now fails to start at all. I cannot access the front or back end. I have tried restarts but do not know where to look. Please help!

---

### Post by Penguin=) on 2010-11-28
Try starting it in the terminal.

---

### Post by sprogmeister on 2010-11-28
Thanks tried, "mythfrontend" and got this output:


2010-11-28 21:38:40.847 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-28 21:38:40.848 Using runtime prefix = /usr
2010-11-28 21:38:40.848 Using configuration directory = /home/iain/.mythtv
2010-11-28 21:38:41.549 Empty LocalHostName.
2010-11-28 21:38:41.550 Using localhost value of iain-laptop
2010-11-28 21:38:41.569 New DB connection, total: 1
2010-11-28 21:38:41.573 Connected to database 'mythconverg' at host: localhost
2010-11-28 21:38:41.574 Closing DB connection named 'DBManager0'
2010-11-28 21:38:41.593 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-28 21:38:41.594 DPMS is active.
2010-11-28 21:38:41.595 Primary screen: 0.
2010-11-28 21:38:41.596 Connected to database 'mythconverg' at host: localhost
2010-11-28 21:38:41.597 Using screen 0, 1280x800 at 0,0
2010-11-28 21:38:41.621 Desktop video mode: 1280x800 59.9988 Hz
2010-11-28 21:38:41.633 MythUI Image Cache size set to 20971520 bytes
2010-11-28 21:38:41.666 AudioPulseUtil: Suspend Success
2010-11-28 21:38:41.667 Enabled verbose msgs:  important general
2010-11-28 21:38:41.671 Primary screen: 0.
2010-11-28 21:38:41.671 Using screen 0, 1280x800 at 0,0
2010-11-28 21:38:41.672 Using theme base resolution of 1920x1080
2010-11-28 21:38:41.676 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-11-28 21:38:41.677 JoystickMenuThread Error: Joystick disabled - Failed to read /home/iain/.mythtv/joystickmenurc
2010-11-28 21:38:41.713 Using Frameless Window
2010-11-28 21:38:41.713 Using Full Screen Window
2010-11-28 21:38:41.994 Using the Qt painter
Floating point exception

---

### Post by sprogmeister on 2010-11-29
When checking the backend for errors this is the result:

tail -f /var/log/mythtv/mythbackend.log
2010-11-29 19:01:10.672 Connected to database 'mythconverg' at host: localhost
2010-11-29 19:01:10.707 New DB scheduler connection
2010-11-29 19:01:10.715 Connected to database 'mythconverg' at host: localhost
2010-11-29 19:01:10.736 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-11-29 19:01:10.742 Main::Registering HttpStatus Extension
2010-11-29 19:01:10.750 Enabled verbose msgs:  important general
2010-11-29 19:01:10.771 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-29 19:01:13.728 Reschedule requested for id -1.
2010-11-29 19:01:13.798 Scheduled 0 items in 0.1 = 0.04 match + 0.02 place
2010-11-29 19:01:13.809 Seem to be woken up by USER
2010-11-29 19:02:30.728 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

The front end:

2010-11-29 19:08:43.252 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-29 19:08:43.253 Using runtime prefix = /usr
2010-11-29 19:08:43.253 Using configuration directory = /home/iain/.mythtv
2010-11-29 19:08:43.836 Empty LocalHostName.
2010-11-29 19:08:43.836 Using localhost value of iain-laptop
2010-11-29 19:08:43.857 New DB connection, total: 1
2010-11-29 19:08:43.861 Connected to database 'mythconverg' at host: localhost
2010-11-29 19:08:43.862 Closing DB connection named 'DBManager0'
2010-11-29 19:08:43.879 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-29 19:08:43.880 DPMS is active.
2010-11-29 19:08:43.882 Primary screen: 0.
2010-11-29 19:08:43.882 Connected to database 'mythconverg' at host: localhost
2010-11-29 19:08:43.883 Using screen 0, 1280x800 at 0,0
2010-11-29 19:08:43.909 Desktop video mode: 1280x800 59.9988 Hz
2010-11-29 19:08:43.921 MythUI Image Cache size set to 20971520 bytes
2010-11-29 19:08:43.955 AudioPulseUtil: Suspend Success
2010-11-29 19:08:43.956 Enabled verbose msgs:  important general
2010-11-29 19:08:43.960 Primary screen: 0.
2010-11-29 19:08:43.961 Using screen 0, 1280x800 at 0,0
2010-11-29 19:08:43.961 Using theme base resolution of 1920x1080
2010-11-29 19:08:43.966 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-11-29 19:08:43.967 JoystickMenuThread Error: Joystick disabled - Failed to read /home/iain/.mythtv/joystickmenurc
2010-11-29 19:08:44.010 Using Frameless Window
2010-11-29 19:08:44.010 Using Full Screen Window
2010-11-29 19:08:44.291 Using the Qt painter
Floating point exception

Please help!

---

### Post by sprogmeister on 2010-11-29
Also from the front end:

tail -f /var/log/mythtv/mythfrontend.log
2010-11-29 21:27:03.165 Enabled verbose msgs:  important general
2010-11-29 21:27:03.170 Primary screen: 0.
2010-11-29 21:27:03.170 Using screen 0, 1280x800 at 0,0
2010-11-29 21:27:03.171 Using theme base resolution of 1920x1080
2010-11-29 21:27:03.175 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-11-29 21:27:03.175 JoystickMenuThread Error: Joystick disabled - Failed to read /home/iain/.mythtv/joystickmenurc
2010-11-29 21:27:03.217 Using Frameless Window
2010-11-29 21:27:03.217 Using Full Screen Window
2010-11-29 21:27:03.546 Using the Qt painter

---

### Post by sprogmeister on 2010-11-29
I also found this:

 sudo /usr/bin/mythbackend
2010-11-29 22:05:14.495 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-29 22:05:14.495 Using runtime prefix = /usr
2010-11-29 22:05:14.495 Using configuration directory = /home/iain/.mythtv
2010-11-29 22:05:14.496 Empty LocalHostName.
2010-11-29 22:05:14.496 Using localhost value of iain-laptop
2010-11-29 22:05:14.509 New DB connection, total: 1
2010-11-29 22:05:14.513 Connected to database 'mythconverg' at host: localhost
2010-11-29 22:05:14.513 Closing DB connection named 'DBManager0'
2010-11-29 22:05:14.514 Connected to database 'mythconverg' at host: localhost
2010-11-29 22:05:14.517 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-29 22:05:14.519 MythBackend: Starting up as the master server.
2010-11-29 22:05:14.524 New DB connection, total: 2
2010-11-29 22:05:14.528 Connected to database 'mythconverg' at host: localhost
2010-11-29 22:05:14.531 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.581 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.632 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.682 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.732 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.783 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.833 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.883 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.934 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:14.984 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.034 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.085 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.135 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.185 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.236 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.286 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.336 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.387 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.437 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.487 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2010-11-29 22:05:15.487 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-11-29 22:05:15.488 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2010-11-29 22:05:15.490 New DB connection, total: 3
2010-11-29 22:05:15.491 Connected to database 'mythconverg' at host: localhost
2010-11-29 22:05:15.503 MediaServer::HttpServer Create Error
2010-11-29 22:05:15.504 Enabled verbose msgs:  important general
2010-11-29 22:05:15.506 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-29 22:05:15.508 Failed to bind port 6543. Exiting.
2010-11-29 22:05:15.509 Backend exiting, MainServer initialization error.
Error in my_thread_global_end(): 1 threads didn't exit

---

### Post by thatguruguy on 2010-11-29
It seems that you either don't have a capture card defined, or that it is not defined correctly.  If it is a digital tuner, does it work with metv?

---

### Post by sprogmeister on 2010-11-30
I had the receiver work with Kaffeine but it still did not work with Myth TV. Myth TV will not let me into the backend to change the settings. I have tried complete removal and install and still the same. I really am confused!

---

### Post by nickrout on 2010-11-30
> **sprogmeister said:**
> I had the receiver work with Kaffeine but it still did not work with Myth TV. Myth TV will not let me into the backend to change the settings. I have tried complete removal and install and still the same. I really am confused!

the "mythbuntu" way is to run mythbuntu-control-centre and start the backend config from in there. (in the mysql tab i think)

---

### Post by sprogmeister on 2010-12-06
Thanks for the replies. I will loo more next month when I have arrived in my new abode and set up.

---

