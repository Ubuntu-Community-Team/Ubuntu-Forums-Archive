---
title: "poor kiwi can't surf"
date: 2009-08-25
forum: Mythbuntu
---

### Post by ubn2usr on 2009-08-25
As you probably guessed I'm in New Zealand. 
My problem is I can't get any channel when I do a scan.
I'm in Auckland and I think I use the sky tower for my reception. I dual boot and use cybercinema which works well with freeview. So I don't think there is anything with my ability to receive freeview channels.
I use a wintv nova-t 500 DVB-t with a new pc running Mythbuntu ver 9.04.
I've followed the nova-t wiki for installation though when I restarted the pc it didn't recognize the card but I can deal with that myself or ask for help a little later. What I mean is I can get the card recognized via the command line per session. Sorry off track
I'll include the error file and hope someone can make sense of it. Any help would be great.
thank

==> /var/log/mythtv/mtd.log <==
mtd started at Tue Aug 25 20:37:33 2009
mtd is running on a host called Mythtv
20:37:33: Waiting for connections/jobs
20:37:33: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-08-24 16:41:56.885 Using runtime prefix = /usr
2009-08-24 16:41:56.960 Empty LocalHostName.
2009-08-24 16:41:56.969 Using localhost value of Mythtv
2009-08-24 16:41:57.042 New DB connection, total: 1
2009-08-24 16:41:57.111 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.188 Closing DB connection named 'DBManager0'
2009-08-24 16:41:57.193 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.207 New DB connection, total: 2
2009-08-24 16:41:57.214 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.232 Current Schema Version: 1214
Running as a slave backend.
2009-08-24 16:41:57.494 New DB connection, total: 3
2009-08-24 16:41:57.532 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.534 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 16:41:57.573 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 16:41:57.602 DVBChan(2:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 16:41:57.605 ChannelBase(2) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 16:41:57.640 MediaServer:: Loopback address specified - 127.0.0.1      . Disabling UPnP
2009-08-24 16:41:57.659 Main::Registering HttpStatus Extension
2009-08-24 16:41:57.667 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-24 16:41:57.667 Enabled verbose msgs:  important general
2009-08-24 16:41:58.695 Connecting to master server: 127.0.0.1:6543
2009-08-24 16:41:58.907 Connected successfully
2009-08-24 16:42:29.237 MythSocket(b13080b0:10): readStringList: Error, timeout.
2009-08-24 16:42:29.257 adding: Mythtv as a slave backend server
2009-08-24 16:42:29.271 MythSocket(b1301748:-1): writeStringList: Error, socket went unconnected.
2009-08-24 17:58:31.181 MainServer::HandleAnnounce Monitor
2009-08-24 17:58:31.184 adding: Mythtv as a client (events: 0)
2009-08-24 17:58:31.185 MainServer::HandleAnnounce Monitor
2009-08-24 17:58:31.185 adding: Mythtv as a client (events: 1)
2009-08-24 17:58:31.188 MainServer::HandleAnnounce Playback
2009-08-24 17:58:31.200 adding: Mythtv as a client (events: 0)
2009-08-24 17:58:31.201 TVRec(1): Changing from None to WatchingLiveTV
2009-08-24 17:58:31.204 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2009-08-24 17:58:31.205 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2009-08-24 17:58:31.206 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 17:58:31.206 TVRec(1): HW Tuner: 1->1
2009-08-24 17:58:31.208 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 17:58:31.208 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2009-08-24 17:58:31.209 TVRec(1): Changing from WatchingLiveTV to None
2009-08-24 17:58:32.050 MainServer::HandleAnnounce Playback
2009-08-24 17:58:32.050 adding: Mythtv as a client (events: 0)
2009-08-24 17:58:32.051 TVRec(1): Changing from None to WatchingLiveTV
2009-08-24 17:58:32.056 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2009-08-24 17:58:32.057 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2009-08-24 17:58:32.057 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 17:58:32.058 TVRec(1): HW Tuner: 1->1
2009-08-24 17:58:32.059 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 17:58:32.059 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2009-08-24 17:58:32.060 TVRec(1): Changing from WatchingLiveTV to None
2009-08-25 20:37:26.293 Using runtime prefix = /usr
2009-08-25 20:37:26.368 Empty LocalHostName.
2009-08-25 20:37:26.377 Using localhost value of Mythtv
2009-08-25 20:37:26.450 New DB connection, total: 1
2009-08-25 20:37:26.530 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:26.563 Closing DB connection named 'DBManager0'
2009-08-25 20:37:26.578 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:26.579 New DB connection, total: 2
2009-08-25 20:37:26.580 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:26.707 Current Schema Version: 1214
Running as a slave backend.
2009-08-25 20:37:26.901 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-08-25 20:37:26.903 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-08-25 20:42:39.408 Using runtime prefix = /usr
2009-08-25 20:42:39.508 Empty LocalHostName.
2009-08-25 20:42:39.509 Using localhost value of Mythtv
2009-08-25 20:42:39.513 New DB connection, total: 1
2009-08-25 20:42:39.517 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:42:39.518 Closing DB connection named 'DBManager0'
2009-08-25 20:42:39.519 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:42:39.520 New DB connection, total: 2
2009-08-25 20:42:39.520 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:42:39.521 Current Schema Version: 1214
Running as a slave backend.
2009-08-25 20:42:39.526 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-08-25 20:42:39.527 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-08-25 20:42:39.528 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2009-08-25 20:42:39.529 DVBChan(3:-1) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

==> /var/log/mythtv/mythfrontend.log <==
2009-08-22 23:27:51.441 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-22 23:27:53.045 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-22 23:27:55.638 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-22 23:27:55.638 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-22 23:28:02.550 Deleting UPnP client...
Starting mythfrontend.real..
2009-08-24 16:42:07.517 New DB connection, total: 2
2009-08-24 16:42:07.517 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:42:07.518 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-24 16:42:07.518 Enabled verbose msgs:  important general
2009-08-24 16:42:07.557 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-24 16:42:09.545 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-24 16:42:09.545 Primary screen 0.
2009-08-24 16:42:09.545 Using screen 0, 1920x1080 at 0,0
2009-08-24 16:42:09.545 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-24 16:42:09.546 Switching to square mode (Mythbuntu-8.04)
2009-08-24 16:42:09.577 Using the Qt painter
2009-08-24 16:42:09.578 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2009-08-24 16:42:09.578 lirc init success using configuration file: /home/tomas/.mythtv/lircrc
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font clock
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font small
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font medium
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font large
2009-08-24 16:42:10.315 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-24 16:42:10.435 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-24 16:42:10.485 Registering Internal as a media playback plugin.
2009-08-24 16:42:10.602 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-24 16:42:10.864 Failed to run 'cdrecord --scanbus'
2009-08-24 16:42:10.866 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-24 16:42:10.867 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-24 16:42:10.880 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-24 16:42:10.988 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-24 17:12:07.514 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-24 17:42:07.545 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-24 17:58:31.180 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-24 17:58:31.181 Using protocol version 40
2009-08-24 17:58:31.188 TV: Attempting to change from None to WatchingLiveTV
2009-08-24 17:58:31.188 Using protocol version 40
2009-08-24 17:58:31.209 GetEntryAt(-1) failed.
2009-08-24 17:58:31.210 EntryToProgram(0@Thu Jan 1 12:00:00 1970) failed to get pginfo
2009-08-24 17:58:31.210 TV Error: LiveTV not successfully started
2009-08-24 17:58:31.210 TV Error: LiveTV not successfully started
2009-08-24 17:58:31.302 TV: Deleting TV Chain in destructor
2009-08-24 17:58:31.305 DPMS Deactivated 
2009-08-24 17:58:31.305 DPMS Reactivated.
2009-08-24 17:58:32.049 TV: Attempting to change from None to WatchingLiveTV
2009-08-24 17:58:32.049 Using protocol version 40
2009-08-24 17:58:32.061 GetEntryAt(-1) failed.
2009-08-24 17:58:32.061 EntryToProgram(0@Thu Jan 1 12:00:00 1970) failed to get pginfo
2009-08-24 17:58:32.061 TV Error: LiveTV not successfully started
2009-08-24 17:58:32.061 TV Error: LiveTV not successfully started
2009-08-24 17:58:32.150 TV: Deleting TV Chain in destructor
2009-08-24 17:58:32.153 DPMS Deactivated 
2009-08-24 17:58:32.153 DPMS Reactivated.
2009-08-24 17:58:37.157 Deleting UPnP client...
2009-08-24 17:58:37.157 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2009-08-25 20:37:37.726 New DB connection, total: 2
2009-08-25 20:37:37.726 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:37.727 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-25 20:37:37.727 Enabled verbose msgs:  important general
2009-08-25 20:37:39.738 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:37:39.739 Primary screen 0.
2009-08-25 20:37:39.739 Using screen 0, 1920x1080 at 0,0
2009-08-25 20:37:39.739 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:37:39.740 Switching to square mode (Mythbuntu-8.04)
2009-08-25 20:37:39.786 Using the Qt painter
2009-08-25 20:37:39.786 lirc init success using configuration file: /home/tomas/.mythtv/lircrc
2009-08-25 20:37:39.787 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font clock
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font small
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font medium
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font large
2009-08-25 20:37:40.535 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-25 20:37:40.643 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-25 20:37:40.670 Registering Internal as a media playback plugin.
2009-08-25 20:37:40.785 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-25 20:37:41.039 Failed to run 'cdrecord --scanbus'
2009-08-25 20:37:41.041 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-25 20:37:41.043 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-25 20:37:41.055 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-25 20:37:41.129 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:37:49.477 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-25 20:37:49.477 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-25 20:38:01.469 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:38:06.198 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-25 20:38:06.199 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-25 20:38:11.487 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Aug 25 20:37:28 Mythtv avahi-daemon[3457]: Network interface enumeration completed.
Aug 25 20:37:28 Mythtv avahi-daemon[3457]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 25 20:37:28 Mythtv avahi-daemon[3457]: Server startup complete. Host name is Mythtv.local. Local service cookie is 3719317468.
Aug 25 20:37:28 Mythtv nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Aug 25 20:37:28 Mythtv kernel: [   30.364177] ppdev: user-space parallel port driver
Aug 25 20:37:29 Mythtv acpid: client connected from 3409[0:0] 
Aug 25 20:37:29 Mythtv /usr/sbin/cron[3588]: (CRON) INFO (pidfile fd = 3)
Aug 25 20:37:29 Mythtv /usr/sbin/cron[3589]: (CRON) STARTUP (fork ok)
Aug 25 20:37:29 Mythtv /usr/sbin/cron[3589]: (CRON) INFO (Running @reboot jobs)
Aug 25 20:37:31 Mythtv console-kit-daemon[3167]: WARNING: Couldn't read /proc/3166/environ: Failed to open file '/proc/3166/environ': No such file or directory 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): bringing up device. 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): preparing device. 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 25 20:37:32 Mythtv kernel: [   33.524174] r8169: eth0: link up
Aug 25 20:37:32 Mythtv kernel: [   33.524178] r8169: eth0: link up
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Aug 25 20:37:32 Mythtv nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_24_21_10_21_71
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  dhclient started with pid 3904 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 25 20:37:33 Mythtv dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 25 20:37:33 Mythtv dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 25 20:37:33 Mythtv dhclient: All rights reserved.
Aug 25 20:37:33 Mythtv dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 25 20:37:33 Mythtv dhclient: 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Aug 25 20:37:33 Mythtv dhclient: Listening on LPF/eth0/00:24:21:10:21:71
Aug 25 20:37:33 Mythtv dhclient: Sending on   LPF/eth0/00:24:21:10:21:71
Aug 25 20:37:33 Mythtv dhclient: Sending on   Socket/fallback
Aug 25 20:37:33 Mythtv avahi-daemon[3457]: Registering new address record for fe80::224:21ff:fe10:2171 on eth0.*.
Aug 25 20:37:36 Mythtv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 25 20:37:36 Mythtv dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
Aug 25 20:37:36 Mythtv dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Aug 25 20:37:36 Mythtv dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Aug 25 20:37:36 Mythtv NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    address 192.168.2.3 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    prefix 24 (255.255.255.0) 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    gateway 192.168.2.1 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    nameserver '192.168.2.1' 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    domain name 'Belkin' 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 25 20:37:36 Mythtv avahi-daemon[3457]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.3.
Aug 25 20:37:36 Mythtv avahi-daemon[3457]: New relevant interface eth0.IPv4 for mDNS.
Aug 25 20:37:36 Mythtv avahi-daemon[3457]: Registering new address record for 192.168.2.3 on eth0.IPv4.
Aug 25 20:37:36 Mythtv dhclient: bound to 192.168.2.3 -- renewal in 882 seconds.
Aug 25 20:37:37 Mythtv NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Aug 25 20:37:37 Mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 25 20:37:37 Mythtv NetworkManager: <info>  Activation (eth0) successful, device activated. 
Aug 25 20:37:37 Mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: accepted new client on /dev/lircd
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: initializing '/dev/lirc0'
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: unable to open '/dev/lirc0'
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: Failed to initialize hardware
Aug 25 20:37:42 Mythtv kernel: [   44.412008] eth0: no IPv6 routers present
Aug 25 20:37:48 Mythtv ntpd[3139]: ntpd exiting on signal 15
Aug 25 20:37:50 Mythtv ntpdate[4132]: step time server 91.189.94.4 offset 0.916647 sec
Aug 25 20:37:50 Mythtv ntpd[4161]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Aug 25 20:37:50 Mythtv ntpd[4162]: precision = 1.000 usec
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #2 lo, ::1#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #3 eth0, fe80::224:21ff:fe10:2171#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #5 eth0, 192.168.2.3#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: kernel time sync status 0040
Aug 25 20:37:50 Mythtv ntpd[4162]: frequency initialized -30.974 PPM from /var/lib/ntp/ntp.drift
Aug 25 20:38:13 Mythtv lircd-0.8.4a[2661]: removed client
Aug 25 20:38:13 Mythtv lircd-0.8.4a[2661]: closing '/dev/lirc0'
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: accepted new client on /dev/lircd
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: initializing '/dev/lirc0'
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: unable to open '/dev/lirc0'
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: Failed to initialize hardware
Aug 25 20:39:01 Mythtv /USR/SBIN/CRON[4207]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 25 20:40:02 Mythtv /USR/SBIN/CRON[4374]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 25 20:42:08 Mythtv ntpd[4162]: synchronized to 91.189.94.4, stratum 2
Aug 25 20:42:08 Mythtv ntpd[4162]: kernel time sync status change 0001
Aug 25 20:42:36 Mythtv lircd-0.8.4a[2661]: removed client
Aug 25 20:42:36 Mythtv lircd-0.8.4a[2661]: closing '/dev/lirc0'
Aug 25 20:44:01 Mythtv kernel: [  421.908337] dib0700: loaded with support for 8 different device-types
Aug 25 20:44:01 Mythtv kernel: [  421.908376] usbcore: registered new interface driver dvb_usb_dib0700
Aug 25 20:50:01 Mythtv /USR/SBIN/CRON[4904]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

==> /var/log/Xorg.0.log <==
(II) NVIDIA(0): Assigned Display Device: DFP-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
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
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 9 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
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
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"

==> /home/tomas/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2009-08-25 20:37:33.176 Using runtime prefix = /usr
2009-08-25 20:37:33.176 Empty LocalHostName.
2009-08-25 20:37:33.176 Using localhost value of Mythtv
2009-08-25 20:37:33.200 New DB connection, total: 1
2009-08-25 20:37:33.203 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:33.203 Closing DB connection named 'DBManager0'
2009-08-25 20:37:33.203 Connected to database 'mythconverg' at host: localhost
/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[3947]: starting up

(xfce4-panel:3945): xfce4-panel-WARNING **: xfce4-panel is not running
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:3967): WARNING **: already running?

