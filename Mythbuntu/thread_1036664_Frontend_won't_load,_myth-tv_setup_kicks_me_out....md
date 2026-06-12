---
title: "Frontend won't load, myth-tv setup kicks me out..."
date: 2009-01-11
forum: Mythbuntu
---

### Post by emmiesix on 2009-01-11
Instead of just buying a new video card like I should have, I have been struggling to make the ATI Radeon 7000 I have work in mythbuntu.

Through the following commands I was able to get the TV output on the composite (erroneously labeled S-video):

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

Which (for the most part) will at least get output to my TV.  Problem is that it gets wiped on every restart and I don't want to keep an extra monitor around.  So I inserted the above commands in my /etc/rc.local file above exit 0, and figured that would work, right?

Well now, I have more problems.

Upon booting, I get the mythbuntu desktop environment instead of the welcome screen, and while the theme claims to be loading (the every-annoying bit about sizing clips) nothing actually happens.  I can go into applications and try and load it and same thing, no menu of options pops up.  I've looked at the log files and no obvious errors pop out at me (admitted noob here).

Even bigger problem is that if I try to go into the mythbuntu setup, I just get an error message that a bunch of directories don't exist. (I put them in the storage group section on first setting up, intending to create them later).  This is my fault for not figuring out where to create those dirs, but after this error pops up, I can either say "No I know what I'm doing" at which point it KICKS ME OUT of setup, or I can say "Yes fix this problem" which does nothing.  I can click on it all day and nothing changes on the display.

I really don't want to have to do a re-install so if anyone has any ideas I'm listening.

---

### Post by emmiesix on 2009-01-11
Well no one has any insight so I'll post some more info.  I took out those lines in the rc.local (which wasn't working anyway... grr!!!) and the problem persists.  Here is what is in my logsL

