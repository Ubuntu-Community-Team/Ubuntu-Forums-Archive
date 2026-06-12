---
title: "&quot;Capture cards&quot; section under mythtv-setup not loading"
date: 2009-02-03
forum: Mythbuntu
---

### Post by GCFreak on 2009-02-03
Hi guys,

I managed to build a better machine than the Dell I was running, except for the video card but that's not important since I'm not getting any hardware acceleration off of it anyway.

I've sorted out most of the problems, no driver installation problems, system is picking up the Nova-T 500 perfectly, proprietary drivers are working, except when I go to add the capture card under MythTV's backend setup, I enter "Capture cards", "add capture card" and then nothing. Just the familiar black detailed background, I have to Ctrl+Alt+Esc+Click to kill mythtv-setup. I can supply logs if you need it.

Thanks in advance.

EDIT: Also, I have another problem I might as well put in here as well. =)

MythDVD. After about 1 second after starting a DVD from my server (gigabit ethernet) the video pauses and the sound continues to play but is stuttering to no end. VLC and MPlayer have no issues, haven't tried xine.

Thanks.

---

### Post by GCFreak on 2009-02-04
Bump. To be honest, I'm getting tired of most of my threads being ignored.

---

### Post by tgm4883 on 2009-02-04
Insert logs.  And by mythdvd, I hope you mean mythvideo, since mythdvd is no more, or are you running mythtv > 0.21

---

### Post by GCFreak on 2009-02-05
Hi tgm4883,

Thanks for replying to my thread. And yes, I mean MythVideo =P

