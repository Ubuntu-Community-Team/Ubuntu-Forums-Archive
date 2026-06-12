---
title: "Mythtv front and backend gone to a better place ??"
date: 2010-03-22
forum: Mythbuntu
---

### Post by blkbx on 2010-03-22
I was configuring my mythbuntu box yesterday when after I closed down the front and backends mythtv was gone. I mean the front and backend are gone. I downloaded the new dvb firmware and nvidia graphics driver, installed mplayer via apt-get, messed with the music and video setups but nothing to complicated. A reboot hot and cold did't help. The pc just goes striaght to the desktop now. Here's the log file.


==> /var/log/mythtv/jamu.log <==

==> /var/log/mythtv/mtd.log <==
mtd started at Mon Mar 22 18:04:39 2010
mtd is running on a host called Mythtv
18:04:39: Waiting for connections/jobs
18:04:39: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2010-03-22 18:45:31.228 New DB connection, total: 3
2010-03-22 18:45:31.266 Connected to database 'mythconverg' at host: localhost
2010-03-22 18:45:31.312 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-03-22 18:45:31.355 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-22 18:45:31.399 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
2010-03-22 18:45:31.637 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '2'.
2010-03-22 18:45:31.678 DVBChan(2:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-22 18:45:31.722 ChannelBase(2) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
2010-03-22 18:45:31.777 New DB scheduler connection
2010-03-22 18:45:31.823 Connected to database 'mythconverg' at host: localhost
2010-03-22 18:45:31.878 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-22 18:45:31.923 Main::Registering HttpStatus Extension
2010-03-22 18:45:31.967 Enabled verbose msgs:  important general
2010-03-22 18:45:32.024 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 18:45:33.131 MainServer::ANN Monitor
2010-03-22 18:45:33.181 adding: Mythtv as a client (events: 0)
2010-03-22 18:45:33.237 MainServer::ANN Monitor
2010-03-22 18:45:33.292 adding: Mythtv as a client (events: 1)
2010-03-22 18:45:34.872 Reschedule requested for id -1.
2010-03-22 18:45:34.998 Scheduled 0 items in 0.1 = 0.06 match + 0.07 place
2010-03-22 18:45:35.063 Seem to be woken up by USER
2010-03-22 18:45:47.700 MainServer::ANN Monitor
2010-03-22 18:45:47.762 adding: Mythtv as a client (events: 0)
2010-03-22 18:45:47.818 MainServer::ANN Monitor
2010-03-22 18:45:47.867 adding: Mythtv as a client (events: 1)
2010-03-22 18:46:51.871 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 19:01:51.954 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 19:16:52.560 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 19:17:01.851 MainServer::ANN Monitor
2010-03-22 19:17:01.927 adding: Mythtv as a client (events: 0)
2010-03-22 19:31:53.043 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 19:46:59.757 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-03-22 19:46:59.843 Using runtime prefix = /usr
2010-03-22 19:46:59.887 Using configuration directory = /home/mythtv/.mythtv
2010-03-22 19:46:59.951 Empty LocalHostName.
2010-03-22 19:46:59.988 Using localhost value of Mythtv
2010-03-22 19:47:00.050 New DB connection, total: 1
2010-03-22 19:47:00.091 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:47:00.133 Closing DB connection named 'DBManager0'
2010-03-22 19:47:00.177 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:47:00.224 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-22 19:47:00.267 MythBackend: Starting up as the master server.
2010-03-22 19:47:00.313 New DB connection, total: 2
2010-03-22 19:47:00.356 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:47:00.541 New DB connection, total: 3
2010-03-22 19:47:00.578 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:47:00.625 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-03-22 19:47:00.670 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-22 19:47:00.712 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
2010-03-22 19:47:00.972 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '2'.
2010-03-22 19:47:01.034 DVBChan(2:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-22 19:47:01.101 ChannelBase(2) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
2010-03-22 19:47:01.158 New DB scheduler connection
2010-03-22 19:47:01.213 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:47:01.294 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-22 19:47:01.335 Main::Registering HttpStatus Extension
2010-03-22 19:47:01.413 Enabled verbose msgs:  important general
2010-03-22 19:47:01.470 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 19:47:04.283 Reschedule requested for id -1.
2010-03-22 19:47:04.448 Scheduled 0 items in 0.2 = 0.07 match + 0.10 place
2010-03-22 19:47:04.507 Seem to be woken up by USER
2010-03-22 19:47:08.557 MainServer::ANN Monitor
2010-03-22 19:47:08.605 adding: Mythtv as a client (events: 0)
2010-03-22 19:47:08.662 MainServer::ANN Monitor
2010-03-22 19:47:08.717 adding: Mythtv as a client (events: 1)
2010-03-22 19:47:08.773 Reschedule requested for id -1.
2010-03-22 19:47:08.923 Scheduled 0 items in 0.2 = 0.08 match + 0.07 place
2010-03-22 19:47:19.896 MainServer::ANN Monitor
2010-03-22 19:47:19.988 adding: Mythtv as a client (events: 0)
2010-03-22 19:47:20.056 MainServer::ANN Monitor
2010-03-22 19:47:20.133 adding: Mythtv as a client (events: 1)
2010-03-22 19:48:21.287 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-22 19:57:33.874 Reloading backend settings
2010-03-22 19:57:59.026 MainServer::ANN Monitor
2010-03-22 19:57:59.112 adding: Mythtv as a client (events: 0)
2010-03-22 19:57:59.168 MainServer::ANN Monitor
2010-03-22 19:57:59.224 adding: Mythtv as a client (events: 1)
2010-03-22 19:58:04.575 MainServer::ANN Playback
2010-03-22 19:58:04.646 adding: Mythtv as a client (events: 0)
2010-03-22 19:58:04.726 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-03-22 19:58:04.782 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-03-22 19:58:04.846 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2010-03-22 19:58:04.902 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
2010-03-22 19:58:04.958 TVRec(1): HW Tuner: 1->1
2010-03-22 19:58:05.016 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-03-22 19:58:05.080 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-22 19:58:05.125 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2010-03-22 19:58:05.170 TVRec(1): Changing from Watching WatchingLiveTV to None
2010-03-22 20:03:21.377 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2010-03-22 19:47:25.471 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-03-22 19:47:25.644 SortedList is Empty
2010-03-22 19:47:31.673 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-03-22 19:47:35.893 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-03-22 19:47:41.861 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/movies-ui.xml
2010-03-22 19:47:41.872 Theme error: Unknown widget type
Type: 'spacing'
Name: ''
Line: 26
2010-03-22 19:47:41.877 Movie Data Has Expired. Refreshing.
2010-03-22 19:47:41.924 MythMovies Data Grabber: Executing '/usr/bin/ignyte --zip 00000 --radius 20'
2010-03-22 19:47:43.951 Grabber Finished. Processing Data.
2010-03-22 19:47:43.951 Error parsing data from grabber: Error: tag mismatch Location Line: 1 Column 58
2010-03-22 19:47:43.953 Failed to process the grabber data!
2010-03-22 19:47:52.655 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/status-ui.xml
2010-03-22 19:48:26.362 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//optical_menu.xml
2010-03-22 19:48:35.718 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-03-22 19:48:37.823 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-22 19:48:37.871 Loading menu theme from /usr/share/mythtv/musicmenu.xml
2010-03-22 19:48:42.702 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-22 19:48:42.760 Loading menu theme from /usr/share/mythtv/music_settings.xml
2010-03-22 19:49:09.274 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-03-22 19:49:14.774 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-03-22 19:49:16.486 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-22 19:49:16.525 Loading menu theme from /usr/share/mythtv/music_settings.xml
2010-03-22 19:49:53.293 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-03-22 19:57:33.946 Received a remote 'Clear Cache' request
2010-03-22 19:57:42.925 Deleting UPnP client...
Starting mythfrontend.real..
2010-03-22 19:57:57.277 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-03-22 19:57:57.277 Using runtime prefix = /usr
2010-03-22 19:57:57.277 Using configuration directory = /home/tomas/.mythtv
2010-03-22 19:57:58.130 Empty LocalHostName.
2010-03-22 19:57:58.130 Using localhost value of Mythtv
2010-03-22 19:57:58.134 New DB connection, total: 1
2010-03-22 19:57:58.137 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:57:58.138 Closing DB connection named 'DBManager0'
2010-03-22 19:57:58.146 ScreenSaverX11Private: Gnome screen saver support enabled
2010-03-22 19:57:58.147 DPMS is active.
2010-03-22 19:57:58.148 Primary screen: 0.
2010-03-22 19:57:58.149 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:57:58.150 Using screen 0, 1280x720 at 0,0
2010-03-22 19:57:58.159 MythUI Image Cache size set to 20971520 bytes
2010-03-22 19:57:58.159 Enabled verbose msgs:  important general
2010-03-22 19:57:58.162 Primary screen: 0.
2010-03-22 19:57:58.162 Using screen 0, 1280x720 at 0,0
2010-03-22 19:57:58.163 Using theme base resolution of 1280x720
2010-03-22 19:57:58.166 LIRC: Successfully initialized '/dev/lircd' using '/home/tomas/.mythtv/lircrc' config
2010-03-22 19:57:58.166 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2010-03-22 19:57:58.222 Using the Qt painter
2010-03-22 19:57:58.276 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-03-22 19:57:58.280 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-03-22 19:57:58.285 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-03-22 19:57:58.285 Unable to load window 'backgroundwindow' from base
2010-03-22 19:57:58.293 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-22 19:57:58.421 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
2010-03-22 19:57:58.421 Desktop video mode: 0x0 0 Hz
2010-03-22 19:57:58.507 Registering Internal as a media playback plugin.
2010-03-22 19:57:58.558 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-03-22 19:57:58.561 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-03-22 19:57:58.564 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-03-22 19:57:58.565 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-03-22 19:57:58.581 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-03-22 19:57:58.602 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-03-22 19:57:58.609 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-22 19:57:58.634 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-22 19:57:58.676 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-03-22 19:57:58.677 Found mainmenu.xml for theme 'Mythbuntu'
2010-03-22 19:57:59.025 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-03-22 19:57:59.026 Using protocol version 50
2010-03-22 19:58:04.452 New DB connection, total: 2
2010-03-22 19:58:04.452 Connected to database 'mythconverg' at host: localhost
2010-03-22 19:58:04.562 TV: Attempting to change from None to Watching WatchingLiveTV
2010-03-22 19:58:04.575 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-03-22 19:58:04.575 Using protocol version 50
2010-03-22 19:58:04.702 Spawning LiveTV Recorder -- begin
2010-03-22 19:58:05.214 Spawning LiveTV Recorder -- end
2010-03-22 19:58:05.215 GetEntryAt(-1) failed.
2010-03-22 19:58:05.233 EntryToProgram(0@Thu Jan 1 12:00:00 1970) failed to get pginfo
2010-03-22 19:58:05.233 TV Error: HandleStateChange(): LiveTV not successfully started
2010-03-22 19:58:05.233 We have a RingBuffer
2010-03-22 19:58:05.283 TV Error: LiveTV not successfully started
2010-03-22 19:58:05.314 ScreenSaverX11Private: DPMS Deactivated 1
2010-03-22 19:58:05.315 ScreenSaverX11Private: DPMS Reactivated 1
2010-03-22 19:58:13.801 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2010-03-22 19:58:17.324 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-03-22 19:58:21.634 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-03-22 19:58:36.317 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-03-22 19:58:38.136 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-22 19:58:38.170 Loading menu theme from /usr/share/mythtv/musicmenu.xml
2010-03-22 19:58:45.967 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-03-22 19:58:50.637 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-03-22 20:02:18.068 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-03-22 20:02:21.425 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-03-22 20:02:26.477 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-03-22 20:02:26.646 SortedList is Empty
2010-03-22 20:02:33.442 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Mar 23 14:35:54 Mythtv NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 23 14:35:54 Mythtv NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 23 14:35:54 Mythtv NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Belkin54g' has security, and secrets exist.  No new secrets needed.
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Config: added 'ssid' value 'Belkin54g'
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar 23 14:35:54 Mythtv NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 23 14:35:54 Mythtv NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 23 14:35:54 Mythtv NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 23 14:35:54 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Mar 23 14:35:57 Mythtv wpa_supplicant[1646]: CTRL-EVENT-SCAN-RESULTS 
Mar 23 14:35:57 Mythtv wpa_supplicant[1646]: Trying to associate with 00:17:3f:09:02:e8 (SSID='Belkin54g' freq=2462 MHz)
Mar 23 14:35:57 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 23 14:35:57 Mythtv wpa_supplicant[1646]: Association request to the driver failed
Mar 23 14:35:57 Mythtv kernel: [ 5457.285470] wlan0: authenticate with AP 00:17:3f:09:02:e8
Mar 23 14:35:57 Mythtv kernel: [ 5457.288151] wlan0: authenticated
Mar 23 14:35:57 Mythtv kernel: [ 5457.288153] wlan0: associate with AP 00:17:3f:09:02:e8
Mar 23 14:35:57 Mythtv kernel: [ 5457.290970] wlan0: RX AssocResp from 00:17:3f:09:02:e8 (capab=0x471 status=0 aid=1)
Mar 23 14:35:57 Mythtv kernel: [ 5457.290972] wlan0: associated
Mar 23 14:35:57 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Mar 23 14:35:57 Mythtv wpa_supplicant[1646]: Associated with 00:17:3f:09:02:e8
Mar 23 14:35:57 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Mar 23 14:35:57 Mythtv kernel: [ 5457.316305] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 23 14:36:02 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Mar 23 14:36:02 Mythtv kernel: [ 5462.457709] padlock: VIA PadLock not detected.
Mar 23 14:36:02 Mythtv wpa_supplicant[1646]: WPA: Key negotiation completed with 00:17:3f:09:02:e8 [PTK=CCMP GTK=CCMP]
Mar 23 14:36:02 Mythtv wpa_supplicant[1646]: CTRL-EVENT-CONNECTED - Connection to 00:17:3f:09:02:e8 completed (auth) [id=0 id_str=]
Mar 23 14:36:02 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Mar 23 14:36:02 Mythtv NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Belkin54g'.
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 23 14:36:02 Mythtv NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 23 14:36:02 Mythtv NetworkManager: <info>  dhclient started with pid 2533
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 23 14:36:02 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 23 14:36:02 Mythtv dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 23 14:36:02 Mythtv dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 23 14:36:02 Mythtv dhclient: All rights reserved.
Mar 23 14:36:02 Mythtv dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 23 14:36:02 Mythtv dhclient: 
Mar 23 14:36:02 Mythtv NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Mar 23 14:36:02 Mythtv dhclient: Listening on LPF/wlan0/00:1b:2f:37:31:73
Mar 23 14:36:02 Mythtv dhclient: Sending on   LPF/wlan0/00:1b:2f:37:31:73
Mar 23 14:36:02 Mythtv dhclient: Sending on   Socket/fallback
Mar 23 14:36:04 Mythtv dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 23 14:36:04 Mythtv dhclient: DHCPOFFER of 192.168.2.6 from 192.168.2.1
Mar 23 14:36:04 Mythtv dhclient: DHCPREQUEST of 192.168.2.6 on wlan0 to 255.255.255.255 port 67
Mar 23 14:36:04 Mythtv dhclient: DHCPACK of 192.168.2.6 from 192.168.2.1
Mar 23 14:36:04 Mythtv NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Mar 23 14:36:04 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 23 14:36:04 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 23 14:36:04 Mythtv NetworkManager: <info>    address 192.168.2.6
Mar 23 14:36:04 Mythtv NetworkManager: <info>    prefix 24 (255.255.255.0)
Mar 23 14:36:04 Mythtv NetworkManager: <info>    gateway 192.168.2.1
Mar 23 14:36:04 Mythtv NetworkManager: <info>    nameserver '192.168.2.1'
Mar 23 14:36:04 Mythtv NetworkManager: <info>    domain name 'Belkin'
Mar 23 14:36:04 Mythtv dhclient: bound to 192.168.2.6 -- renewal in 862 seconds.
Mar 23 14:36:04 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 23 14:36:04 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 23 14:36:04 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 23 14:36:05 Mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 23 14:36:05 Mythtv NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Mar 23 14:36:05 Mythtv NetworkManager: <info>  Activation (wlan0) successful, device activated.
Mar 23 14:36:05 Mythtv NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 23 14:36:05 Mythtv ntpd[2200]: ntpd exiting on signal 15
Mar 23 14:36:07 Mythtv ntpdate[2597]: adjust time server 91.189.94.4 offset -0.000142 sec
Mar 23 14:36:07 Mythtv ntpd[2625]: ntpd 4.2.4p6@1.1549-o Thu Oct 22 21:58:37 UTC 2009 (1)
Mar 23 14:36:07 Mythtv ntpd[2626]: precision = 1.000 usec
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #1 wildcard, ::#123 Disabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #2 lo, ::1#123 Enabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #3 wlan0, fe80::21b:2fff:fe37:3173#123 Enabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #4 eth0, fe80::226:18ff:fe03:46e8#123 Enabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #6 eth0, 192.168.2.3#123 Enabled
Mar 23 14:36:07 Mythtv ntpd[2626]: Listening on interface #7 wlan0, 192.168.2.6#123 Enabled
Mar 23 14:36:07 Mythtv ntpd[2626]: kernel time sync status 2040
Mar 23 14:36:07 Mythtv ntpd[2626]: frequency initialized -10.308 PPM from /var/lib/ntp/ntp.drift
Mar 23 14:36:08 Mythtv kernel: [ 5468.212011] wlan0: no IPv6 routers present
Mar 23 14:36:40 Mythtv wpa_supplicant[1646]: CTRL-EVENT-SCAN-RESULTS 
Mar 23 14:37:20 Mythtv wpa_supplicant[1646]: CTRL-EVENT-SCAN-RESULTS 
Mar 23 14:38:20 Mythtv wpa_supplicant[1646]: CTRL-EVENT-SCAN-RESULTS 
Mar 23 14:38:27 Mythtv dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 192.168.2.1 port 67
Mar 23 14:38:27 Mythtv dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Mar 23 14:38:27 Mythtv dhclient: bound to 192.168.2.3 -- renewal in 677 seconds.
Mar 23 14:39:01 Mythtv CRON[2649]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar 23 14:39:40 Mythtv wpa_supplicant[1646]: CTRL-EVENT-SCAN-RESULTS 

==> /var/log/Xorg.0.log <==
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Logitech Logitech BT Mini-Receiver
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event6"
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event3"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device Logitech Logitech BT Mini-Receiver
(**) Logitech Logitech BT Mini-Receiver: always reports core events
(**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event7"
(II) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
(II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
(II) Logitech Logitech BT Mini-Receiver: Found keys
(II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
(**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
(**) Logitech Logitech BT Mini-Receiver: (accel) filter chain progression: 2.00
(**) Logitech Logitech BT Mini-Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech Logitech BT Mini-Receiver: (accel) set acceleration profile 0
(II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
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

==> /home/tomas/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7

** (gnome-screensaver:2454): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
xfdesktop[2474]: starting up

(polkit-gnome-authentication-agent-1:2488): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2488): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
xfce4-settings-helper is already running

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             875G   17G  815G   2% /
udev                  1.5G  364K  1.5G   1% /dev
none                  1.5G     0  1.5G   0% /dev/shm
none                  1.5G  336K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw

==> uname -a <==
Linux Mythtv 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9300 / nForce 730i] (rev b1)
05:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller

==> lsusb <==
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c714 Logitech, Inc. 
Bus 004 Device 003: ID 046d:c713 Logitech, Inc. 
Bus 004 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2040:9950 Hauppauge 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 002 Device 003: ID 0bc2:3000 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

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
          size: 3023MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: [REMOVED]
          size: 2003MHz
          capacity: 2003MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:4f00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:14 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:f9e80000-f9efffff
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:f9e7f000-f9e7ffff
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:f9e7ec00-f9e7ecff
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:f9e7d000-f9e7dfff
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:f9e7e800-f9e7e8ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:22 memory:f9e78000-f9e7bfff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:c000(size=4096) memory:f9f00000-f9ffffff
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 62
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=uhci_hcd latency=64
                resources: irq:17 ioport:cc00(size=32)
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 6.1
                bus info: pci@0000:01:06.1
                version: 62
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=uhci_hcd latency=64
                resources: irq:16 ioport:c480(size=32)
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: 6.2
                bus info: pci@0000:01:06.2
                version: 65
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ehci_hcd latency=64
                resources: irq:18 memory:f9fff800-f9fff8ff
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: [REMOVED]
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=[REMOVED] latency=0 maxlatency=20 mingnt=1 multicast=yes
             resources: irq:23 memory:f9e7c000-f9e7cfff ioport:b480(size=8) memory:f9e7e400-f9e7e4ff memory:f9e7e000-f9e7e00f
        *-ide
             description: IDE interface
             product: MCP79 SATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:27 ioport:b400(size=8) ioport:b080(size=4) ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=16) memory:f9e76000-f9e77fff
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:d000(size=4096) memory:fa000000-fbefffff ioport:e0000000(size=402653184)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: C79 [GeForce 9300 / nForce 730i]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:fa000000-faffffff memory:e0000000-efffffff(prefetchable) memory:f6000000-f7ffffff(prefetchable) ioport:dc00(size=128) memory:fbee0000-fbefffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list rom
                configuration: driver=pata_jmicron latency=0
                resources: irq:19 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:fbff0000-fbffffff(prefetchable)
  *-scsi
       physical id: 1
       bus info: scsi@8
       logical name: scsi8
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=[REMOVED] multicast=yes wireless=IEEE 802.11bg

---

### Post by klc5555 on 2010-03-23
The backend appears to be unconfigured. Nor does the machine appear to be aware of any installed tuners (though lsusb does list some sort of hauppauge device). This might be a cause of the apparent unconfiguration.

As a start I would check to make sure the hardware/driver/firmware setup of your dvb tuner cards is functional (since you say you recently modified this) and make sure the machine is aware of your tuner hardware.

Once this is straightened out, you may have to run mythtv-setup (the backend setup) again, either from a prompt or from the desktop menu, in order to correctly add the card(s) and scan them, so that the backend will start and run.

Once the backend appears to be running, then you can try running the frontend from the desktop menu or from a prompt (mythfrontend), and see whether it will run at all, and, if so, whether it can connect properly to the running backend.

If all of this is OK --it connects --, then you can try some normal activities (like livetv or doing/playing a recording). 

If that works, then you can fine tune stuff --startup and cron jobs and such.

All this assumes that the installation is of long-enough standing to be worth salvaging.

---

### Post by blkbx on 2010-03-23
It's a new install so I'm probably going to do a reinstall. If it's going to do weird stuff like this at the beginning whats it going to do when it's all configured. I'd like to know why it did in the first place though so I don't repeat it. Just to make things clear wqith the error that I have. The backend and front end have uninstalled themselves completely. In your post you mention using them but do you need me to reinstall them I mean obvously I have to install them if their not there right then go ahead with what you suggest.

---

### Post by klc5555 on 2010-03-23
Your logs indicated that the backend/frontend were still present. I did not realize the components had uninstalled.

Generally, apt-get or synaptic will sometimes get huffy and eviscerate the entire myth backend/frontend installation if something the myth components are dependencies of (or are dependencies of them) gets uninstalled, or gets updated in a way the package managers can't quite follow. Like uninstalling lirc, for example, will cause all of mythtv to go away. There have been reports that the very latest NVidia drivers may also cause this type of odd behavior --for video drivers you might want to go with the installation default for the time being.

Otherwise, use Synaptic or apt-get to (re)install mythtv in your current installation. Pay attention to the files/packages the package managers may tell you that they want to delete when doing installation/uninstallation work before allowing them to proceed.

---

### Post by blkbx on 2010-03-29
Thanks for the reply.
I thought that it might have something to do with either the Nvidia driver or the dvb firmware that I loaded before things went south. I'll do a complete install of Mythbuntu. I haven't done much it the install so it's no great loss. How can I tell what Nvidia driver to stay away from.

---

### Post by klc5555 on 2010-03-29
> **blkbx said:**
> Thanks for the reply.
I thought that it might have something to do with either the Nvidia driver or the dvb firmware that I loaded before things went south. I'll do a complete install of Mythbuntu. I haven't done much it the install so it's no great loss. How can I tell what Nvidia driver to stay away from.

Stick with the distribution install level of the NVidia and other 3rd party drivers (and software), at least until know your way around the peculiarities of mythtv (to say nothing of ubuntu, which is weird enough by itself) well enough to diagnose things when (not if) they break. With the 3rd party stuff, like NVidia drivers, you gain very little by moving to the up-to-the-current-nanosecond version anyway, and frequently the stuff has not been vetted quite as well as it could be to make absolutely sure that it plays nicely on all systems. 

The downside of rapid version turnover schedules.

---

### Post by xinix on 2010-03-29
If you use synaptic, it will pop up a dialog that tells you it's going to remove mythtv.  I'd avoid the driver that triggers this.  Did you add a special repo for the nvidia driver?

---

### Post by bgiannes on 2010-04-06
special repo nvidia driver will uninstall mythtv!


you can reinstall myhtv with apt-get, the DB should still be intact.  i had this happen with my old install.  I have to reinstall mythtv and mythplugins everytime i did anything to the nvidia drivers.

so just stick to using the stock nvidia drivers in the repo, if you have a production mythtv server.

---