2009-08-25 20:37:37.034 Using runtime prefix = /usr
2009-08-25 20:37:37.034 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-25 20:37:37.035 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-25 20:37:37.567 XScreenSaver support enabled
2009-08-25 20:37:37.567 DPMS is active.
2009-08-25 20:37:37.567 Empty LocalHostName.
2009-08-25 20:37:37.567 Using localhost value of Mythtv
2009-08-25 20:37:37.571 New DB connection, total: 1
2009-08-25 20:37:37.574 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:37.574 Closing DB connection named 'DBManager0'
2009-08-25 20:37:37.575 Primary screen 0.
2009-08-25 20:37:37.575 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:37.575 Using screen 0, 1920x1080 at 0,0
** (nm-applet:3969): DEBUG: applet_common_device_state_changed
** (nm-applet:3969): DEBUG: foo_client_state_changed_cb
** (update-notifier:3950): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:3950): DEBUG: crashreport_check

 * Stopping MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
Traceback (most recent call last):
  File "/usr/bin/pastebinit", line 317, in <module>
    page = url_opener.open(website, params) #Send the informations and be redirected to the final page
  File "/usr/lib/python2.6/urllib.py", line 205, in open
    return getattr(self, name)(url, data)
  File "/usr/lib/python2.6/urllib.py", line 342, in open_http
    h.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 868, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 740, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 683, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 498, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
