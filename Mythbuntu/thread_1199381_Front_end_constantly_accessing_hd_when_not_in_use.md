---
title: "Front end constantly accessing hd when not in use"
date: 2009-06-28
forum: Mythbuntu
---

### Post by mark467 on 2009-06-28
I am having trouble with Front end constantly accessing hd when not in use. anyone point me in the right direction as to where to look?

---

### Post by mark467 on 2009-06-28
Forgot the logs

==> /var/log/mythtv/mythbackend.log <==
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 22:29:53.358 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 22:29:53.409 Cannot login to database?
2009-06-28 22:29:53.410 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [RFLD9XCK]  
[console is not interactive, using default 'RFLD9XCK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-06-28 22:29:53.587 Unable to connect to database!
2009-06-28 22:29:53.594 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 22:29:53.662 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 22:29:53.713 Cannot login to database?
2009-06-28 22:29:53.714 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [RFLD9XCK]  
[console is not interactive, using default 'RFLD9XCK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-06-28 22:29:53.899 Unable to connect to database!
2009-06-28 22:29:53.907 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 22:29:53.974 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 22:29:54.025 Cannot login to database?
2009-06-28 22:29:54.026 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [RFLD9XCK]  
[console is not interactive, using default 'RFLD9XCK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-06-28 22:29:54.203 Unable to connect to database!

==> /var/log/mythtv/mythfrontend.log <==
2009-06-28 12:11:30.890 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.25' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 12:11:30.940 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 12:11:30.991 Database not open while trying to load setting: PopupHeightPadding
2009-06-28 12:11:30.991 Unable to connect to database!
2009-06-28 12:11:30.991 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.25' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 12:11:31.042 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 12:11:31.093 Database not open while trying to load setting: PopupWidthPadding
2009-06-28 12:11:31.992 Unable to connect to database!
2009-06-28 12:11:31.992 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.25' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 12:11:32.043 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 12:11:32.093 Database not open while trying to load setting: OverrideExitMenu
2009-06-28 12:11:34.818 Unable to connect to database!
2009-06-28 12:11:34.818 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.25' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 12:11:34.869 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 12:11:34.919 Database not open while trying to save setting: PlayMode
2009-06-28 12:11:34.920 Unable to connect to database!
2009-06-28 12:11:34.920 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.25' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 12:11:34.971 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 12:11:35.021 Database not open while trying to save setting: RepeatMode
2009-06-28 12:11:35.022 Unable to connect to database!
2009-06-28 12:11:35.022 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.25' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 12:11:35.073 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 12:11:35.123 Database not open while trying to save setting: MusicAutoShowPlayer
2009-06-28 12:11:35.187 Deleting UPnP client...
Starting mythfrontend.real..
2009-06-28 22:23:43.260 New DB connection, total: 2
2009-06-28 22:23:43.262 Connected to database 'mythconverg' at host: 192.168.1.25
2009-06-28 22:23:43.268 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-06-28 22:23:43.268 Enabled verbose msgs:  important general
2009-06-28 22:23:44.828 No theme dir: /home/mark467/.mythtv/themes/G.A.N.T
2009-06-28 22:23:44.830 Primary screen 0.
2009-06-28 22:23:44.831 Using screen 0, 1024x768 at 0,0
2009-06-28 22:23:44.832 No theme dir: /home/mark467/.mythtv/themes/G.A.N.T
2009-06-28 22:23:44.833 Switching to square mode (G.A.N.T)
2009-06-28 22:23:44.873 Using the Qt painter
2009-06-28 22:23:44.873 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark467/.mythtv/joystickmenurc
2009-06-28 22:23:44.875 lirc init success using configuration file: /home/mark467/.mythtv/lircrc
2009-06-28 22:23:45.613 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-06-28 22:23:45.693 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-06-28 22:23:45.925 Registering Internal as a media playback plugin.
2009-06-28 22:23:46.052 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-06-28 22:23:46.402 Failed to run 'cdrecord --scanbus'
2009-06-28 22:23:46.407 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-06-28 22:23:46.413 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-06-28 22:23:46.491 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-06-28 22:23:46.786 No theme dir: /home/mark467/.mythtv/themes/G.A.N.T

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Jun 28 22:23:28 mb9fe ntpd[4591]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Jun 28 22:23:28 mb9fe ntpd[4591]: kernel time sync status 0040
Jun 28 22:23:28 mb9fe ntpd[4591]: frequency initialized -159.602 PPM from /var/lib/ntp/ntp.drift
Jun 28 22:23:29 mb9fe acpid: client connected from 4759[112:120] 
Jun 28 22:23:30 mb9fe ntpd_initres[4593]: host name not found: ntp.ubuntu.com
Jun 28 22:23:30 mb9fe ntpd_initres[4593]: couldn't resolve `ntp.ubuntu.com', giving up on it
Jun 28 22:23:31 mb9fe bluetoothd[4786]: Bluetooth daemon
Jun 28 22:23:31 mb9fe bluetoothd[4786]: Starting SDP server
Jun 28 22:23:31 mb9fe kernel: [  109.676976] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 28 22:23:31 mb9fe kernel: [  109.676980] Bluetooth: BNEP filters: protocol multicast
Jun 28 22:23:31 mb9fe bluetoothd[4786]: bridge pan0 created
Jun 28 22:23:31 mb9fe kernel: [  109.705587] Bridge firewalling registered
Jun 28 22:23:31 mb9fe bluetoothd[4786]: Registered interface org.bluez.Service on path /org/bluez/4786/any
Jun 28 22:23:31 mb9fe bluetoothd[4786]: Starting experimental netlink support
Jun 28 22:23:31 mb9fe bluetoothd[4786]: Failed to find Bluetooth netlink family
Jun 28 22:23:32 mb9fe gdm[4821]: WARNING: Didn't understand `' (expected true or false) 
Jun 28 22:23:32 mb9fe NetworkManager: <info>  starting... 
Jun 28 22:23:32 mb9fe NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169') 
Jun 28 22:23:32 mb9fe NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_c0_ba_12_8d 
Jun 28 22:23:32 mb9fe NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Jun 28 22:23:32 mb9fe NetworkManager: <info>  Trying to start the supplicant... 
Jun 28 22:23:32 mb9fe NetworkManager: <info>  Trying to start the system settings daemon... 
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPlugin-Ifupdown: init!
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_c0_ba_12_8d, iface: eth0): not well known
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jun 28 22:23:32 mb9fe nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 28 22:23:32 mb9fe nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPlugin-Ifupdown: (139958016) ... get_connections.
Jun 28 22:23:32 mb9fe nm-system-settings:    SCPlugin-Ifupdown: (139958016) ... get_connections (managed=false): return empty list.
Jun 28 22:23:32 mb9fe nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jun 28 22:23:32 mb9fe acpid: client connected from 4833[0:0] 
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Found user 'avahi' (UID 110) and group 'avahi' (GID 118).
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Successfully dropped root privileges.
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: avahi-daemon 0.6.23 starting up.
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Successfully called chroot().
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Successfully dropped remaining capabilities.
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: No service file found in /etc/avahi/services.
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Network interface enumeration completed.
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 28 22:23:33 mb9fe avahi-daemon[4871]: Server startup complete. Host name is mb9fe.local. Local service cookie is 1911834754.
Jun 28 22:23:33 mb9fe kernel: [  111.263500] ppdev: user-space parallel port driver
Jun 28 22:23:34 mb9fe acpid: client connected from 4833[0:0] 
Jun 28 22:23:34 mb9fe /usr/sbin/cron[5006]: (CRON) INFO (pidfile fd = 3)
Jun 28 22:23:34 mb9fe /usr/sbin/cron[5007]: (CRON) STARTUP (fork ok)
Jun 28 22:23:34 mb9fe /usr/sbin/cron[5007]: (CRON) INFO (Running @reboot jobs)
Jun 28 22:23:36 mb9fe console-kit-daemon[4616]: WARNING: Couldn't read /proc/4615/environ: Failed to open file '/proc/4615/environ': No such file or directory 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): bringing up device. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): preparing device. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jun 28 22:23:37 mb9fe kernel: [  114.931778] r8169: eth0: link up
Jun 28 22:23:37 mb9fe kernel: [  114.931787] r8169: eth0: link up
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jun 28 22:23:37 mb9fe NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jun 28 22:23:37 mb9fe avahi-daemon[4871]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.26.
Jun 28 22:23:37 mb9fe avahi-daemon[4871]: New relevant interface eth0.IPv4 for mDNS.
Jun 28 22:23:37 mb9fe avahi-daemon[4871]: Registering new address record for 192.168.1.26 on eth0.IPv4.
Jun 28 22:23:38 mb9fe NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Jun 28 22:23:38 mb9fe NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Jun 28 22:23:38 mb9fe NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jun 28 22:23:38 mb9fe NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 28 22:23:38 mb9fe avahi-daemon[4871]: Registering new address record for fe80::21c:c0ff:feba:128d on eth0.*.
Jun 28 22:23:39 mb9fe ntpd[4591]: ntpd exiting on signal 15
Jun 28 22:23:40 mb9fe ntpdate[5327]: adjust time server 91.189.94.4 offset 0.297888 sec
Jun 28 22:23:40 mb9fe ntpd[5366]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Jun 28 22:23:40 mb9fe ntpd[5367]: precision = 1.000 usec
Jun 28 22:23:40 mb9fe ntpd[5367]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jun 28 22:23:40 mb9fe ntpd[5367]: Listening on interface #1 wildcard, ::#123 Disabled
Jun 28 22:23:40 mb9fe ntpd[5367]: Listening on interface #2 lo, ::1#123 Enabled
Jun 28 22:23:40 mb9fe ntpd[5367]: Listening on interface #3 eth0, fe80::21c:c0ff:feba:128d#123 Enabled
Jun 28 22:23:40 mb9fe ntpd[5367]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jun 28 22:23:40 mb9fe ntpd[5367]: Listening on interface #5 eth0, 192.168.1.26#123 Enabled
Jun 28 22:23:40 mb9fe ntpd[5367]: kernel time sync status 0040
Jun 28 22:23:40 mb9fe ntpd[5367]: frequency initialized -159.602 PPM from /var/lib/ntp/ntp.drift
Jun 28 22:23:44 mb9fe lircd-0.8.4a[1509]: accepted new client on /dev/lircd
Jun 28 22:23:47 mb9fe kernel: [  125.260051] eth0: no IPv6 routers present
Jun 28 22:28:01 mb9fe ntpd[5367]: synchronized to 91.189.94.4, stratum 2
Jun 28 22:28:01 mb9fe ntpd[5367]: time reset +0.225678 s
Jun 28 22:28:01 mb9fe ntpd[5367]: kernel time sync status change 0001

==> /var/log/Xorg.0.log <==
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.98.12.00.51
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: TV-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device PATEN USB Receiver
(**) PATEN USB Receiver: always reports core events
(**) PATEN USB Receiver: Device: "/dev/input/event6"
(II) PATEN USB Receiver: Found 3 mouse buttons
(II) PATEN USB Receiver: Found x and y relative axes
(II) PATEN USB Receiver: Configuring as mouse
(**) PATEN USB Receiver: YAxisMapping: buttons 4 and 5
(**) PATEN USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PATEN USB Receiver" (type: MOUSE)
(**) PATEN USB Receiver: (accel) keeping acceleration scheme 1
(**) PATEN USB Receiver: (accel) filter chain progression: 2.00
(**) PATEN USB Receiver: (accel) filter stage 0: 20.00 ms
(**) PATEN USB Receiver: (accel) set acceleration profile 0

==> /home/mark467/.xsession-errors <==
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 22:23:51.189 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 22:23:51.239 Cannot login to database?
2009-06-28 22:23:51.239 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [RFLD9XCK]  
[console is not interactive, using default 'RFLD9XCK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-06-28 22:23:51.240 Unable to connect to database!
2009-06-28 22:23:51.240 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 22:23:51.291 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 22:23:51.341 Cannot login to database?
2009-06-28 22:23:51.341 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [RFLD9XCK]  
[console is not interactive, using default 'RFLD9XCK']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-06-28 22:23:51.342 Unable to connect to database!
2009-06-28 22:23:51.342 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-28 22:23:51.392 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-06-28 22:23:51.443 Cannot login to database?
2009-06-28 22:23:51.443 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [RFLD9XCK]  
[console is not interactive, using default 'RFLD9XCK']

...Too much output, ignoring rest...

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.2G  7.3G  31% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
varrun               1006M  344K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M  144K 1006M   1% /dev
tmpfs                1006M     0 1006M   0% /dev/shm
lrm                  1006M  2.2M 1004M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6             920G  206M  920G   1% /var/lib
192.168.1.25:/var/lib/mythtv/videos
                      1.4T  1.3T   79G  95% /var/lib/mythtv/videos
192.168.1.25:/var/lib/mythtv/pictures
                      1.4T  1.3T   79G  95% /var/lib/mythtv/pictures
192.168.1.25:/var/lib/mythtv/posters
                      1.4T  1.3T   79G  95% /var/lib/mythtv/posters
192.168.1.25:/var/lib/mythtv/music
                      1.4T  1.3T   79G  95% /var/lib/mythtv/music

==> uname -a <==
Linux mb9fe 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1020:000a Labtec Wireless Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2304:0225 Pinnacle Systems, Inc. [hex] 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce 8400 GS
IRQ:   		 16
Video BIOS: 	 62.98.12.00.51
Card Type: 	 PCI-E
DMA Size: 	 40 bits
DMA Mask: 	 0xffffffffff
Bus Location: 	 01.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2010MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU        E1200  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8400 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=[REMOVED] latency=0 module=r8169 multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW SH-S182D
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Mister.Vash on 2009-06-30
All those
"QSqlQuery::exec: database not open
QSqlQuery::exec: database not open"
messages from the logs are a little worrying - are you even able to connect and watch tv or recorded programs?

I found this link, [http://www.bramkortleven.be/?p=131](http://www.bramkortleven.be/?p=131) , which may help.  It recommends the deletions of superfluous mysql.txt files from system.

Since we can't rule those errors out as a cause, it might be best to sort that out first to make sure it isn't related.

---

### Post by mark467 on 2009-06-30
Yes I can that is what is odd. I can watch recordings, videos, and music. It does lock up and needs a hard reboot at times. The backend also looses the database connection at times (seems to happen when the remote front end locks) I will check that post.

---

### Post by borm on 2009-08-31
> **Mister.Vash said:**
> All those
"QSqlQuery::exec: database not open
QSqlQuery::exec: database not open"
messages from the logs are a little worrying - are you even able to connect and watch tv or recorded programs?

I found this link, [http://www.bramkortleven.be/?p=131](http://www.bramkortleven.be/?p=131) , which may help.  It recommends the deletions of superfluous mysql.txt files from system.

Since we can't rule those errors out as a cause, it might be best to sort that out first to make sure it isn't related.


I have this same problem on my frontend.  I installed Mythbuntu 9.04 as just a frontend.  It connects to my primary backend and operates (more or less) correctly.  

The problem seems to be that the install process also installed a secondary backend on my frontend machine.  I did not ask to have the secondary backend installed.  The error messages are generated when the secondary backend tries to connect to a local mysql database using the remote database's password.

I have a number of issues with this:


[LIST]
[*] I don't know if this secondary backend is necessary for some functionality that I simply haven't discovered yet.
[*]If it is necessary, I don't know how it is supposed to be configured.  Currently it is neither used by a frontend nor is it affiliated with a primary backend.
[*]When I uninstalled the secondary backend (through the mythbuntu control panel), the automatic login behavior changed.  After uninstalling the backend, the system does a 30 second timed login.  I don't see why these two things would be related.  I spent several hours trying to diagnose the auto-login problem before simply reinstalling.
[/LIST]
 
Does this additional information help uncover the problem?

Thanks...Eric

---

### Post by borm on 2009-09-03
Fixed:  I fixed the problems mentioned above, and wanted to relay the solutions. 

Regarding mythbuntu and the secondary backend: It does not appear to be necessary for anything on my frontend machine.  Therefore, the right move seems to be disabling the secondary backend.  Doing so does not disable the mysql server that is also running but not required.  For that, I simply disabled the 3 (?) mysql service processes.

The autologin problem seems to be happening to a number of people.  A brief discussions is posted here: [http://ubuntuforums.org/showthread.php?p=7891394#post7891394](http://ubuntuforums.org/showthread.php?p=7891394#post7891394).  It links to a longer discussion as well.

FWIW, I also had trouble getting samba to mount my remote directories of recorded shows and videos.  I was mounting them in fstab, and it was adding 90 seconds to the boot time.  To fix this, I removed them from fstab and mounted them from rc.local using smbmount.  It works great.

  --Eric

---

### Post by williammanda on 2009-09-06
One other way to remove the secondary backend is to use mythbuntu control center. You can deselect the backend and it will be removed.
Thanks

---