errorlogs.log from Mythbuntu Log Grabber:
```
==> /var/log/mythtv/mtd.log <==
mtd started at Sun Feb 1 12:27:44 2009
mtd is running on a host called mediacentre
12:27:44: Waiting for connections/jobs
12:27:44: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-02-06 14:14:32.188 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:14:32.356 UPnpMedia: BuildMediaMap VIDEO scan starting in :/dull/movies:
2009-02-06 14:14:32.990 UPnpMedia: BuildMediaMap Done. Found 750 objects
2009-02-06 14:14:45.058 MainServer::HandleAnnounce Monitor
2009-02-06 14:14:45.063 adding: mediacentre as a client (events: 0)
2009-02-06 14:14:45.065 MainServer::HandleAnnounce Monitor
2009-02-06 14:14:45.065 adding: mediacentre as a client (events: 1)
2009-02-06 14:16:13.537 Using runtime prefix = /usr
2009-02-06 14:16:13.570 Empty LocalHostName.
2009-02-06 14:16:13.571 Using localhost value of mediacentre
2009-02-06 14:16:13.579 New DB connection, total: 1
2009-02-06 14:16:13.585 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:16:13.586 Closing DB connection named 'DBManager0'
2009-02-06 14:16:13.588 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:16:13.600 New DB connection, total: 2
2009-02-06 14:16:13.605 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:16:13.609 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-02-06 14:16:14.943 Main::Registering HttpStatus Extension
2009-02-06 14:16:14.951 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:16:14.959 Enabled verbose msgs:  important general
2009-02-06 14:16:14.961 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 14:16:23.746 UPnpMedia: BuildMediaMap VIDEO scan starting in :/dull/movies:
2009-02-06 14:16:24.156 UPnpMedia: BuildMediaMap Done. Found 750 objects
2009-02-06 14:17:33.639 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QSqlQuery::exec: database not open
2009-02-06 14:19:23.722 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2009-02-06 14:19:23.776 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
No error type from QSqlError?  Strange...
2009-02-06 14:21:58.680 Using runtime prefix = /usr
2009-02-06 14:21:58.727 Empty LocalHostName.
2009-02-06 14:21:58.757 Using localhost value of mediacentre
2009-02-06 14:21:58.858 New DB connection, total: 1
2009-02-06 14:21:58.926 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:21:58.947 Closing DB connection named 'DBManager0'
2009-02-06 14:21:58.950 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:21:58.953 New DB connection, total: 2
2009-02-06 14:21:58.955 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:21:58.977 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-02-06 14:22:00.273 Main::Registering HttpStatus Extension
2009-02-06 14:22:00.312 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:22:00.331 Enabled verbose msgs:  important general
2009-02-06 14:22:00.357 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 14:22:09.232 UPnpMedia: BuildMediaMap VIDEO scan starting in :/dull/movies:
2009-02-06 14:22:09.721 UPnpMedia: BuildMediaMap Done. Found 750 objects
2009-02-06 14:22:34.791 MainServer::HandleAnnounce Monitor
2009-02-06 14:22:34.797 adding: mediacentre as a client (events: 0)
2009-02-06 14:22:34.798 MainServer::HandleAnnounce Monitor
2009-02-06 14:22:34.798 adding: mediacentre as a client (events: 1)
2009-02-06 14:23:10.087 Using runtime prefix = /usr
2009-02-06 14:23:10.096 Empty LocalHostName.
2009-02-06 14:23:10.124 Using localhost value of mediacentre
2009-02-06 14:23:10.134 New DB connection, total: 1
2009-02-06 14:23:10.140 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:23:10.141 Closing DB connection named 'DBManager0'
2009-02-06 14:23:10.143 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:23:10.146 New DB connection, total: 2
2009-02-06 14:23:10.149 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:23:10.154 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-02-06 14:23:11.489 Main::Registering HttpStatus Extension
2009-02-06 14:23:11.502 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:23:11.517 Enabled verbose msgs:  important general
2009-02-06 14:23:11.519 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 14:23:20.297 UPnpMedia: BuildMediaMap VIDEO scan starting in :/dull/movies:
2009-02-06 14:23:20.911 UPnpMedia: BuildMediaMap Done. Found 750 objects
2009-02-06 14:24:30.182 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 14:33:28.995 Using runtime prefix = /usr
2009-02-06 14:33:29.004 Empty LocalHostName.
2009-02-06 14:33:29.020 Using localhost value of mediacentre
2009-02-06 14:33:29.041 New DB connection, total: 1
2009-02-06 14:33:29.047 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:33:29.049 Closing DB connection named 'DBManager0'
2009-02-06 14:33:29.050 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:33:29.062 New DB connection, total: 2
2009-02-06 14:33:29.072 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:33:29.075 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-02-06 14:33:30.414 Main::Registering HttpStatus Extension
2009-02-06 14:33:30.421 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:33:30.425 Enabled verbose msgs:  important general
2009-02-06 14:33:30.430 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-02-06 14:33:39.218 UPnpMedia: BuildMediaMap VIDEO scan starting in :/dull/movies:
2009-02-06 14:33:39.692 UPnpMedia: BuildMediaMap Done. Found 750 objects

==> /var/log/mythtv/mythfrontend.log <==
Starting mythfrontend.real..
2009-02-06 14:05:55.472 New DB connection, total: 2
2009-02-06 14:05:55.472 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:05:55.474 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:05:55.474 Enabled verbose msgs:  important general
2009-02-06 14:05:59.751 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:05:59.752 Primary screen 0.
2009-02-06 14:05:59.752 Using screen 0, 1024x768 at 0,0
2009-02-06 14:05:59.753 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:05:59.754 Switching to square mode (Mythbuntu-8.04)
2009-02-06 14:06:00.034 Using the Qt painter
2009-02-06 14:06:00.035 lirc init success using configuration file: /home/media/.mythtv/lircrc
2009-02-06 14:06:00.035 JoystickMenuClient Error: Joystick disabled - Failed to read /home/media/.mythtv/joystickmenurc
2009-02-06 14:06:01.903 Specified base font 'medium' does not exist for font clock
2009-02-06 14:06:01.903 Specified base font 'medium' does not exist for font small
2009-02-06 14:06:01.904 Specified base font 'medium' does not exist for font medium
2009-02-06 14:06:01.904 Specified base font 'medium' does not exist for font large
2009-02-06 14:06:01.904 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-02-06 14:06:02.003 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-06 14:06:02.069 Registering Internal as a media playback plugin.
2009-02-06 14:06:02.250 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-06 14:06:02.565 Failed to run 'cdrecord --scanbus'
2009-02-06 14:06:02.570 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-06 14:06:02.575 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-06 14:06:02.600 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-02-06 14:06:02.732 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:06:05.028 Connecting to backend server: 10.1.1.6:6543 (try 1 of 5)
2009-02-06 14:06:05.042 Using protocol version 40
2009-02-06 14:06:06.376 Deleting UPnP client...
Starting mythfrontend.real..
2009-02-06 14:14:36.903 New DB connection, total: 2
2009-02-06 14:14:36.903 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:14:36.905 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:14:36.905 Enabled verbose msgs:  important general
2009-02-06 14:14:39.705 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:14:39.706 Primary screen 0.
2009-02-06 14:14:39.706 Using screen 0, 1024x768 at 0,0
2009-02-06 14:14:39.707 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:14:39.708 Switching to square mode (Mythbuntu-8.04)
2009-02-06 14:14:39.961 Using the Qt painter
2009-02-06 14:14:39.962 lirc init success using configuration file: /home/media/.mythtv/lircrc
2009-02-06 14:14:39.963 JoystickMenuClient Error: Joystick disabled - Failed to read /home/media/.mythtv/joystickmenurc
2009-02-06 14:14:41.755 Specified base font 'medium' does not exist for font clock
2009-02-06 14:14:41.755 Specified base font 'medium' does not exist for font small
2009-02-06 14:14:41.755 Specified base font 'medium' does not exist for font medium
2009-02-06 14:14:41.755 Specified base font 'medium' does not exist for font large
2009-02-06 14:14:41.756 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-02-06 14:14:41.864 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-06 14:14:41.930 Registering Internal as a media playback plugin.
2009-02-06 14:14:42.066 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-06 14:14:42.364 Failed to run 'cdrecord --scanbus'
2009-02-06 14:14:42.369 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-06 14:14:42.374 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-06 14:14:42.399 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-02-06 14:14:42.531 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:14:45.043 Connecting to backend server: 10.1.1.6:6543 (try 1 of 5)
2009-02-06 14:14:45.057 Using protocol version 40
2009-02-06 14:14:48.261 Deleting UPnP client...
Starting mythfrontend.real..
2009-02-06 14:22:18.393 New DB connection, total: 2
2009-02-06 14:22:18.423 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:22:18.424 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-02-06 14:22:18.425 Enabled verbose msgs:  important general
2009-02-06 14:22:21.678 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:22:21.680 Primary screen 0.
2009-02-06 14:22:21.680 Using screen 0, 1024x768 at 0,0
2009-02-06 14:22:21.681 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:22:21.681 Switching to square mode (Mythbuntu-8.04)
2009-02-06 14:22:21.874 Using the Qt painter
2009-02-06 14:22:21.876 lirc init success using configuration file: /home/media/.mythtv/lircrc
2009-02-06 14:22:21.876 JoystickMenuClient Error: Joystick disabled - Failed to read /home/media/.mythtv/joystickmenurc
2009-02-06 14:22:23.524 Specified base font 'medium' does not exist for font clock
2009-02-06 14:22:23.524 Specified base font 'medium' does not exist for font small
2009-02-06 14:22:23.524 Specified base font 'medium' does not exist for font medium
2009-02-06 14:22:23.525 Specified base font 'medium' does not exist for font large
2009-02-06 14:22:23.525 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-02-06 14:22:23.621 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-02-06 14:22:23.690 Registering Internal as a media playback plugin.
2009-02-06 14:22:23.869 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-02-06 14:22:24.181 Failed to run 'cdrecord --scanbus'
2009-02-06 14:22:24.186 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-02-06 14:22:24.191 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-02-06 14:22:24.218 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-02-06 14:22:24.350 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-02-06 14:22:34.770 Connecting to backend server: 10.1.1.6:6543 (try 1 of 5)
2009-02-06 14:22:34.791 Using protocol version 40
2009-02-06 14:22:36.309 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Feb  6 14:21:51 mediacentre kernel: [   19.813196] type=1505 audit(1233883287.016:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4089
Feb  6 14:21:51 mediacentre kernel: [   20.005974] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb  6 14:21:51 mediacentre kernel: [   20.069932] skge eth0: enabling interface
Feb  6 14:21:51 mediacentre kernel: [   22.491664] skge eth0: Link is up at 1000 Mbps, full duplex, flow control none
Feb  6 14:21:51 mediacentre kernel: [   22.724972]  CIFS VFS: Server requests plain text password but client support disabled
Feb  6 14:21:51 mediacentre kernel: [   41.509721] NET: Registered protocol family 10
Feb  6 14:21:51 mediacentre kernel: [   41.510216] lo: Disabled Privacy Extensions
Feb  6 14:21:51 mediacentre kernel: [   42.060557] RPC: Registered udp transport module.
Feb  6 14:21:51 mediacentre kernel: [   42.060561] RPC: Registered tcp transport module.
Feb  6 14:21:51 mediacentre kernel: [   43.314350] ACPI: WMI: Mapper loaded
Feb  6 14:21:51 mediacentre kernel: [   43.679322] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Found user 'avahi' (UID 111) and group 'avahi' (GID 120).
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Successfully dropped root privileges.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: avahi-daemon 0.6.23 starting up.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Successfully called chroot().
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Successfully dropped remaining capabilities.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: No service file found in /etc/avahi/services.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.1.6.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: New relevant interface eth0.IPv4 for mDNS.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Network interface enumeration completed.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Registering new address record for fe80::213:d4ff:febc:13 on eth0.*.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Registering new address record for 10.1.1.6 on eth0.IPv4.
Feb  6 14:21:51 mediacentre avahi-daemon[4806]: Registering HINFO record with values 'I686'/'LINUX'.
Feb  6 14:21:52 mediacentre avahi-daemon[4806]: Server startup complete. Host name is mediacentre.local. Local service cookie is 1864444430.
Feb  6 14:21:53 mediacentre atieventsd[4901]: ATI External Events Daemon started... 
Feb  6 14:21:53 mediacentre atieventsd[4901]: Event daemon control socket created 
Feb  6 14:21:53 mediacentre acpid: client connected from 4901[0:0] 
Feb  6 14:21:53 mediacentre atieventsd[4901]: acpid connection established 
Feb  6 14:21:53 mediacentre kernel: [   46.326506] ppdev: user-space parallel port driver
Feb  6 14:21:54 mediacentre mysqld_safe[5102]: started
Feb  6 14:21:54 mediacentre mysqld[5106]: 090206 14:21:54 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
Feb  6 14:21:55 mediacentre mysqld[5106]: 090206 14:21:55  InnoDB: Started; log sequence number 0 81271
Feb  6 14:21:55 mediacentre mysqld[5106]: 090206 14:21:55 [Note] /usr/sbin/mysqld: ready for connections.
Feb  6 14:21:55 mediacentre mysqld[5106]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Feb  6 14:21:55 mediacentre /etc/mysql/debian-start[5144]: Upgrading MySQL tables if necessary.
Feb  6 14:21:56 mediacentre /etc/mysql/debian-start[5149]: Looking for 'mysql' in: /usr/bin/mysql
Feb  6 14:21:56 mediacentre /etc/mysql/debian-start[5149]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Feb  6 14:21:56 mediacentre /etc/mysql/debian-start[5149]: This installation of MySQL is already upgraded to 5.0.67, use --force if you still need to run mysql_upgrade
Feb  6 14:21:56 mediacentre /etc/mysql/debian-start[5169]: Checking for insecure root accounts.
Feb  6 14:21:56 mediacentre /etc/mysql/debian-start[5175]: WARNING: mysql.user contains 3 root accounts without password!
Feb  6 14:21:56 mediacentre /etc/mysql/debian-start[5177]: Triggering myisam-recover for all MyISAM tables
Feb  6 14:21:58 mediacentre kernel: [   51.568020] eth0: no IPv6 routers present
Feb  6 14:21:58 mediacentre kernel: [   51.700169] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Feb  6 14:21:59 mediacentre kernel: [   51.826626] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Feb  6 14:21:59 mediacentre kernel: [   51.837377] NFSD: starting 90-second grace period
Feb  6 14:22:00 mediacentre acpid: client connected from 5567[113:122] 
Feb  6 14:22:01 mediacentre bluetoothd[5630]: Bluetooth daemon
Feb  6 14:22:01 mediacentre kernel: [   53.922248] Bluetooth: Core ver 2.13
Feb  6 14:22:01 mediacentre kernel: [   53.923820] NET: Registered protocol family 31
Feb  6 14:22:01 mediacentre kernel: [   53.923825] Bluetooth: HCI device and connection manager initialized
Feb  6 14:22:01 mediacentre kernel: [   53.923830] Bluetooth: HCI socket layer initialized
Feb  6 14:22:01 mediacentre bluetoothd[5630]: Starting SDP server
Feb  6 14:22:01 mediacentre kernel: [   53.996114] Bluetooth: L2CAP ver 2.11
Feb  6 14:22:01 mediacentre kernel: [   53.996119] Bluetooth: L2CAP socket layer initialized
Feb  6 14:22:01 mediacentre kernel: [   54.031799] Bluetooth: SCO (Voice Link) ver 0.6
Feb  6 14:22:01 mediacentre kernel: [   54.031805] Bluetooth: SCO socket layer initialized
Feb  6 14:22:01 mediacentre bluetoothd[5630]: Starting experimental netlink support
Feb  6 14:22:01 mediacentre bluetoothd[5630]: Failed to find Bluetooth netlink family
Feb  6 14:22:01 mediacentre bluetoothd[5630]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Feb  6 14:22:01 mediacentre kernel: [   54.058009] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb  6 14:22:01 mediacentre kernel: [   54.058015] Bluetooth: BNEP filters: protocol multicast
Feb  6 14:22:01 mediacentre kernel: [   54.079961] Bridge firewalling registered
Feb  6 14:22:01 mediacentre bluetoothd[5630]: bridge pan0 created
Feb  6 14:22:01 mediacentre kernel: [   54.245234] Bluetooth: RFCOMM socket layer initialized
Feb  6 14:22:01 mediacentre kernel: [   54.245802] Bluetooth: RFCOMM TTY layer initialized
Feb  6 14:22:01 mediacentre kernel: [   54.245807] Bluetooth: RFCOMM ver 1.10
Feb  6 14:22:02 mediacentre gdm[5695]: WARNING: Didn't understand `' (expected true or false) 
Feb  6 14:22:03 mediacentre acpid: client connected from 5702[0:0] 
Feb  6 14:22:04 mediacentre kernel: [   56.813950] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
Feb  6 14:22:04 mediacentre lircd-0.8.4a[5766]: lircd(devinput) ready
Feb  6 14:22:05 mediacentre /usr/sbin/cron[5809]: (CRON) INFO (pidfile fd = 3)
Feb  6 14:22:05 mediacentre /usr/sbin/cron[5810]: (CRON) STARTUP (fork ok)
Feb  6 14:22:05 mediacentre /usr/sbin/cron[5810]: (CRON) INFO (Running @reboot jobs)
Feb  6 14:22:07 mediacentre kernel: [   60.189750] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
Feb  6 14:22:07 mediacentre kernel: [   60.189780] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Feb  6 14:22:07 mediacentre kernel: [   60.189955] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode
Feb  6 14:22:07 mediacentre kernel: [   60.189970] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
Feb  6 14:22:07 mediacentre kernel: [   60.192335] [fglrx] Setup AGP aperture
Feb  6 14:22:07 mediacentre kernel: [   60.192911] [fglrx] GART Table is not in FRAME_BUFFER range 
Feb  6 14:22:07 mediacentre kernel: [   60.197640] [fglrx] Reserved FB block: Shared offset:0, size:40000 
Feb  6 14:22:21 mediacentre lircd-0.8.4a[5766]: accepted new client on /dev/lircd
Feb  6 14:22:21 mediacentre lircd-0.8.4a[5766]: initializing '/dev/lirc0'
Feb  6 14:22:21 mediacentre lircd-0.8.4a[5766]: unable to open '/dev/lirc0'
Feb  6 14:22:21 mediacentre lircd-0.8.4a[5766]: Failed to initialize hardware
Feb  6 14:22:37 mediacentre lircd-0.8.4a[5766]: removed client
Feb  6 14:22:37 mediacentre lircd-0.8.4a[5766]: closing '/dev/lirc0'
Feb  6 14:22:53 mediacentre lircd-0.8.4a[5766]: accepted new client on /dev/lircd
Feb  6 14:22:53 mediacentre lircd-0.8.4a[5766]: initializing '/dev/lirc0'
Feb  6 14:22:53 mediacentre lircd-0.8.4a[5766]: unable to open '/dev/lirc0'
Feb  6 14:22:53 mediacentre lircd-0.8.4a[5766]: Failed to initialize hardware
Feb  6 14:23:06 mediacentre lircd-0.8.4a[5766]: removed client
Feb  6 14:23:06 mediacentre lircd-0.8.4a[5766]: closing '/dev/lirc0'
Feb  6 14:26:12 mediacentre ntpd[4689]: synchronized to 91.189.94.4, stratum 2
Feb  6 14:26:12 mediacentre ntpd[4689]: kernel time sync status change 0001
Feb  6 14:32:35 mediacentre lircd-0.8.4a[5766]: accepted new client on /dev/lircd
Feb  6 14:32:35 mediacentre lircd-0.8.4a[5766]: initializing '/dev/lirc0'
Feb  6 14:32:35 mediacentre lircd-0.8.4a[5766]: unable to open '/dev/lirc0'
Feb  6 14:32:35 mediacentre lircd-0.8.4a[5766]: Failed to initialize hardware
Feb  6 14:33:25 mediacentre lircd-0.8.4a[5766]: removed client
Feb  6 14:33:25 mediacentre lircd-0.8.4a[5766]: closing '/dev/lirc0'