IOError: [Errno socket error] [Errno -2] Name or service not known

==> lsb_release -a <==

---

### Post by KillerKiwi on 2009-08-25
> **ubn2usr said:**
> As you probably guessed I'm in New Zealand. 
My problem is I can't get any channel when I do a scan.
I'm in Auckland and I think I use the sky tower for my reception. I dual boot and use cybercinema which works well with freeview. So I don't think there is anything with my ability to receive freeview channels.
I use a wintv nova-t 500 DVB-t with a new pc running Mythbuntu ver 9.04.
I've followed the nova-t wiki for installation though when I restarted the pc it didn't recognize the card but I can deal with that myself or ask for help a little later. What I mean is I can get the card recognized via the command line per session. Sorry off track
I'll include the error file and hope someone can make sense of it. Any help would be great.
thank

==> /var/log/mythtv/mtd.log <==
mtd started at Tue Aug 25 20:37:33 2009
mtd is running on a host called Mythtv
20:37:33: Waiting for connections/jobs
20:37:33: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-08-24 16:41:56.885 Using runtime prefix = /usr
2009-08-24 16:41:56.960 Empty LocalHostName.
2009-08-24 16:41:56.969 Using localhost value of Mythtv
2009-08-24 16:41:57.042 New DB connection, total: 1
2009-08-24 16:41:57.111 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.188 Closing DB connection named 'DBManager0'
2009-08-24 16:41:57.193 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.207 New DB connection, total: 2
2009-08-24 16:41:57.214 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.232 Current Schema Version: 1214
Running as a slave backend.
2009-08-24 16:41:57.494 New DB connection, total: 3
2009-08-24 16:41:57.532 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:41:57.534 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 16:41:57.573 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 16:41:57.602 DVBChan(2:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 16:41:57.605 ChannelBase(2) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 16:41:57.640 MediaServer:: Loopback address specified - 127.0.0.1      . Disabling UPnP
2009-08-24 16:41:57.659 Main::Registering HttpStatus Extension
2009-08-24 16:41:57.667 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-24 16:41:57.667 Enabled verbose msgs:  important general
2009-08-24 16:41:58.695 Connecting to master server: 127.0.0.1:6543
2009-08-24 16:41:58.907 Connected successfully
2009-08-24 16:42:29.237 MythSocket(b13080b0:10): readStringList: Error, timeout.
2009-08-24 16:42:29.257 adding: Mythtv as a slave backend server
2009-08-24 16:42:29.271 MythSocket(b1301748:-1): writeStringList: Error, socket went unconnected.
2009-08-24 17:58:31.181 MainServer::HandleAnnounce Monitor
2009-08-24 17:58:31.184 adding: Mythtv as a client (events: 0)
2009-08-24 17:58:31.185 MainServer::HandleAnnounce Monitor
2009-08-24 17:58:31.185 adding: Mythtv as a client (events: 1)
2009-08-24 17:58:31.188 MainServer::HandleAnnounce Playback
2009-08-24 17:58:31.200 adding: Mythtv as a client (events: 0)
2009-08-24 17:58:31.201 TVRec(1): Changing from None to WatchingLiveTV
2009-08-24 17:58:31.204 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2009-08-24 17:58:31.205 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2009-08-24 17:58:31.206 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 17:58:31.206 TVRec(1): HW Tuner: 1->1
2009-08-24 17:58:31.208 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 17:58:31.208 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2009-08-24 17:58:31.209 TVRec(1): Changing from WatchingLiveTV to None
2009-08-24 17:58:32.050 MainServer::HandleAnnounce Playback
2009-08-24 17:58:32.050 adding: Mythtv as a client (events: 0)
2009-08-24 17:58:32.051 TVRec(1): Changing from None to WatchingLiveTV
2009-08-24 17:58:32.056 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2009-08-24 17:58:32.057 ChannelBase(1): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2009-08-24 17:58:32.057 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2009-08-24 17:58:32.058 TVRec(1): HW Tuner: 1->1
2009-08-24 17:58:32.059 DVBChan(1:0) Error: SetChannelByString(Please add): CheckChannel failed.
			Please verify the channel in the 'mythtv-setup' Channel Editor.
2009-08-24 17:58:32.059 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2009-08-24 17:58:32.060 TVRec(1): Changing from WatchingLiveTV to None
2009-08-25 20:37:26.293 Using runtime prefix = /usr
2009-08-25 20:37:26.368 Empty LocalHostName.
2009-08-25 20:37:26.377 Using localhost value of Mythtv
2009-08-25 20:37:26.450 New DB connection, total: 1
2009-08-25 20:37:26.530 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:26.563 Closing DB connection named 'DBManager0'
2009-08-25 20:37:26.578 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:26.579 New DB connection, total: 2
2009-08-25 20:37:26.580 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:26.707 Current Schema Version: 1214
Running as a slave backend.
2009-08-25 20:37:26.901 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-08-25 20:37:26.903 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-08-25 20:42:39.408 Using runtime prefix = /usr
2009-08-25 20:42:39.508 Empty LocalHostName.
2009-08-25 20:42:39.509 Using localhost value of Mythtv
2009-08-25 20:42:39.513 New DB connection, total: 1
2009-08-25 20:42:39.517 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:42:39.518 Closing DB connection named 'DBManager0'
2009-08-25 20:42:39.519 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:42:39.520 New DB connection, total: 2
2009-08-25 20:42:39.520 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:42:39.521 Current Schema Version: 1214
Running as a slave backend.
2009-08-25 20:42:39.526 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-08-25 20:42:39.527 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-08-25 20:42:39.528 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2009-08-25 20:42:39.529 DVBChan(3:-1) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

==> /var/log/mythtv/mythfrontend.log <==
2009-08-22 23:27:51.441 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-22 23:27:53.045 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-22 23:27:55.638 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-22 23:27:55.638 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-22 23:28:02.550 Deleting UPnP client...
Starting mythfrontend.real..
2009-08-24 16:42:07.517 New DB connection, total: 2
2009-08-24 16:42:07.517 Connected to database 'mythconverg' at host: localhost
2009-08-24 16:42:07.518 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-24 16:42:07.518 Enabled verbose msgs:  important general
2009-08-24 16:42:07.557 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-24 16:42:09.545 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-24 16:42:09.545 Primary screen 0.
2009-08-24 16:42:09.545 Using screen 0, 1920x1080 at 0,0
2009-08-24 16:42:09.545 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-24 16:42:09.546 Switching to square mode (Mythbuntu-8.04)
2009-08-24 16:42:09.577 Using the Qt painter
2009-08-24 16:42:09.578 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2009-08-24 16:42:09.578 lirc init success using configuration file: /home/tomas/.mythtv/lircrc
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font clock
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font small
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font medium
2009-08-24 16:42:10.315 Specified base font 'medium' does not exist for font large
2009-08-24 16:42:10.315 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-24 16:42:10.435 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-24 16:42:10.485 Registering Internal as a media playback plugin.
2009-08-24 16:42:10.602 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-24 16:42:10.864 Failed to run 'cdrecord --scanbus'
2009-08-24 16:42:10.866 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-24 16:42:10.867 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-24 16:42:10.880 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-24 16:42:10.988 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-24 17:12:07.514 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-24 17:42:07.545 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-24 17:58:31.180 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-24 17:58:31.181 Using protocol version 40
2009-08-24 17:58:31.188 TV: Attempting to change from None to WatchingLiveTV
2009-08-24 17:58:31.188 Using protocol version 40
2009-08-24 17:58:31.209 GetEntryAt(-1) failed.
2009-08-24 17:58:31.210 EntryToProgram(0@Thu Jan 1 12:00:00 1970) failed to get pginfo
2009-08-24 17:58:31.210 TV Error: LiveTV not successfully started
2009-08-24 17:58:31.210 TV Error: LiveTV not successfully started
2009-08-24 17:58:31.302 TV: Deleting TV Chain in destructor
2009-08-24 17:58:31.305 DPMS Deactivated 
2009-08-24 17:58:31.305 DPMS Reactivated.
2009-08-24 17:58:32.049 TV: Attempting to change from None to WatchingLiveTV
2009-08-24 17:58:32.049 Using protocol version 40
2009-08-24 17:58:32.061 GetEntryAt(-1) failed.
2009-08-24 17:58:32.061 EntryToProgram(0@Thu Jan 1 12:00:00 1970) failed to get pginfo
2009-08-24 17:58:32.061 TV Error: LiveTV not successfully started
2009-08-24 17:58:32.061 TV Error: LiveTV not successfully started
2009-08-24 17:58:32.150 TV: Deleting TV Chain in destructor
2009-08-24 17:58:32.153 DPMS Deactivated 
2009-08-24 17:58:32.153 DPMS Reactivated.
2009-08-24 17:58:37.157 Deleting UPnP client...
2009-08-24 17:58:37.157 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2009-08-25 20:37:37.726 New DB connection, total: 2
2009-08-25 20:37:37.726 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:37.727 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-25 20:37:37.727 Enabled verbose msgs:  important general
2009-08-25 20:37:39.738 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:37:39.739 Primary screen 0.
2009-08-25 20:37:39.739 Using screen 0, 1920x1080 at 0,0
2009-08-25 20:37:39.739 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:37:39.740 Switching to square mode (Mythbuntu-8.04)
2009-08-25 20:37:39.786 Using the Qt painter
2009-08-25 20:37:39.786 lirc init success using configuration file: /home/tomas/.mythtv/lircrc
2009-08-25 20:37:39.787 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickmenurc
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font clock
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font small
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font medium
2009-08-25 20:37:40.534 Specified base font 'medium' does not exist for font large
2009-08-25 20:37:40.535 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-25 20:37:40.643 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-25 20:37:40.670 Registering Internal as a media playback plugin.
2009-08-25 20:37:40.785 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-25 20:37:41.039 Failed to run 'cdrecord --scanbus'
2009-08-25 20:37:41.041 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-25 20:37:41.043 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-25 20:37:41.055 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-25 20:37:41.129 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:37:49.477 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-25 20:37:49.477 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-25 20:38:01.469 No theme dir: /home/tomas/.mythtv/themes/Mythbuntu-8.04
2009-08-25 20:38:06.198 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-25 20:38:06.199 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-25 20:38:11.487 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Aug 25 20:37:28 Mythtv avahi-daemon[3457]: Network interface enumeration completed.
Aug 25 20:37:28 Mythtv avahi-daemon[3457]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 25 20:37:28 Mythtv avahi-daemon[3457]: Server startup complete. Host name is Mythtv.local. Local service cookie is 3719317468.
Aug 25 20:37:28 Mythtv nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Aug 25 20:37:28 Mythtv kernel: [   30.364177] ppdev: user-space parallel port driver
Aug 25 20:37:29 Mythtv acpid: client connected from 3409[0:0] 
Aug 25 20:37:29 Mythtv /usr/sbin/cron[3588]: (CRON) INFO (pidfile fd = 3)
Aug 25 20:37:29 Mythtv /usr/sbin/cron[3589]: (CRON) STARTUP (fork ok)
Aug 25 20:37:29 Mythtv /usr/sbin/cron[3589]: (CRON) INFO (Running @reboot jobs)
Aug 25 20:37:31 Mythtv console-kit-daemon[3167]: WARNING: Couldn't read /proc/3166/environ: Failed to open file '/proc/3166/environ': No such file or directory 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): bringing up device. 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): preparing device. 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 25 20:37:32 Mythtv kernel: [   33.524174] r8169: eth0: link up
Aug 25 20:37:32 Mythtv kernel: [   33.524178] r8169: eth0: link up
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Aug 25 20:37:32 Mythtv NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Aug 25 20:37:32 Mythtv nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_24_21_10_21_71
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  dhclient started with pid 3904 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 25 20:37:33 Mythtv dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 25 20:37:33 Mythtv dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 25 20:37:33 Mythtv dhclient: All rights reserved.
Aug 25 20:37:33 Mythtv dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 25 20:37:33 Mythtv dhclient: 
Aug 25 20:37:33 Mythtv NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Aug 25 20:37:33 Mythtv dhclient: Listening on LPF/eth0/00:24:21:10:21:71
Aug 25 20:37:33 Mythtv dhclient: Sending on   LPF/eth0/00:24:21:10:21:71
Aug 25 20:37:33 Mythtv dhclient: Sending on   Socket/fallback
Aug 25 20:37:33 Mythtv avahi-daemon[3457]: Registering new address record for fe80::224:21ff:fe10:2171 on eth0.*.
Aug 25 20:37:36 Mythtv dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 25 20:37:36 Mythtv dhclient: DHCPOFFER of 192.168.2.3 from 192.168.2.1
Aug 25 20:37:36 Mythtv dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Aug 25 20:37:36 Mythtv dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Aug 25 20:37:36 Mythtv NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    address 192.168.2.3 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    prefix 24 (255.255.255.0) 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    gateway 192.168.2.1 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    nameserver '192.168.2.1' 
Aug 25 20:37:36 Mythtv NetworkManager: <info>    domain name 'Belkin' 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 25 20:37:36 Mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 25 20:37:36 Mythtv avahi-daemon[3457]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.3.
Aug 25 20:37:36 Mythtv avahi-daemon[3457]: New relevant interface eth0.IPv4 for mDNS.
Aug 25 20:37:36 Mythtv avahi-daemon[3457]: Registering new address record for 192.168.2.3 on eth0.IPv4.
Aug 25 20:37:36 Mythtv dhclient: bound to 192.168.2.3 -- renewal in 882 seconds.
Aug 25 20:37:37 Mythtv NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Aug 25 20:37:37 Mythtv NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 25 20:37:37 Mythtv NetworkManager: <info>  Activation (eth0) successful, device activated. 
Aug 25 20:37:37 Mythtv NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: accepted new client on /dev/lircd
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: initializing '/dev/lirc0'
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: unable to open '/dev/lirc0'
Aug 25 20:37:39 Mythtv lircd-0.8.4a[2661]: Failed to initialize hardware
Aug 25 20:37:42 Mythtv kernel: [   44.412008] eth0: no IPv6 routers present
Aug 25 20:37:48 Mythtv ntpd[3139]: ntpd exiting on signal 15
Aug 25 20:37:50 Mythtv ntpdate[4132]: step time server 91.189.94.4 offset 0.916647 sec
Aug 25 20:37:50 Mythtv ntpd[4161]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Aug 25 20:37:50 Mythtv ntpd[4162]: precision = 1.000 usec
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #2 lo, ::1#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #3 eth0, fe80::224:21ff:fe10:2171#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: Listening on interface #5 eth0, 192.168.2.3#123 Enabled
Aug 25 20:37:50 Mythtv ntpd[4162]: kernel time sync status 0040
Aug 25 20:37:50 Mythtv ntpd[4162]: frequency initialized -30.974 PPM from /var/lib/ntp/ntp.drift
Aug 25 20:38:13 Mythtv lircd-0.8.4a[2661]: removed client
Aug 25 20:38:13 Mythtv lircd-0.8.4a[2661]: closing '/dev/lirc0'
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: accepted new client on /dev/lircd
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: initializing '/dev/lirc0'
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: unable to open '/dev/lirc0'
Aug 25 20:38:42 Mythtv lircd-0.8.4a[2661]: Failed to initialize hardware
Aug 25 20:39:01 Mythtv /USR/SBIN/CRON[4207]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 25 20:40:02 Mythtv /USR/SBIN/CRON[4374]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 25 20:42:08 Mythtv ntpd[4162]: synchronized to 91.189.94.4, stratum 2
Aug 25 20:42:08 Mythtv ntpd[4162]: kernel time sync status change 0001
Aug 25 20:42:36 Mythtv lircd-0.8.4a[2661]: removed client
Aug 25 20:42:36 Mythtv lircd-0.8.4a[2661]: closing '/dev/lirc0'
Aug 25 20:44:01 Mythtv kernel: [  421.908337] dib0700: loaded with support for 8 different device-types
Aug 25 20:44:01 Mythtv kernel: [  421.908376] usbcore: registered new interface driver dvb_usb_dib0700
Aug 25 20:50:01 Mythtv /USR/SBIN/CRON[4904]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

==> /var/log/Xorg.0.log <==
(II) NVIDIA(0): Assigned Display Device: DFP-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
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
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 9 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
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
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"

==> /home/tomas/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2009-08-25 20:37:33.176 Using runtime prefix = /usr
2009-08-25 20:37:33.176 Empty LocalHostName.
2009-08-25 20:37:33.176 Using localhost value of Mythtv
2009-08-25 20:37:33.200 New DB connection, total: 1
2009-08-25 20:37:33.203 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:33.203 Closing DB connection named 'DBManager0'
2009-08-25 20:37:33.203 Connected to database 'mythconverg' at host: localhost
/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[3947]: starting up

(xfce4-panel:3945): xfce4-panel-WARNING **: xfce4-panel is not running
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:3967): WARNING **: already running?