==> /var/log/mythtv/mtd.log <==
mtd started at Sun Jan 11 07:54:16 2009
mtd is running on a host called dvr-machine
07:54:16: Waiting for connections/jobs
07:54:16: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-01-11 01:50:56.590 Empty LocalHostName.
2009-01-11 01:50:56.592 Using localhost value of dvr-machine
2009-01-11 01:50:56.601 New DB connection, total: 1
2009-01-11 01:50:56.608 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:50:56.610 Closing DB connection named 'DBManager0'
2009-01-11 01:50:56.613 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:50:56.620 New DB connection, total: 2
2009-01-11 01:50:56.622 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:50:56.627 Current Schema Version: 1214
Starting up as the master server.
2009-01-11 01:50:56.669 New DB connection, total: 3
2009-01-11 01:50:56.671 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:50:56.897 New DB scheduler connection
2009-01-11 01:50:56.904 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:50:56.977 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-11 01:50:56.978 Main::Registering HttpStatus Extension
2009-01-11 01:50:56.979 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 01:50:56.980 Enabled verbose msgs:  important general
2009-01-11 01:50:56.986 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-11 01:50:59.908 Reschedule requested for id -1.
2009-01-11 01:50:59.946 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-01-11 01:50:59.959 Seem to be woken up by USER
2009-01-11 01:51:04.764 MainServer::HandleAnnounce Monitor
2009-01-11 01:51:04.774 adding: dvr-machine as a client (events: 0)
2009-01-11 01:51:04.776 MainServer::HandleAnnounce Monitor
2009-01-11 01:51:04.777 adding: dvr-machine as a client (events: 1)
2009-01-11 01:51:04.781 Reschedule requested for id -1.
2009-01-11 01:51:04.823 Scheduled 0 items in 0.0 = 0.01 match + 0.04 place
2009-01-11 01:52:18.307 Using runtime prefix = /usr
2009-01-11 01:52:18.348 Empty LocalHostName.
2009-01-11 01:52:18.359 Using localhost value of dvr-machine
2009-01-11 01:52:18.368 New DB connection, total: 1
2009-01-11 01:52:18.382 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:18.384 Closing DB connection named 'DBManager0'
2009-01-11 01:52:18.386 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:18.389 New DB connection, total: 2
2009-01-11 01:52:18.393 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:18.399 Current Schema Version: 1214
Starting up as the master server.
2009-01-11 01:52:18.434 New DB connection, total: 3
2009-01-11 01:52:18.441 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:18.655 New DB scheduler connection
2009-01-11 01:52:18.667 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:18.775 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-11 01:52:18.776 Main::Registering HttpStatus Extension
2009-01-11 01:52:18.777 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 01:52:18.780 Enabled verbose msgs:  important general
2009-01-11 01:52:18.786 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-11 01:52:21.672 Reschedule requested for id -1.
2009-01-11 01:52:21.701 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-01-11 01:52:21.708 Seem to be woken up by USER
2009-01-11 01:52:52.900 Using runtime prefix = /usr
2009-01-11 01:52:52.929 Empty LocalHostName.
2009-01-11 01:52:52.932 Using localhost value of dvr-machine
2009-01-11 01:52:52.941 New DB connection, total: 1
2009-01-11 01:52:52.949 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:52.951 Closing DB connection named 'DBManager0'
2009-01-11 01:52:52.953 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:52.967 New DB connection, total: 2
2009-01-11 01:52:52.969 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:52.977 Current Schema Version: 1214
Starting up as the master server.
2009-01-11 01:52:53.010 New DB connection, total: 3
2009-01-11 01:52:53.012 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:53.238 New DB scheduler connection
2009-01-11 01:52:53.246 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:52:53.330 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-11 01:52:53.332 Main::Registering HttpStatus Extension
2009-01-11 01:52:53.333 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 01:52:53.336 Enabled verbose msgs:  important general
2009-01-11 01:52:53.348 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-11 01:52:56.254 Reschedule requested for id -1.
2009-01-11 01:52:56.284 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-01-11 01:52:56.294 Seem to be woken up by USER
2009-01-11 01:54:13.256 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2009-01-11 01:54:13.268 AutoExpire: ERROR: Filesystem Info cache is empty, unable to determine what Recordings to expire
2009-01-11 07:54:01.156 Using runtime prefix = /usr
2009-01-11 07:54:01.216 Empty LocalHostName.
2009-01-11 07:54:01.282 Using localhost value of dvr-machine
2009-01-11 07:54:01.354 New DB connection, total: 1
2009-01-11 07:54:01.402 Connected to database 'mythconverg' at host: localhost
2009-01-11 07:54:01.501 Closing DB connection named 'DBManager0'
2009-01-11 07:54:01.507 Connected to database 'mythconverg' at host: localhost
2009-01-11 07:54:01.510 New DB connection, total: 2
2009-01-11 07:54:01.511 Connected to database 'mythconverg' at host: localhost
2009-01-11 07:54:01.543 Current Schema Version: 1214
Starting up as the master server.
2009-01-11 07:54:08.013 New DB connection, total: 3
2009-01-11 07:54:08.020 Connected to database 'mythconverg' at host: localhost
2009-01-11 07:54:08.294 New DB scheduler connection
2009-01-11 07:54:08.302 Connected to database 'mythconverg' at host: localhost
2009-01-11 07:54:08.391 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-11 07:54:08.411 Main::Registering HttpStatus Extension
2009-01-11 07:54:08.435 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 07:54:08.436 Enabled verbose msgs:  important general
2009-01-11 07:54:08.471 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-11 07:54:11.309 Reschedule requested for id -1.
2009-01-11 07:54:11.375 Scheduled 0 items in 0.0 = 0.02 match + 0.02 place
2009-01-11 07:54:11.408 Seem to be woken up by USER
2009-01-11 07:55:27.474 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
Starting mythfrontend.real..
2009-01-11 01:48:45.105 New DB connection, total: 2
2009-01-11 01:48:45.106 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:48:45.108 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 01:48:45.109 Enabled verbose msgs:  important general
2009-01-11 01:48:48.608 Primary screen 0.
2009-01-11 01:48:48.609 Using screen 0, 1024x768 at 0,0
2009-01-11 01:48:48.624 The theme (blootube) is missing a themeinfo.xml file
2009-01-11 01:48:48.624 Switching to square mode (blootube)
2009-01-11 01:48:48.837 Using the Qt painter
2009-01-11 01:48:48.840 lirc init success using configuration file: /home/meyer/.mythtv/lircrc
2009-01-11 01:48:48.841 JoystickMenuClient Error: Joystick disabled - Failed to read /home/meyer/.mythtv/joystickmenurc
2009-01-11 01:48:50.010 Loading from: /usr/share/mythtv/themes/default/base.xml
QImage::smoothScale: Image is a null image
2009-01-11 01:48:50.159 Registering Internal as a media playback plugin.
2009-01-11 01:48:50.379 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-11 01:48:50.733 Failed to run 'cdrecord --scanbus'
2009-01-11 01:48:50.737 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-11 01:48:50.741 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-11 01:48:50.801 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.3:5060 NAT address 192.168.2.3
SIP: Cannot register; proxy, username or password not set
Couldn't find theme /home/meyer/.mythtv/themes/blootube
Destroying SipFsm object 
2009-01-11 01:48:51.462 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-11 01:49:07.470 New DB connection, total: 2
2009-01-11 01:49:07.471 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:49:07.474 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 01:49:07.475 Enabled verbose msgs:  important general
2009-01-11 01:49:08.146 Primary screen 0.
2009-01-11 01:49:08.146 Using screen 0, 1024x768 at 0,0
2009-01-11 01:49:08.147 The theme (blootube) is missing a themeinfo.xml file
2009-01-11 01:49:08.147 Switching to square mode (blootube)
2009-01-11 01:49:08.167 Using the Qt painter
2009-01-11 01:49:08.170 lirc init success using configuration file: /home/meyer/.mythtv/lircrc
2009-01-11 01:49:08.170 JoystickMenuClient Error: Joystick disabled - Failed to read /home/meyer/.mythtv/joystickmenurc
2009-01-11 01:49:08.618 Loading from: /usr/share/mythtv/themes/default/base.xml
QImage::smoothScale: Image is a null image
2009-01-11 01:49:08.662 Registering Internal as a media playback plugin.
2009-01-11 01:49:08.748 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-11 01:49:08.787 Failed to run 'cdrecord --scanbus'
2009-01-11 01:49:08.791 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-11 01:49:08.795 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-11 01:49:08.839 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.3:5060 NAT address 192.168.2.3
SIP: Cannot register; proxy, username or password not set
Couldn't find theme /home/meyer/.mythtv/themes/blootube
Destroying SipFsm object 
2009-01-11 01:49:09.433 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-11 01:50:22.673 New DB connection, total: 2
2009-01-11 01:50:22.674 Connected to database 'mythconverg' at host: localhost
2009-01-11 01:50:22.678 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 01:50:22.678 Enabled verbose msgs:  important general
2009-01-11 01:50:23.336 Primary screen 0.
2009-01-11 01:50:23.337 Using screen 0, 1024x768 at 0,0
2009-01-11 01:50:23.337 The theme (blootube) is missing a themeinfo.xml file
2009-01-11 01:50:23.338 Switching to square mode (blootube)
2009-01-11 01:50:23.357 Using the Qt painter
2009-01-11 01:50:23.360 lirc init success using configuration file: /home/meyer/.mythtv/lircrc
2009-01-11 01:50:23.360 JoystickMenuClient Error: Joystick disabled - Failed to read /home/meyer/.mythtv/joystickmenurc
2009-01-11 01:50:23.820 Loading from: /usr/share/mythtv/themes/default/base.xml
QImage::smoothScale: Image is a null image
2009-01-11 01:50:23.860 Registering Internal as a media playback plugin.
2009-01-11 01:50:23.946 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-11 01:50:23.985 Failed to run 'cdrecord --scanbus'
2009-01-11 01:50:23.989 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-11 01:50:23.993 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-11 01:50:24.037 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.3:5060 NAT address 192.168.2.3
SIP: Cannot register; proxy, username or password not set
Couldn't find theme /home/meyer/.mythtv/themes/blootube
Destroying SipFsm object 
2009-01-11 01:50:24.649 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-11 07:54:22.774 New DB connection, total: 2
2009-01-11 07:54:22.787 Connected to database 'mythconverg' at host: localhost
2009-01-11 07:54:22.790 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-11 07:54:22.790 Enabled verbose msgs:  important general
2009-01-11 07:54:26.128 Primary screen 0.
2009-01-11 07:54:26.129 Using screen 0, 1024x768 at 0,0
2009-01-11 07:54:26.152 The theme (blootube) is missing a themeinfo.xml file
2009-01-11 07:54:26.153 Switching to square mode (blootube)
2009-01-11 07:54:26.483 Using the Qt painter
2009-01-11 07:54:26.486 lirc init success using configuration file: /home/meyer/.mythtv/lircrc
2009-01-11 07:54:26.486 JoystickMenuClient Error: Joystick disabled - Failed to read /home/meyer/.mythtv/joystickmenurc
2009-01-11 07:54:27.465 Loading from: /usr/share/mythtv/themes/default/base.xml
QImage::smoothScale: Image is a null image
2009-01-11 07:54:27.608 Registering Internal as a media playback plugin.
2009-01-11 07:54:27.804 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-11 07:54:28.171 Failed to run 'cdrecord --scanbus'
2009-01-11 07:54:28.175 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-11 07:54:28.179 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-11 07:54:28.238 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.3:5060 NAT address 192.168.2.3
SIP: Cannot register; proxy, username or password not set
Couldn't find theme /home/meyer/.mythtv/themes/blootube
Destroying SipFsm object 
2009-01-11 07:54:28.909 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==