==> /var/log/Xorg.0.log <==
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device HID 062a:0001
(**) HID 062a:0001: always reports core events
(**) HID 062a:0001: Device: "/dev/input/event2"
(II) HID 062a:0001: Found x and y relative axes
(II) HID 062a:0001: Found 3 mouse buttons
(II) HID 062a:0001: Configuring as mouse
(II) XINPUT: Adding extended input device "HID 062a:0001" (type: MOUSE)
(**) HID 062a:0001: YAxisMapping: buttons 4 and 5
(**) HID 062a:0001: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

==> /home/media/.xsession-errors <==
06/02/2009 14:22:10 passing arg to libvncserver: -rfbport
06/02/2009 14:22:10 passing arg to libvncserver: 5900
06/02/2009 14:22:10 x11vnc version: 0.9.3 lastmod: 2007-09-30
06/02/2009 14:22:10 Using X display :0
06/02/2009 14:22:10 
06/02/2009 14:22:10 ------------------ USEFUL INFORMATION ------------------
06/02/2009 14:22:10 X DAMAGE available on display, using it for polling hints.
06/02/2009 14:22:10   To disable this behavior use: '-noxdamage'
06/02/2009 14:22:10 
06/02/2009 14:22:10 XFIXES available on display, resetting cursor mode
06/02/2009 14:22:10   to: '-cursor most'.
06/02/2009 14:22:10   to disable this behavior use: '-cursor arrow'
06/02/2009 14:22:10   or '-noxfixes'.
06/02/2009 14:22:10 using XFIXES for cursor drawing.
06/02/2009 14:22:10 GrabServer control via XTEST.
06/02/2009 14:22:10 
06/02/2009 14:22:10 Scroll Detection: -scrollcopyrect mode is in effect to
06/02/2009 14:22:10   use RECORD extension to try to detect scrolling windows
06/02/2009 14:22:10   (induced by either user keystroke or mouse input).
06/02/2009 14:22:10   If this yields undesired behavior (poor response, painting
06/02/2009 14:22:10   errors, etc) it may be disabled via: '-noscr'
06/02/2009 14:22:10   Also see the -help entry for tuning parameters.
06/02/2009 14:22:10   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/02/2009 14:22:10   repaint the screen, also see the -fixscreen option for
06/02/2009 14:22:10   periodic repaints.
06/02/2009 14:22:10 
06/02/2009 14:22:10 XKEYBOARD: number of keysyms per keycode 6 is greater
06/02/2009 14:22:10   than 4 and 290 keysyms are mapped above 4.
06/02/2009 14:22:10   Automatically switching to -xkb mode.
06/02/2009 14:22:10   If this makes the key mapping worse you can
06/02/2009 14:22:10   disable it with the "-noxkb" option.
06/02/2009 14:22:10   Also, remember "-remap DEAD" for accenting characters.
06/02/2009 14:22:10 X FBPM extension not supported.
06/02/2009 14:22:10 X display is capable of DPMS.
06/02/2009 14:22:10 --------------------------------------------------------
06/02/2009 14:22:10 
06/02/2009 14:22:10 Default visual ID: 0x23
06/02/2009 14:22:11 Read initial data from X display into framebuffer.
06/02/2009 14:22:11 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
06/02/2009 14:22:11 
06/02/2009 14:22:11 X display :0.0 is 32bpp depth=24 true color
06/02/2009 14:22:11 
06/02/2009 14:22:11 Listening for VNC connections on TCP port 5900
06/02/2009 14:22:11 fb read rate: 7 MB/sec
06/02/2009 14:22:11 screen setup finished.
06/02/2009 14:22:11 