2009-08-25 20:37:37.034 Using runtime prefix = /usr
2009-08-25 20:37:37.034 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-25 20:37:37.035 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-25 20:37:37.567 XScreenSaver support enabled
2009-08-25 20:37:37.567 DPMS is active.
2009-08-25 20:37:37.567 Empty LocalHostName.
2009-08-25 20:37:37.567 Using localhost value of Mythtv
2009-08-25 20:37:37.571 New DB connection, total: 1
2009-08-25 20:37:37.574 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:37.574 Closing DB connection named 'DBManager0'
2009-08-25 20:37:37.575 Primary screen 0.
2009-08-25 20:37:37.575 Connected to database 'mythconverg' at host: localhost
2009-08-25 20:37:37.575 Using screen 0, 1920x1080 at 0,0
** (nm-applet:3969): DEBUG: applet_common_device_state_changed
** (nm-applet:3969): DEBUG: foo_client_state_changed_cb
** (update-notifier:3950): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:3950): DEBUG: crashreport_check

 * Stopping MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
Traceback (most recent call last):
  File "/usr/bin/pastebinit", line 317, in <module>
    page = url_opener.open(website, params) #Send the informations and be redirected to the final page
  File "/usr/lib/python2.6/urllib.py", line 205, in open
    return getattr(self, name)(url, data)
  File "/usr/lib/python2.6/urllib.py", line 342, in open_http
    h.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 868, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 740, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 683, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 498, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
IOError: [Errno socket error] [Errno -2] Name or service not known

==> lsb_release -a <==

Id suggest asking on the NZ mailing list
[http://lists.ourshack.com/mailman/listinfo/mythtvnz](http://lists.ourshack.com/mailman/listinfo/mythtvnz)

Note that DVB-T in NZ is a bit flacky at the moment due to the code not being in mythtv main yet there is a ppa somewhere , again best to have a look at the mailing list

---

### Post by ubn2usr on 2009-08-27
Thanks been checking that mailing list over the past couple of days.
If you think of anything I'd appreciate it you'd send me a post.

---

