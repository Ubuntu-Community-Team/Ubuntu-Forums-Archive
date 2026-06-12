---
title: "Mythmusic crashes to Desktop (randomly)"
date: 2008-11-14
forum: Mythbuntu
---

### Post by laffinet on 2008-11-14
My mythbox seems to be running okay, but every once in a while mythmusic crashes to the desktop. 

No particular moment, sometimes early after starting to play music, sometimes later, not during a specific songs (I started the same song that played when it crashed again and everything worked fine). 

No idea what's happening.

Below are the logs, but I couldn't see anything that helped me find a cause:

```
==> /var/log/mythtv/mtd.log <==
mtd started at Fri Nov 14 19:36:10 2008
mtd is running on a host called laffi-mythbox
19:36:10: Waiting for connections/jobs
19:36:10: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==

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
2008-11-14 19:18:20.793 Using runtime prefix = /usr
2008-11-14 19:18:20.857 Empty LocalHostName.
2008-11-14 19:18:20.867 Using localhost value of laffi-mythbox
2008-11-14 19:18:20.890 New DB connection, total: 1
2008-11-14 19:18:20.948 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:18:20.965 Closing DB connection named 'DBManager0'
2008-11-14 19:18:20.967 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:18:20.969 New DB connection, total: 2
2008-11-14 19:18:20.970 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:18:20.987 Current Schema Version: 1214
Starting up as the master server.
2008-11-14 19:18:21.326 New DB connection, total: 3
2008-11-14 19:18:21.367 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:18:21.476 New DB scheduler connection
2008-11-14 19:18:21.511 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:18:21.567 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-14 19:18:21.591 Main::Registering HttpStatus Extension
2008-11-14 19:18:21.610 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-14 19:18:21.610 Enabled verbose msgs:  important general
2008-11-14 19:18:21.612 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 19:18:24.535 Reschedule requested for id -1.
2008-11-14 19:18:24.819 Scheduled 10 items in 0.3 = 0.11 match + 0.18 place
2008-11-14 19:18:24.837 Seem to be woken up by USER
2008-11-14 19:18:58.664 MainServer::HandleAnnounce Monitor
2008-11-14 19:18:58.667 adding: laffi-mythbox as a client (events: 0)
2008-11-14 19:18:58.669 MainServer::HandleAnnounce Monitor
2008-11-14 19:18:58.670 adding: laffi-mythbox as a client (events: 1)
2008-11-14 19:19:41.552 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 19:34:41.596 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 19:36:04.389 Using runtime prefix = /usr
2008-11-14 19:36:04.431 Empty LocalHostName.
2008-11-14 19:36:04.451 Using localhost value of laffi-mythbox
2008-11-14 19:36:04.469 New DB connection, total: 1
2008-11-14 19:36:04.514 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:36:04.549 Closing DB connection named 'DBManager0'
2008-11-14 19:36:04.552 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:36:04.553 New DB connection, total: 2
2008-11-14 19:36:04.554 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:36:04.556 Current Schema Version: 1214
Starting up as the master server.
2008-11-14 19:36:04.683 New DB connection, total: 3
2008-11-14 19:36:04.813 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:36:04.909 New DB scheduler connection
2008-11-14 19:36:04.919 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:36:04.949 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-11-14 19:36:04.972 Main::Registering HttpStatus Extension
2008-11-14 19:36:04.978 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-11-14 19:36:04.984 Enabled verbose msgs:  important general
2008-11-14 19:36:05.028 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 19:36:07.923 Reschedule requested for id -1.
2008-11-14 19:36:08.118 Scheduled 10 items in 0.2 = 0.11 match + 0.09 place
2008-11-14 19:36:08.147 Seem to be woken up by USER
2008-11-14 19:36:50.707 MainServer::HandleAnnounce Monitor
2008-11-14 19:36:50.711 adding: laffi-mythbox as a client (events: 0)
2008-11-14 19:36:50.713 MainServer::HandleAnnounce Monitor
2008-11-14 19:36:50.714 adding: laffi-mythbox as a client (events: 1)
2008-11-14 19:36:58.897 MainServer::HandleAnnounce Monitor
2008-11-14 19:36:58.913 adding: laffi-mythbox as a client (events: 0)
2008-11-14 19:36:58.914 MainServer::HandleAnnounce Monitor
2008-11-14 19:36:58.915 adding: laffi-mythbox as a client (events: 1)
2008-11-14 19:36:58.990 MainServer::HandleAnnounce Monitor
2008-11-14 19:36:58.991 adding: laffi-mythbox as a client (events: 0)
2008-11-14 19:36:58.991 MainServer::HandleAnnounce Monitor
2008-11-14 19:36:58.992 adding: laffi-mythbox as a client (events: 1)
2008-11-14 19:37:13.419 MainServer::HandleAnnounce Monitor
2008-11-14 19:37:13.420 adding: laffi-mythbox as a client (events: 0)
2008-11-14 19:37:13.421 MainServer::HandleAnnounce Monitor
2008-11-14 19:37:13.422 adding: laffi-mythbox as a client (events: 1)
2008-11-14 19:37:24.926 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 19:52:24.968 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 19:59:14.533 MainServer::HandleAnnounce Monitor
2008-11-14 19:59:14.536 adding: laffi-mythbox as a client (events: 0)
2008-11-14 19:59:14.537 MainServer::HandleAnnounce Monitor
2008-11-14 19:59:14.537 adding: laffi-mythbox as a client (events: 1)
2008-11-14 19:59:14.539 Reschedule requested for id -1.
2008-11-14 19:59:14.590 Scheduled 10 items in 0.1 = 0.03 match + 0.02 place
2008-11-14 20:07:25.012 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 20:22:25.059 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 20:32:08.275 MainServer::HandleAnnounce Monitor
2008-11-14 20:32:08.279 adding: laffi-mythbox as a client (events: 0)
2008-11-14 20:32:08.280 MainServer::HandleAnnounce Monitor
2008-11-14 20:32:08.281 adding: laffi-mythbox as a client (events: 1)
2008-11-14 20:34:08.680 Reloading backend settings
2008-11-14 20:37:25.105 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-14 20:52:25.152 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2008-11-14 18:27:17.434 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 18:27:17.434 Switching to square mode (Mythbuntu-8.04)
2008-11-14 18:27:17.445 Using the Qt painter
2008-11-14 18:27:17.445 JoystickMenuClient Error: Joystick disabled - Failed to read /home/laffi/.mythtv/joystickmenurc
2008-11-14 18:27:17.446 lirc init success using configuration file: /home/laffi/.mythtv/lircrc
2008-11-14 18:27:18.024 Specified base font 'medium' does not exist for font clock
2008-11-14 18:27:18.024 Specified base font 'medium' does not exist for font small
2008-11-14 18:27:18.024 Specified base font 'medium' does not exist for font medium
2008-11-14 18:27:18.024 Specified base font 'medium' does not exist for font large
2008-11-14 18:27:18.025 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-14 18:27:18.101 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-14 18:27:18.123 Registering Internal as a media playback plugin.
2008-11-14 18:27:18.166 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-14 18:27:18.190 Failed to run 'cdrecord --scanbus'
2008-11-14 18:27:18.194 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-14 18:27:18.197 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-14 18:27:18.214 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-14 18:27:18.270 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 18:27:21.366 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-14 18:27:21.367 Using protocol version 40
2008-11-14 18:27:23.142 Deleting UPnP client...
Starting mythfrontend.real..
2008-11-14 19:18:32.747 New DB connection, total: 2
2008-11-14 19:18:32.747 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:18:32.749 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-14 19:18:32.749 Enabled verbose msgs:  important general
2008-11-14 19:18:32.753 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-11-14 19:18:34.407 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 19:18:34.408 Primary screen 0.
2008-11-14 19:18:34.408 Using screen 0, 1360x768 at 0,0
2008-11-14 19:18:34.408 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 19:18:34.409 Switching to square mode (Mythbuntu-8.04)
2008-11-14 19:18:34.449 Using the Qt painter
2008-11-14 19:18:34.450 lirc init success using configuration file: /home/laffi/.mythtv/lircrc
2008-11-14 19:18:34.451 JoystickMenuClient Error: Joystick disabled - Failed to read /home/laffi/.mythtv/joystickmenurc
2008-11-14 19:18:35.702 Specified base font 'medium' does not exist for font clock
2008-11-14 19:18:35.702 Specified base font 'medium' does not exist for font small
2008-11-14 19:18:35.702 Specified base font 'medium' does not exist for font medium
2008-11-14 19:18:35.702 Specified base font 'medium' does not exist for font large
2008-11-14 19:18:35.703 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-14 19:18:35.846 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-14 19:18:35.911 Registering Internal as a media playback plugin.
2008-11-14 19:18:36.015 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-14 19:18:36.226 Failed to run 'cdrecord --scanbus'
2008-11-14 19:18:36.229 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-14 19:18:36.232 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-14 19:18:36.254 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-14 19:18:36.436 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 19:18:58.653 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-14 19:18:58.655 Using protocol version 40
2008-11-14 19:18:59.863 Deleting UPnP client...
Starting mythfrontend.real..
2008-11-14 19:36:14.050 New DB connection, total: 2
2008-11-14 19:36:14.050 Connected to database 'mythconverg' at host: localhost
2008-11-14 19:36:14.051 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-14 19:36:14.051 Enabled verbose msgs:  important general
2008-11-14 19:36:14.103 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-11-14 19:36:15.805 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 19:36:15.806 Primary screen 0.
2008-11-14 19:36:15.806 Using screen 0, 1360x768 at 0,0
2008-11-14 19:36:15.806 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 19:36:15.807 Switching to square mode (Mythbuntu-8.04)
2008-11-14 19:36:15.832 Using the Qt painter
2008-11-14 19:36:15.833 JoystickMenuClient Error: Joystick disabled - Failed to read /home/laffi/.mythtv/joystickmenurc
2008-11-14 19:36:15.834 lirc init success using configuration file: /home/laffi/.mythtv/lircrc
2008-11-14 19:36:17.322 Specified base font 'medium' does not exist for font clock
2008-11-14 19:36:17.322 Specified base font 'medium' does not exist for font small
2008-11-14 19:36:17.322 Specified base font 'medium' does not exist for font medium
2008-11-14 19:36:17.322 Specified base font 'medium' does not exist for font large
2008-11-14 19:36:17.323 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-11-14 19:36:17.639 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-14 19:36:17.716 Registering Internal as a media playback plugin.
2008-11-14 19:36:18.279 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-14 19:36:18.524 Failed to run 'cdrecord --scanbus'
2008-11-14 19:36:18.527 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-14 19:36:18.530 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-14 19:36:18.549 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-11-14 19:36:18.707 No theme dir: /home/laffi/.mythtv/themes/Mythbuntu-8.04
2008-11-14 19:36:23.792 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/music-ui.xml
2008-11-14 19:36:25.493 Opening audio device 'default'. ch 2(2) sr 44100
2008-11-14 19:36:25.493 Opening ALSA audio device 'default'.
2008-11-14 19:36:25.569 Mixer unable to find control Master
2008-11-14 19:36:25.569 Mixer unable to find control Master
2008-11-14 19:36:25.660 DPMS Deactivated 
2008-11-14 19:36:47.835 DPMS Reactivated.
2008-11-14 19:36:50.690 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-14 19:36:50.692 Using protocol version 40
2008-11-14 19:36:52.523 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Nov 14 19:36:17 laffi-mythbox kernel: [   35.400653] wlan0: associated
Nov 14 19:36:17 laffi-mythbox kernel: [   35.400926] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 14 19:36:17 laffi-mythbox NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Nov 14 19:36:18 laffi-mythbox avahi-daemon[4950]: Registering new address record for fe80::221:91ff:fe89:c622 on wlan0.*.
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wireless'. 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  dhclient started with pid 6225 
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 14 19:36:18 laffi-mythbox dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov 14 19:36:18 laffi-mythbox dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 14 19:36:18 laffi-mythbox dhclient: All rights reserved.
Nov 14 19:36:18 laffi-mythbox dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 14 19:36:18 laffi-mythbox dhclient: 
Nov 14 19:36:18 laffi-mythbox dhclient: wmaster0: unknown hardware address type 801
Nov 14 19:36:18 laffi-mythbox NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Nov 14 19:36:18 laffi-mythbox dhclient: wmaster0: unknown hardware address type 801
Nov 14 19:36:19 laffi-mythbox dhclient: Listening on LPF/wlan0/00:21:91:89:c6:22
Nov 14 19:36:19 laffi-mythbox dhclient: Sending on   LPF/wlan0/00:21:91:89:c6:22
Nov 14 19:36:19 laffi-mythbox dhclient: Sending on   Socket/fallback
Nov 14 19:36:20 laffi-mythbox dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov 14 19:36:20 laffi-mythbox dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.254
Nov 14 19:36:20 laffi-mythbox dhclient: DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
Nov 14 19:36:20 laffi-mythbox dhclient: DHCPACK of 192.168.1.100 from 192.168.1.254
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>    address 192.168.1.100 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>    prefix 24 (255.255.255.0) 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>    gateway 192.168.1.254 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>    hostname 'laffi-mythbox' 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>    nameserver '192.168.1.254' 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 14 19:36:20 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 14 19:36:20 laffi-mythbox dhclient: bound to 192.168.1.100 -- renewal in 17728 seconds.
Nov 14 19:36:20 laffi-mythbox avahi-daemon[4950]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Nov 14 19:36:20 laffi-mythbox avahi-daemon[4950]: New relevant interface wlan0.IPv4 for mDNS.
Nov 14 19:36:20 laffi-mythbox avahi-daemon[4950]: Registering new address record for 192.168.1.100 on wlan0.IPv4.
Nov 14 19:36:21 laffi-mythbox NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Nov 14 19:36:21 laffi-mythbox NetworkManager: <info>  Policy set 'Wireless connection 1' (wlan0) as default for routing and DNS. 
Nov 14 19:36:21 laffi-mythbox NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Nov 14 19:36:21 laffi-mythbox NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 14 19:36:21 laffi-mythbox nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1
Nov 14 19:36:21 laffi-mythbox ntpd[5549]: ntpd exiting on signal 15
Nov 14 19:36:23 laffi-mythbox ntpdate[6312]: adjust time server 91.189.94.4 offset -0.004588 sec
Nov 14 19:36:23 laffi-mythbox ntpd[6353]: ntpd 4.2.4p4@1.1520-o Wed Aug 20 17:03:52 UTC 2008 (1)
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: precision = 1.000 usec
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: Listening on interface #2 wlan0, 192.168.1.100#123 Enabled
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: kernel time sync status 0040
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: frequency initialized -22.705 PPM from /var/lib/ntp/ntp.drift
Nov 14 19:36:23 laffi-mythbox ntpd[6354]: getaddrinfo: "::1" invalid host address, ignored
Nov 14 19:36:27 laffi-mythbox kernel: [   45.496019] wlan0: no IPv6 routers present
Nov 14 19:36:36 laffi-mythbox kernel: [   54.032730] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Nov 14 19:36:53 laffi-mythbox lircd-0.8.3[3863]: removed client
Nov 14 19:36:55 laffi-mythbox lircd-0.8.3[3863]: accepted new client on /dev/lircd
Nov 14 19:36:55 laffi-mythbox lircd-0.8.3[3863]: accepted new client on /dev/lircd
Nov 14 19:37:02 laffi-mythbox lircd-0.8.3[3863]: removed client
Nov 14 19:37:02 laffi-mythbox lircd-0.8.3[3863]: removed client
Nov 14 19:37:08 laffi-mythbox lircd-0.8.3[3863]: accepted new client on /dev/lircd
Nov 14 19:37:16 laffi-mythbox lircd-0.8.3[3863]: removed client
Nov 14 19:37:18 laffi-mythbox lircd-0.8.3[3863]: accepted new client on /dev/lircd
Nov 14 19:39:01 laffi-mythbox /USR/SBIN/CRON[6865]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 14 19:40:43 laffi-mythbox ntpd[6354]: synchronized to 91.189.94.4, stratum 2
Nov 14 19:40:43 laffi-mythbox ntpd[6354]: kernel time sync status change 0001
Nov 14 19:41:11 laffi-mythbox NetworkManager: <debug> [1226653871.042533] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:41:17 laffi-mythbox NetworkManager: <debug> [1226653877.046039] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:43:11 laffi-mythbox NetworkManager: <debug> [1226653991.124282] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:43:17 laffi-mythbox NetworkManager: <debug> [1226653997.130027] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:43:55 laffi-mythbox NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Nov 14 19:43:55 laffi-mythbox NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Nov 14 19:45:11 laffi-mythbox NetworkManager: <debug> [1226654111.206455] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:45:17 laffi-mythbox NetworkManager: <debug> [1226654117.210529] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:47:11 laffi-mythbox NetworkManager: <debug> [1226654231.286391] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:47:17 laffi-mythbox NetworkManager: <debug> [1226654237.290178] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:49:11 laffi-mythbox NetworkManager: <debug> [1226654351.365946] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:49:17 laffi-mythbox NetworkManager: <debug> [1226654357.366022] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:51:11 laffi-mythbox NetworkManager: <debug> [1226654471.441948] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:51:17 laffi-mythbox NetworkManager: <debug> [1226654477.446678] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:53:11 laffi-mythbox NetworkManager: <debug> [1226654591.523633] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:53:17 laffi-mythbox NetworkManager: <debug> [1226654597.526739] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:55:11 laffi-mythbox NetworkManager: <debug> [1226654711.602441] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:55:17 laffi-mythbox NetworkManager: <debug> [1226654717.606519] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:57:11 laffi-mythbox NetworkManager: <debug> [1226654831.682124] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Nov 14 19:57:17 laffi-mythbox NetworkManager: <debug> [1226654837.686520] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Nov 14 19:59:01 laffi-mythbox /USR/SBIN/CRON[6957]: (laffi) CMD (nice mythfilldatabase --graboptions '--daily')
Nov 14 20:06:43 laffi-mythbox lircd-0.8.3[3863]: removed client
Nov 14 20:07:29 laffi-mythbox lircd-0.8.3[3863]: accepted new client on /dev/lircd
Nov 14 20:09:01 laffi-mythbox /USR/SBIN/CRON[7219]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 14 20:17:01 laffi-mythbox /USR/SBIN/CRON[7284]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 14 20:35:58 laffi-mythbox -- MARK --
Nov 14 20:39:01 laffi-mythbox /USR/SBIN/CRON[7998]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 14 20:51:05 laffi-mythbox lircd-0.8.3[3863]: removed client

==> /var/log/Xorg.0.log <==
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1360x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
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
(II) config/hal: Adding input device cx88 IR (WinFast DTV2000 H ver.
(**) cx88 IR (WinFast DTV2000 H ver.: always reports core events
(**) cx88 IR (WinFast DTV2000 H ver.: Device: "/dev/input/event7"
(II) cx88 IR (WinFast DTV2000 H ver.: Found keys
(II) cx88 IR (WinFast DTV2000 H ver.: Configuring as keyboard
(II) XINPUT: Adding extended input device "cx88 IR (WinFast DTV2000 H ver." (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) cx88 IR (WinFast DTV2000 H ver.: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) cx88 IR (WinFast DTV2000 H ver.: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) cx88 IR (WinFast DTV2000 H ver.: xkb_layout: "de"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event1"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 5 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Logitech USB Receiver: xkb_layout: "de"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Logitech USB Receiver: xkb_layout: "de"

==> /home/laffi/.xsession-errors <==
b608f000-b6090000 rwxp b608f000 00:00 0 
b6090000-b60ff000 r-xp 00000000 08:01 514517     /usr/lib/libGLU.so.1.3.070200
b60ff000-b6100000 r--p 0006f000 08:01 514517     /usr/lib/libGLU.so.1.3.070200
b6100000-b6101000 rw-p 00070000 08:01 514517     /usr/lib/libGLU.so.1.3.070200
b6101000-b67f3000 r-xp 00000000 08:01 515292     /usr/lib/libqt-mt.so.3.3.8
b67f3000-b6833000 rw-p 006f1000 08:01 515292     /usr/lib/libqt-mt.so.3.3.8
b6833000-b6838000 rw-p b6833000 00:00 0 
b6838000-b683b000 r-xp 00000000 08:01 514641     /usr/lib/libXvMC.so.1.0.0
b683b000-b683c000 rw-p 00002000 08:01 514641     /usr/lib/libXvMC.so.1.0.0
b683c000-b6840000 r-xp 00000000 08:01 514643     /usr/lib/libXvMCW.so.1.0.0
b6840000-b6841000 rw-p 00003000 08:01 514643     /usr/lib/libXvMCW.so.1.0.0
b6841000-b6846000 r-xp 00000000 08:01 514629     /usr/lib/libXrandr.so.2.1.0
b6846000-b6847000 r--p 00005000 08:01 514629     /usr/lib/libXrandr.so.2.1.0
b6847000-b6848000 rw-p 00006000 08:01 514629     /usr/lib/libXrandr.so.2.1.0
b6848000-b684c000 r-xp 00000000 08:01 514649     /usr/lib/libXxf86vm.so.1.0.0
b684c000-b684d000 r--p 00003000 08:01 514649     /usr/lib/libXxf86vm.so.1.0.0
b684d000-b684e000 rw-p 00004000 08:01 514649     /usr/lib/libXxf86vm.so.1.0.0
b684e000-b6852000 r-xp 00000000 08:01 514639     /usr/lib/libXv.so.1.0.0
b6852000-b6853000 r--p 00003000 08:01 514639     /usr/lib/libXv.so.1.0.0
b6853000-b6854000 rw-p 00004000 08:01 514639     /usr/lib/libXv.so.1.0.0
b6854000-b6856000 r-xp 00000000 08:01 514621     /usr/lib/libXinerama.so.1.0.0
b6856000-b6857000 rw-p 00001000 08:01 514621     /usr/lib/libXinerama.so.1.0.0
b6857000-b6858000 rw-p b6857000 00:00 0 
b6858000-b685b000 r-xp 00000000 08:01 515313     /usr/lib/librom1394.so.0.3.0
b685b000-b685c000 rw-p 00002000 08:01 515313     /usr/lib/librom1394.so.0.3.0
b685c000-b685f000 r-xp 00000000 08:01 514694     /usr/lib/libavc1394.so.0.3.0
b685f000-b6860000 rw-p 00002000 08:01 514694     /usr/lib/libavc1394.so.0.3.0
b6860000-b686c000 r-xp 00000000 08:01 515051     /usr/lib/libiec61883.so.0.1.0
b686c000-b686d000 rw-p 0000b000 08:01 515051     /usr/lib/libiec61883.so.0.1.0
b686d000-b6872000 r-xp 00000000 08:01 515301     /usr/lib/libraw1394.so.8.2.0
b6872000-b6873000 r--p 00004000 08:01 515301     /usr/lib/libraw1394.so.8.2.0
b6873000-b6874000 rw-p 00005000 08:01 515301     /usr/lib/libraw1394.so.8.2.0
b6874000-b6882000 r-xp 00000000 08:01 515064     /usr/lib/libjack.so.0.0.28
b6882000-b6883000 r--p 0000e000 08:01 515064     /usr/lib/libjack.so.0.0.28
b6883000-b6885000 rw-p 0000f000 08:01 515064     /usr/lib/libjack.so.0.0.28
b6885000-b688d000 rw-p b6885000 00:00 0 
b688d000-b6892000 r-xp 00000000 08:01 514670     /usr/lib/libartsc.so.0.0.0
b6892000-b6893000 r--p 00004000 08:01 514670     /usr/lib/libartsc.so.0.0.0
b6893000-b6894000 rw-p 00005000 08:01 514670     /usr/lib/libartsc.so.0.0.0
b6894000-b6895000 rw-p b6894000 00:00 0 
b6895000-b6958000 r-xp 00000000 08:01 514672     /usr/lib/libasound.so.2.0.0
b6958000-b695a000 r--p 000c2000 08:01 514672     /usr/lib/libasound.so.2.0.0
b695a000-b695d000 rw-p 000c4000 08:01 514672     /usr/lib/libasound.so.2.0.0
b695d000-b699f000 r-xp 00000000 08:01 515132     /usr/lib/libmp3lame.so.0.0.0
b699f000-b69a0000 r--p 00042000 08:01 515132     /usr/lib/libmp3lame.so.0.0.0
b69a0000-b69a2000 rw-p 00043000 08:01 515132     /usr/lib/libmp3lame.so.0.0.0
b69a2000-b69d2000 rw-p b69a2000 00:00 0 
b69d2000-b69e6000 r-xp 00000000 08:01 515476     /usr/lib/libz.so.1.2.3.3
b69e6000-b69e8000 rw-p 00013000 08:01 515476     /usr/lib/libz.so.1.2.3.3
b69e8000-b6a59000 r-xp 00000000 08:01 514881     /usr/lib/libfreetype.so.6.3.18
b6a59000-b6a5d000 r--p 00070000 08:01 514881     /usr/lib/libfreetype.so.6.3.18
b6a5d000-b6a5e000 rw-p 00074000 08:01 514881     /usr/lib/libfreetype.so.6.3.18
b6a5e000-b6aef000 r-xp 00000000 08:01 515174     /usr/lib/libmythui-0.21.so.0.21.0
b6aef000-b6af1000 r--p 00090000 08:01 515174     /usr/lib/libmythui-0.21.so.0.21.0
b6af1000-b6af2000 rw-p 00092000 08:01 515174     /usr/lib/libmythui-0.21.so.0.21.0
b6af2000-b6de7000 r-xp 00000000 08:01 515153     /usr/lib/libmyth-0.21.so.0.21.0
b6de7000-b6de8000 ---p 002f5000 08:01 515153     /usr/lib/libmyth-0.21.so.0.21.0
b6de8000-b6df6000 r--p 002f5000 08:01 515153     /usr/lib/libmyth-0.21.so.0.21.0
b6df6000-b6df9000 rw-p 00303000 08:01 515153     /usr/lib/libmyth-0.21.so.0.21.0
b6df9000-b6dfb000 rw-p b6df9000 00:00 0 
b6dfb000-b6eb6000 r-xp 00000000 08:01 515168     /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6eb6000-b6ebb000 r--p 000bb000 08:01 515168     /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6ebb000-b6ec1000 rw-p 000c0000 08:01 515168     /usr/lib/libmythlivemedia-0.21.so.0.21.0
b6ec1000-b6ecf000 rw-p b6ec1000 00:00 0 
b6ecf000-b6f69000 r-xp 00000000 08:01 515177     /usr/lib/libmythupnp-0.21.so.0.21.0
b6f69000-b6f6b000 r--p 00099000 08:01 515177     /usr/lib/libmythupnp-0.21.so.0.21.0
b6f6b000-b6f6c000 rw-p 0009b000 08:01 515177     /usr/lib/libmythupnp-0.21.so.0.21.0
b6f6c000-b6fe6000 r-xp 00000000 08:01 515165     /usr/lib/libmythfreemheg-0.21.so.0.21.0
b6fe6000-b6fec000 r--p 00079000 08:01 515165     /usr/lib/libmythfreemheg-0.21.so.0.21.0
b6fec000-b6fed000 rw-p 0007f000 08:01 515165     /usr/lib/libmythfreemheg-0.21.so.0.21.0
b6fed000-b738a000 r-xp 00000000 08:01 515156     /usr/lib/libmythavcodec-0.21.so.0.21.0
b738a000-b7392000 r--p 0039d000 08:01 515156     /usr/lib/libmythavcodec-0.21.so.0.21.0
b7392000-b7399000 rw-p 003a5000 08:01 515156     /usr/lib/libmythavcodec-0.21.so.0.21.0
b7399000-b7499000 rw-p b7399000 00:00 0 
b7499000-b74a2000 r-xp 00000000 08:01 515162     /usr/lib/libmythavutil-0.21.so.0.21.0
b74a2000-b74a3000 r--p 00008000 08:01 515162     /usr/lib/libmythavutil-0.21.so.0.21.0
b74a3000-b74a4000 rw-p 00009000 08:01 515162     /usr/lib/libmythavutil-0.21.so.0.21.0
b74a4000-b74a7000 rw-p b74a4000 00:00 0 
b74a7000-b752b000 r-xp 00000000 08:01 515159     /usr/lib/libmythavformat-0.21.so.0.21.0
b752b000-b752d000 r--p 00084000 08:01 515159     /usr/lib/libmythavformat-0.21.so.0.21.0
b752d000-b7533000 rw-p 00086000 08:01 515159     /usr/lib/libmythavformat-0.21.so.0.21.0
b7533000-b7537000 rw-p b7533000 00:00 0 
b7537000-b7f55000 r-xp 00000000 08:01 515171     /usr/lib/libmythtv-0.21.so.0.21.0
b7f55000-b7f72000 r--p 00a1d000 08:01 515171     /usr/lib/libmythtv-0.21.so.0.21.0
b7f72000-b7f8b000 rw-p 00a3a000 08:01 515171     /usr/lib/libmythtv-0.21.so.0.21.0
b7f8b000-b7f8f000 rw-p b7f8b000 00:00 0 
b7f8f000-b7f90000 r--p 00000000 08:01 565001     /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
b7f90000-b7f91000 r--p 00000000 08:01 565002     /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
b7f91000-b7f98000 r--s 00000000 08:01 163123     /usr/lib/gconv/gconv-modules.cache
b7f98000-b7f99000 r--p 00000000 08:01 565003     /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
b7f99000-b7f9b000 rwxp 00000000 00:0e 663        /dev/zero
b7f9b000-b7f9d000 rw-p b7f9b000 00:00 0 
b7f9d000-b7fb7000 r-xp 00000000 08:01 447938     /lib/ld-2.8.90.so
b7fb7000-b7fb8000 r-xp b7fb7000 00:00 0          [vdso]
b7fb8000-b7fb9000 r--p 0001a000 08:01 447938     /lib/ld-2.8.90.so
b7fb9000-b7fba000 rw-p 0001b000 08:01 447938     /lib/ld-2.8.90.so
bfb97000-bfbba000 rwxp bffdd000 00:00 0          [stack]
/home/laffi/runmyth: 15: 2008-11-14: not found
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.0G  8.5G  20% /
tmpfs                 949M     0  949M   0% /lib/init/rw
varrun                949M  364K  949M   1% /var/run
varlock               949M     0  949M   0% /var/lock
udev                  949M  2.8M  946M   1% /dev
tmpfs                 949M     0  949M   0% /dev/shm
lrm                   949M  2.0M  947M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6             286G   57G  230G  20% /var/lib

==> uname -a <==
Linux laffi-mythbox 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

==> lspci <==
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

==> lsusb <==
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 002: ID 1784:0008 TopSeed Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c503 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
GCC version:  gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce 7050 PV / NVIDIA nForce 630a
IRQ:   		 20
Video BIOS: 	 05.67.32.25.00
Card Type: 	 PCI
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 00.12.0

==> lshw <==
computer
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=40019F7A-8DFE-D511-B389-002215D4B9C6
  *-core
       description: Motherboard
       product: M2N68-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0308 (07/18/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.11.2
          serial: [REMOVED]
          slot: AM2
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory:0
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.11.2
          size: 2600MHz
          capacity: 2600MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 13
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
        *-multimedia:0
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant Systems, Inc.
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
        *-multimedia:1
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
             vendor: Conexant Systems, Inc.
             physical id: 6.1
             bus info: pci@0000:01:06.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88_audio latency=64 maxlatency=255 mingnt=4 module=cx88_alsa
        *-multimedia:2
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
             vendor: Conexant Systems, Inc.
             physical id: 6.2
             bus info: pci@0000:01:06.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6 module=cx8802
        *-network
             description: Wireless interface
             product: RT2561/RT61 rev B 802.11g
             vendor: RaLink
             physical id: 7
             bus info: pci@0000:01:07.0
             logical name: wmaster0
             version: 00
             serial: [REMOVED]
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=rt61pci ip=[REMOVED] latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223F
             vendor: TSSTcorp
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: WDC WD3200AAKS-0
             vendor: Western Digital
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ef831
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: [REMOVED]
                size: 11GiB
                capacity: 11GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-11-12 16:52:14 filesystem=ext3 modified=2008-11-14 19:35:48 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-14 19:18:10 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 286GiB
                capacity: 286GiB
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
                   capacity: 285GiB
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: [REMOVED]
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:5
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:6
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:7
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 11
          bus info: pci@0000:00:11.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: GeForce 7050 PV / nForce 630a
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
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

Any help is much appreciated because this is really starting to annoy me !

---

### Post by egandy on 2008-11-15
The visualization Scope causes my mythmusic to crash to the desktop.

When I have mythmusic set to random visualizations it will crash at the end of the song displaying scope.  Sometimes it will also crash in the middle of the song.  It only happens in fullscreen visualizations for me.  Exiting out of fullscreen visualizations also causes a crash when scope is being displayed. My problem may be totally unrelated to yours but hopefully it may help track yours down. Good Luck

---

### Post by anonymousdog on 2008-11-15
I can't even use full screen visualizations on my low power frontends; I find the CPU load is very high.  So, it wouldn't surprise me to find some systems brought to their knees by them.

---

### Post by laffinet on 2008-11-15
Yeah, I suspected that it might have something to do with some of the visualisations. 

As a test I switched all of them off and since then mythmusic has been running fine. I might switch them back on one by one and see what other ones cause crashes too.  

Thanks.

---