The VNC desktop is:      mediacentre:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

/usr/bin/startxfce4: X server already running on display :0
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-RzdMeU5888/agent.5888

** (xfce4-session:6034): WARNING **: Unable to launch "nm-applet --sm-disable" (specified by autostart/nm-applet.desktop): Failed to execute child process "nm-applet" (No such file or directory)
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-02-06 14:22:17.879 Using runtime prefix = /usr
2009-02-06 14:22:18.100 XScreenSaver support enabled
2009-02-06 14:22:18.101 DPMS is active.
2009-02-06 14:22:18.106 Empty LocalHostName.
2009-02-06 14:22:18.107 Using localhost value of mediacentre
2009-02-06 14:22:18.139 New DB connection, total: 1
2009-02-06 14:22:18.160 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:22:18.161 Closing DB connection named 'DBManager0'
2009-02-06 14:22:18.162 Primary screen 0.
2009-02-06 14:22:18.163 Connected to database 'mythconverg' at host: localhost
2009-02-06 14:22:18.164 Using screen 0, 1024x768 at 0,0
 * Stopping MythTV server: mythbackend 
   ...done.
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x3000008
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend 
   ...done.
Select the window whose client you wish to kill with button 1....
xkill:  killing creator of resource 0x2e00008
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.1G  7.5G  29% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  348K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             116G  188M  116G   1% /var/lib
//10.1.1.2/Movies     582G  235G  317G  43% /dull/movies
//10.1.1.2/Music      582G  235G  317G  43% /dull/music
//10.1.1.2/Downloads  582G  235G  317G  43% /dull/downloads
//10.1.1.2/Backup     289G  274M  274G   1% /dull/backup
//10.1.1.2/Photos     582G  235G  317G  43% /dull/photos

