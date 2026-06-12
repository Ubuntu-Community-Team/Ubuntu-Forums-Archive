---
title: "frontend/backend freeze"
date: 2010-03-14
forum: Mythbuntu
---

### Post by bnhrobotics on 2010-03-14
Hi, I am new to mythbuntu. I installed mythbuntu once just to play around with it. Things worked out fine for the most part, but I went back to reinstall and now the frontend freezes upon boot, or if run manually. The backend setup will also freeze if I try to run it. I have no idea what the problem is. I repeated the install twice more and checked the DVD for errors. I don't understand why it would have worked the first time, but freezes all the rest. Any tips would be appreciated. Thanks

---

### Post by bnhrobotics on 2010-03-15
Here are the error logs. Maybe that will help.

```

==> /var/log/mythtv/mtd.log <==
mtd started at Tue Jan 22 02:25:01 2002
mtd is running on a host called bryan-mythbuntu
02:25:01: Waiting for connections/jobs
02:25:01: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2002-01-22 02:24:47.823 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2002-01-22 02:24:48.015 Using runtime prefix = /usr
2002-01-22 02:24:48.242 Using configuration directory = /home/mythtv/.mythtv
2002-01-22 02:24:48.410 Empty LocalHostName.
2002-01-22 02:24:48.600 Using localhost value of bryan-mythbuntu
2002-01-22 02:24:49.115 New DB connection, total: 1
2002-01-22 02:24:49.252 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:24:49.469 Closing DB connection named 'DBManager0'
2002-01-22 02:24:49.682 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:01.427 Current MythTV Schema Version (DBSchemaVer): 1244
2002-01-22 02:25:02.791 MythBackend: Starting up as the master server.
2002-01-22 02:25:03.886 New DB connection, total: 2
2002-01-22 02:25:04.177 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:04.458 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2002-01-22 02:25:05.325 New DB connection, total: 3
2002-01-22 02:25:05.639 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:08.367 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2002-01-22 02:25:08.543 Main::Registering HttpStatus Extension
2002-01-22 02:25:08.812 Enabled verbose msgs:  important general
2002-01-22 02:25:11.384 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2002-01-22 02:26:25.311 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2002-01-22 02:41:26.938 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
Starting mythfrontend.real..
2002-01-22 02:24:58.414 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2002-01-22 02:24:58.415 Using runtime prefix = /usr
2002-01-22 02:24:58.415 Using configuration directory = /home/bryan/.mythtv
2002-01-22 02:24:58.866 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2002-01-22 02:24:58.873 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2002-01-22 02:24:58.876 Empty LocalHostName.
2002-01-22 02:24:58.876 Using localhost value of bryan-mythbuntu
2002-01-22 02:24:58.953 New DB connection, total: 1
2002-01-22 02:24:58.959 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:24:58.961 Closing DB connection named 'DBManager0'
2002-01-22 02:24:59.073 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2002-01-22 02:24:59.412 ScreenSaverX11Private: Gnome screen saver support enabled
2002-01-22 02:24:59.414 DPMS is active.
2002-01-22 02:24:59.699 Primary screen: 0.
2002-01-22 02:24:59.701 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:01.403 Using screen 0, 1920x1080 at 0,0
2002-01-22 02:25:01.504 MythUI Image Cache size set to 20971520 bytes
2002-01-22 02:25:01.505 Enabled verbose msgs:  important general
2002-01-22 02:25:02.183 Primary screen: 0.
2002-01-22 02:25:02.790 Using screen 0, 1920x1080 at 0,0
2002-01-22 02:25:03.279 Using theme base resolution of 1280x720
2002-01-22 02:25:03.894 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2002-01-22 02:25:03.894 JoystickMenuThread Error: Joystick disabled - Failed to read /home/bryan/.mythtv/joystickmenurc
2002-01-22 02:25:08.919 Using the Qt painter
2002-01-22 02:25:09.723 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2002-01-22 02:25:09.964 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2002-01-22 02:25:10.027 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2002-01-22 02:25:10.028 Unable to load window 'backgroundwindow' from base
2002-01-22 02:25:10.080 Current MythTV Schema Version (DBSchemaVer): 1244
2002-01-22 02:25:10.223 New DB connection, total: 2
2002-01-22 02:25:10.224 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:18.298 Desktop video mode: 1920x1080 60.0024 Hz
2002-01-22 02:25:18.846 Writing settings file /home/bryan/.mythtv/mysql.txt
2002-01-22 02:25:18.847 Closing DB connection named 'DBManager0'
2002-01-22 02:25:18.847 Closing DB connection named 'DBManager1'
2002-01-22 02:25:18.862 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:18.864 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:25:19.348 Registering Internal as a media playback plugin.
2002-01-22 02:25:19.810 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2002-01-22 02:25:19.816 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2002-01-22 02:25:19.851 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2002-01-22 02:25:19.857 MonitorRegisterExtensions(0x100, gif,jpg,png)
2002-01-22 02:25:20.621 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2002-01-22 02:25:20.860 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2002-01-22 02:25:21.017 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2002-01-22 02:25:21.318 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2002-01-22 02:25:21.499 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2002-01-22 02:25:21.503 Found mainmenu.xml for theme 'Mythbuntu'
ICE default IO error handler doing an exit(), pid = 1577, errno = 32

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.channelgroupnames                      OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.channelscan                            OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.channelscan_channel                    OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.channelscan_dtv_multiplex              OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.codecparams                            OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.credits                                OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.customexample                          OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.diseqc_config                          OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.diseqc_tree                            OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.displayprofilegroups                   OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.displayprofiles                        OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.dtv_multiplex                          OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.dtv_privatetypes                       OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.dvdbookmark                            OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.dvdinput                               OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.dvdtranscode                           OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.eit_cache                              OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.filemarkup                             OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.gallerymetadata                        OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.gamemetadata                           OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.gameplayers                            OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.housekeeping                           OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.inputgroup                             OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.inuseprograms                          OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.jobqueue                               OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.jumppoints                             OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.keybindings                            OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.keyword                                OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.movies_movies                          OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.movies_showtimes                       OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.movies_theaters                        OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_albumart                         OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_albums                           OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_artists                          OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_directories                      OK
Jan 22 02:24:46 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_genres                           OK
Jan 22 02:24:50 bryan-mythbuntu ntpd[1525]: ntpd 4.2.4p6@1.1549-o Thu Oct 22 21:58:37 UTC 2009 (1)
Jan 22 02:24:50 bryan-mythbuntu ntpd[1528]: precision = 1.000 usec
Jan 22 02:24:50 bryan-mythbuntu ntpd[1528]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jan 22 02:24:50 bryan-mythbuntu ntpd[1528]: Listening on interface #1 wildcard, ::#123 Disabled
Jan 22 02:24:50 bryan-mythbuntu ntpd[1528]: Listening on interface #2 lo, ::1#123 Enabled
Jan 22 02:24:50 bryan-mythbuntu ntpd[1528]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Jan 22 02:24:50 bryan-mythbuntu ntpd[1528]: kernel time sync status 2040
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_playlists                        OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_smartplaylist_categories         OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_smartplaylist_items              OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_smartplaylists                   OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_songs                            OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.music_stats                            OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.mythlog                                OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.networkiconmap                         OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.oldfind                                OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.oldprogram                             OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.oldrecorded                            OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.people                                 OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.phonecallhistory                       OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.phonedirectory                         OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.pidcache                               OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.playgroup                              OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.powerpriority                          OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.profilegroups                          OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.program                                OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.programgenres                          OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.programrating                          OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recgrouppassword                       OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.record                                 OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recorded                               OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordedcredits                        OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordedfile                           OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordedmarkup                         OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordedprogram                        OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordedrating                         OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordedseek                           OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordingprofiles                      OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.recordmatch                            OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.romdb                                  OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.schemalock                             OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.settings                               OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.storagegroup                           OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.tvchain                                OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.tvosdmenu                              OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.upnpmedia                              OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videocast                              OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videocategory                          OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videocountry                           OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videogenre                             OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videometadata                          OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videometadatacast                      OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videometadatacountry                   OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videometadatagenre                     OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videosource                            OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.videotypes                             OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.weatherdatalayout                      OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.weatherscreens                         OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: mythconverg.weathersourcesettings                  OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: Running 'mysql_fix_privilege_tables'...
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1362]: OK
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1763]: Checking for insecure root accounts.
Jan 22 02:25:17 bryan-mythbuntu /etc/mysql/debian-start[1767]: Triggering myisam-recover for all MyISAM tables
Jan 22 02:39:01 bryan-mythbuntu CRON[1943]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

==> /var/log/Xorg.0.log <==
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
(II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
(II) NVIDIA(0):     configuration option may not be set correctly.  When the
(II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
(II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
(II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
(II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(0):     Config Options in the README.
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
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 9 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.

==> /home/bryan/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2002-01-22 02:24:47.870 Using runtime prefix = /usr
2002-01-22 02:24:47.870 Using configuration directory = /home/bryan/.mythtv
/usr/bin/startxfce4: X server already running on display :0
2002-01-22 02:24:47.996 Empty LocalHostName.
2002-01-22 02:24:47.996 Using localhost value of bryan-mythbuntu
2002-01-22 02:24:48.874 New DB connection, total: 1
2002-01-22 02:24:48.942 Connected to database 'mythconverg' at host: localhost
2002-01-22 02:24:48.942 Closing DB connection named 'DBManager0'
2002-01-22 02:24:48.943 Connected to database 'mythconverg' at host: localhost

** (gnome-screensaver:1494): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[1559]: starting up
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(polkit-gnome-authentication-agent-1:1629): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1629): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
xfce4-settings-helper is already running
2002-01-22 02:24:58.227 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org

MCS->Xfconf settings migration complete

2002-01-22 02:25:01.428 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028

(xfce4-session:1498): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(xfce4-session:1498): GLib-GObject-CRITICAL **: g_object_steal_data: assertion `G_IS_OBJECT (object)' failed

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  1.7G   66G   3% /
udev                  375M  244K  375M   1% /dev
none                  375M     0  375M   0% /dev/shm
none                  375M  276K  375M   1% /var/run
none                  375M     0  375M   0% /var/lock
none                  375M     0  375M   0% /lib/init/rw