I think it's odd that the welcome log is empty???  I have a feeling this is related to my xorg.conf file that I was messing with.

---

### Post by emmiesix on 2009-01-11
Ok, for reference (you know, if anyone wants to help :) ), here is my xorg.conf file.  running the configure command NEVER worked for me, it only asked about some stupid keyboard stuff and then didn't even bother to load it into the file.   Never even got video questions.  So this is all cobbled together by hand:


Section "Device"
	Identifier	"Radeon 7000VE"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 7000VE"
	DefaultDepth	24
	SubSection "Display"
		   Depth	24
		   Modes	"1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection
	
Section "Extensions"
	Option "Composite" "Enable"
EndSection

---

### Post by emmiesix on 2009-01-11
Ok, I know I'm just talking to myself at this point but being a newbie and linux-idiot in general I figure I should keep posting because these forums have helped me and it might help someone else...

The problem with the frontend and setup refusing to load was related to the themes.  While trying to fix the problem of caching themes, I created the .mythtv/themes/ directory (something the log file complained didn't exist).  Well if you do that, then mythtv thinks that is where your themes are located and they AREN'T so everything fails to load up and display.

Deleted the folder and everything is ok.

By the way, this would probably have been easier to realise if I followed the rule "change one thing at a time" and reboot inbetween but... oh well.

---