==> uname -a <==
Linux mediacentre 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

==> lsusb <==
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 2040:9950 Hauppauge 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==> lshw <==
computer
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=9CC6D721-1620-DA11-BDFD-EE8FB5458163
  *-core
       description: Motherboard
       product: A8V
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0218 (10/13/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: [REMOVED]
          slot: Socket 939
          size: 1800MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 37
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci:0
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=64 module=amd64_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display:0
                description: VGA compatible controller
                product: RV350 AR [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AR [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
        *-network
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 13
             serial: [REMOVED]
             size: 1GB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=[REMOVED] latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=1GB/s
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: c.1
             bus info: pci@0000:00:0c.1
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: c.2
             bus info: pci@0000:00:0c.2
             version: 65
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-multimedia:0
             description: Multimedia audio controller
             product: SB Audigy LS
             vendor: Creative Labs
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=64 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             logical name: scsi3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: WDC WD2500PB-00F
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 15.0
                serial: [REMOVED]
                size: 127GiB (137GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8be0bf88
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: [REMOVED]
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-01 10:36:33 filesystem=ext3 modified=2009-02-06 14:19:34 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-02-06 14:13:49 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 116GiB
                   capacity: 116GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 972MiB
                      capabilities: nofs
                 *-logicalvolume:1 UNCLAIMED
                      description: Linux filesystem partition
                      physical id: 6
                      capacity: 115GiB
           *-cdrom
                description: DVD reader
                product: CD-RW  CRX300E
                vendor: SONY
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KYS1
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia:1
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication UNCLAIMED
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Thanks.

---

### Post by GCFreak on 2009-02-06
I've traced the MythVideo problem down to my 9600XT being faulty. Well, that sucks. I've got another video card here somewhere to put in though.

---

### Post by GCFreak on 2009-02-08
Now that I come to think of it, I tried to watch channels in other players, such as Totem and xine, and scanning channels with w_scan, and none of them worked... so this might be a driver/operating system problem? I'd REALLY like to get this working, because we might have to switch back to Windows for this, and I really don't want to do that.

Thanks for your help so far.

---

### Post by tgm4883 on 2009-02-08
Unfortunatly I don't know much about the nova-T, is there any firmware you need to load for it?

---

### Post by GCFreak on 2009-02-14
[This tutorial](http://wiki.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Installing) had two firmwares to install, I used the later one since I actually had it going before with another machine.

---

### Post by Wednesday on 2009-09-14
Hi, Did you fix your problem? I have the same problem I have installed a new NOVA TD-500 card and followed the instructions on the page:
[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI)

but I still find the logs saying that it cannot find the card: "no valid capture cards are defined in the database"

Here is my log. It looks like your log.

Have you any suggestions?

mythbackend.log

2009-09-14 11:03:52.762 Using runtime prefix = /usr
2009-09-14 11:03:52.813 Empty LocalHostName.
2009-09-14 11:03:52.827 Using localhost value of Dell-desktop
2009-09-14 11:03:52.949 New DB connection, total: 1
2009-09-14 11:03:52.977 Connected to database 'mythconverg' at host: localhost
2009-09-14 11:03:53.013 Closing DB connection named 'DBManager0'
2009-09-14 11:03:53.036 Connected to database 'mythconverg' at host: localhost
2009-09-14 11:03:53.038 New DB connection, total: 2
2009-09-14 11:03:53.041 Connected to database 'mythconverg' at host: localhost
2009-09-14 11:03:53.067 Current Schema Version: 1214
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-09-14 11:03:53.121 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-09-14 11:03:53.122 Main::Registering HttpStatus Extension
2009-09-14 11:03:53.123 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-09-14 11:03:53.124 Enabled verbose msgs:  important general
2009-09-14 11:03:53.148 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