==> uname -a <==
Linux bryan-mythbuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/patches <==

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
RmNvclkIdleGraphics: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
GCC version:  gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce 8400 GS
IRQ:   		 21
Video BIOS: 	 62.98.29.00.51
Card Type: 	 PCI-E
DMA Size: 	 40 bits
DMA Mask: 	 0xffffffffff
Bus Location: 	 02.00.0

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
          size: 766MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.4
          size: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:cf000000-cf07ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ce800000-ce8003ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=8192) memory:c9800000-ce7fffff memory:cff00000-e7ffffff(prefetchable)
           *-pci
                description: PCI bridge
                product: PEX8112 x1 Lane PCI Express-to-PCI Bridge
                vendor: PLX Technology, Inc.
                physical id: 9
                bus info: pci@0000:01:09.0
                version: aa
                width: 64 bits
                clock: 66MHz
                capabilities: pci bus_master cap_list
                resources: memory:e7800000-e780ffff(prefetchable) ioport:b000(size=4096) memory:ca000000-ce7fffff memory:cff00000-e77fffff(prefetchable)
              *-display
                   description: VGA compatible controller
                   product: G98 [GeForce 8400 GS]
                   vendor: nVidia Corporation
                   physical id: 0
                   bus info: pci@0000:02:00.0
                   version: a1
                   width: 64 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list rom
                   configuration: driver=nvidia latency=0
                   resources: irq:21 memory:cd000000-cdffffff memory:d0000000-dfffffff(prefetchable) memory:ca000000-cbffffff ioport:b800(size=128) memory:cffe0000-cfffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@0000:01:0d.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:17 ioport:a800(size=256) memory:c9800000-c98000ff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8400(size=16) memory:c9000000-c90003ff
           *-cdrom
                description: DVD reader
                product: DVD-ROM GDR8162B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0015
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e800(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e100(size=64) memory:30000000-300001ff memory:30000200-300002ff

```

---

