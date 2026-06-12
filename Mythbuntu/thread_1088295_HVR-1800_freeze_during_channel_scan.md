---
title: "HVR-1800 freeze during channel scan"
date: 2009-03-05
forum: Mythbuntu
---

### Post by marquarc on 2009-03-05
I'm trying to get a Mythbuntu box set up and going, but every time I do a channel scan the box locks up. I'm somewhat familiar with Ubuntu, but not at all familiar with tv tuner cards or hardware troubleshooting. I bought a Hauppauge WinTV-HVR-1800, because it seemed like a lot of other people were getting OTA ATSC working with no problems. I've been googling and looking at the forums for over a week now and haven't made much progress. 

I filled in everything I could in mythbuntu's backend setup. When I get to channel editing, I click the scan channels button and it looks good. Scans up until channel 13, which is the first local channel here and that's where it freezes. "No Lock" changes to "Lock", the Scroll and Caps lock buttons start flashing on my keyboard, key/mouse stop responding, and I can't even get to another console. I have to then remove power to the PC, and wait a few minutes before booting again. If I boot again too soon, I get "kernel panic - not syncing: fatal exception in interrupt." (I have checked my memory, and it's just fine)

Looking at the backend logs, there is an error about not being able to get inputs for the capturecard. It should be noted that I *have* set an input to the capture card (DVB: 0). I used "no grabber," since I don't have an account to any of the XMLTV things. 

Some things that people might need to know:
-kernel: 2.6.27-7
-Mythtv: 0.21.0
-In mythbackend's setup, the Frontend ID is Samsung S5H1409
-cannot watch liveTV in any program I've tried
-channel scan won't run at all in kaffeine (and no live tv there, either)
-channel scan locks up similarly when run from me-tv
-I have installed/compile mercurial and the v4l-dvb drivers
-I'm using generic Open Source drivers, not the ATI proprietary ones (every time I try these and reboot, mythbuntu's frontend is garbage)
-I don't care about NTSC, only ATSC :) and I'm in the US.

Here are the logs that mythbuntu has generated after the latest crash:

```

==> /var/log/mythtv/mtd.log <==
mtd started at Thu Mar 5 20:06:29 2009
mtd is running on a host called beholder
20:06:29: Waiting for connections/jobs
20:06:29: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-03-05 19:30:39.052 Seem to be woken up by USER
2009-03-05 19:31:56.005 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-05 19:32:26.433 MainServer::HandleAnnounce Monitor
2009-03-05 19:32:26.437 adding: beholder as a client (events: 0)
2009-03-05 19:32:26.438 MainServer::HandleAnnounce Monitor
2009-03-05 19:32:26.438 adding: beholder as a client (events: 1)
2009-03-05 19:40:22.495 Using runtime prefix = /usr
2009-03-05 19:40:22.537 Empty LocalHostName.
2009-03-05 19:40:22.540 Using localhost value of beholder
2009-03-05 19:40:22.606 New DB connection, total: 1
2009-03-05 19:40:22.638 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:40:22.790 Closing DB connection named 'DBManager0'
2009-03-05 19:40:22.796 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:40:22.811 New DB connection, total: 2
2009-03-05 19:40:22.812 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:40:22.833 Current Schema Version: 1214
Starting up as the master server.
2009-03-05 19:40:23.014 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-03-05 19:40:23.028 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-03-05 19:40:23.071 New DB connection, total: 3
2009-03-05 19:40:23.080 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:40:23.111 DVBChan(2:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-03-05 19:40:23.169 New DB scheduler connection
2009-03-05 19:40:23.180 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:40:23.249 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-03-05 19:40:23.258 Main::Registering HttpStatus Extension
2009-03-05 19:40:23.264 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 19:40:23.265 Enabled verbose msgs:  important general
2009-03-05 19:40:23.277 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-05 19:40:26.199 Reschedule requested for id -1.
2009-03-05 19:40:26.234 Scheduled 0 items in 0.0 = 0.03 match + 0.01 place
2009-03-05 19:40:26.239 Seem to be woken up by USER
2009-03-05 19:41:43.199 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-05 19:45:05.228 MainServer::HandleAnnounce Monitor
2009-03-05 19:45:05.231 adding: beholder as a client (events: 0)
2009-03-05 19:45:05.232 MainServer::HandleAnnounce Monitor
2009-03-05 19:45:05.233 adding: beholder as a client (events: 1)
2009-03-05 19:52:56.077 Using runtime prefix = /usr
2009-03-05 19:52:56.107 Empty LocalHostName.
2009-03-05 19:52:56.133 Using localhost value of beholder
2009-03-05 19:52:56.221 New DB connection, total: 1
2009-03-05 19:52:56.253 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:52:56.316 Closing DB connection named 'DBManager0'
2009-03-05 19:52:56.329 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:52:56.334 New DB connection, total: 2
2009-03-05 19:52:56.357 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:52:56.435 Current Schema Version: 1214
Starting up as the master server.
2009-03-05 19:52:56.641 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-03-05 19:52:56.653 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-03-05 19:52:56.697 New DB connection, total: 3
2009-03-05 19:52:56.715 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:52:56.737 DVBChan(2:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-03-05 19:52:56.765 New DB scheduler connection
2009-03-05 19:52:56.769 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:52:56.842 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-03-05 19:52:56.843 Main::Registering HttpStatus Extension
2009-03-05 19:52:56.844 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 19:52:56.847 Enabled verbose msgs:  important general
2009-03-05 19:52:56.892 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-05 19:52:59.785 Reschedule requested for id -1.
2009-03-05 19:52:59.808 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-03-05 19:52:59.816 Seem to be woken up by USER
2009-03-05 19:54:16.785 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-05 20:06:23.430 Using runtime prefix = /usr
2009-03-05 20:06:23.494 Empty LocalHostName.
2009-03-05 20:06:23.500 Using localhost value of beholder
2009-03-05 20:06:23.564 New DB connection, total: 1
2009-03-05 20:06:23.595 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:23.659 Closing DB connection named 'DBManager0'
2009-03-05 20:06:23.684 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:23.688 New DB connection, total: 2
2009-03-05 20:06:23.711 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:23.733 Current Schema Version: 1214
Starting up as the master server.
2009-03-05 20:06:23.938 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-03-05 20:06:23.946 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-03-05 20:06:23.987 New DB connection, total: 3
2009-03-05 20:06:24.005 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:24.046 DVBChan(2:0) Error: SetChannelByString(2): Failed to initialize multiplex options
2009-03-05 20:06:24.074 New DB scheduler connection
2009-03-05 20:06:24.091 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:24.140 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-03-05 20:06:24.166 Main::Registering HttpStatus Extension
2009-03-05 20:06:24.168 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 20:06:24.175 Enabled verbose msgs:  important general
2009-03-05 20:06:24.223 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-05 20:06:27.102 Reschedule requested for id -1.
2009-03-05 20:06:27.120 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-03-05 20:06:27.126 Seem to be woken up by USER
2009-03-05 20:07:44.102 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
SIP listening on IP Address 192.168.0.102:5060 NAT address 192.168.0.102
SIP: Cannot register; proxy, username or password not set
2009-03-05 19:30:50.168 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 19:32:26.415 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-05 19:32:26.416 Using protocol version 40
Destroying SipFsm object 
2009-03-05 19:32:27.607 Deleting UPnP client...
Starting mythfrontend.real..
2009-03-05 19:40:32.246 New DB connection, total: 2
2009-03-05 19:40:32.246 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:40:32.247 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 19:40:32.247 Enabled verbose msgs:  important general
2009-03-05 19:40:34.468 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 19:40:34.469 Primary screen 0.
2009-03-05 19:40:34.469 Using screen 0, 1920x1080 at 0,0
2009-03-05 19:40:34.470 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 19:40:34.470 Switching to square mode (Mythbuntu-8.04)
2009-03-05 19:40:34.628 Using the Qt painter
2009-03-05 19:40:34.628 JoystickMenuClient Error: Joystick disabled - Failed to read /home/marquarc/.mythtv/joystickmenurc
2009-03-05 19:40:34.629 lirc init success using configuration file: /home/marquarc/.mythtv/lircrc
2009-03-05 19:40:35.946 Specified base font 'medium' does not exist for font clock
2009-03-05 19:40:35.946 Specified base font 'medium' does not exist for font small
2009-03-05 19:40:35.946 Specified base font 'medium' does not exist for font medium
2009-03-05 19:40:35.946 Specified base font 'medium' does not exist for font large
2009-03-05 19:40:35.946 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-03-05 19:40:36.101 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-05 19:40:36.154 Registering Internal as a media playback plugin.
2009-03-05 19:40:36.243 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-05 19:40:36.442 Failed to run 'cdrecord --scanbus'
2009-03-05 19:40:36.444 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-05 19:40:36.447 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-05 19:40:36.465 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.102:5060 NAT address 192.168.0.102
SIP: Cannot register; proxy, username or password not set
2009-03-05 19:40:36.622 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 19:45:04.753 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-05 19:45:04.754 Using protocol version 40
Destroying SipFsm object 
2009-03-05 19:45:06.557 Deleting UPnP client...
Starting mythfrontend.real..
2009-03-05 19:53:06.335 New DB connection, total: 2
2009-03-05 19:53:06.339 Connected to database 'mythconverg' at host: localhost
2009-03-05 19:53:06.340 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 19:53:06.341 Enabled verbose msgs:  important general
2009-03-05 19:53:09.045 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 19:53:09.046 Primary screen 0.
2009-03-05 19:53:09.046 Using screen 0, 1920x1080 at 0,0
2009-03-05 19:53:09.046 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 19:53:09.047 Switching to square mode (Mythbuntu-8.04)
2009-03-05 19:53:09.158 Using the Qt painter
2009-03-05 19:53:09.159 JoystickMenuClient Error: Joystick disabled - Failed to read /home/marquarc/.mythtv/joystickmenurc
2009-03-05 19:53:09.160 lirc init success using configuration file: /home/marquarc/.mythtv/lircrc
2009-03-05 19:53:10.574 Specified base font 'medium' does not exist for font clock
2009-03-05 19:53:10.574 Specified base font 'medium' does not exist for font small
2009-03-05 19:53:10.574 Specified base font 'medium' does not exist for font medium
2009-03-05 19:53:10.574 Specified base font 'medium' does not exist for font large
2009-03-05 19:53:10.575 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-03-05 19:53:10.716 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-05 19:53:10.770 Registering Internal as a media playback plugin.
2009-03-05 19:53:10.869 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-05 19:53:11.058 Failed to run 'cdrecord --scanbus'
2009-03-05 19:53:11.060 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-05 19:53:11.062 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-05 19:53:11.080 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.102:5060 NAT address 192.168.0.102
SIP: Cannot register; proxy, username or password not set
2009-03-05 19:53:11.209 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done

Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       

Reading state information... 0%

Reading state information... 0%

Reading state information... Done
 * Stopping MythTV server: mythbackend 
   ...done.
Starting mythfrontend.real..
2009-03-05 20:06:33.970 New DB connection, total: 2
2009-03-05 20:06:33.970 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:33.972 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-05 20:06:33.972 Enabled verbose msgs:  important general
2009-03-05 20:06:36.427 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 20:06:36.428 Primary screen 0.
2009-03-05 20:06:36.428 Using screen 0, 1920x1080 at 0,0
2009-03-05 20:06:36.428 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04
2009-03-05 20:06:36.429 Switching to square mode (Mythbuntu-8.04)
2009-03-05 20:06:36.553 Using the Qt painter
2009-03-05 20:06:36.554 lirc init success using configuration file: /home/marquarc/.mythtv/lircrc
2009-03-05 20:06:36.554 JoystickMenuClient Error: Joystick disabled - Failed to read /home/marquarc/.mythtv/joystickmenurc
2009-03-05 20:06:38.006 Specified base font 'medium' does not exist for font clock
2009-03-05 20:06:38.006 Specified base font 'medium' does not exist for font small
2009-03-05 20:06:38.007 Specified base font 'medium' does not exist for font medium
2009-03-05 20:06:38.007 Specified base font 'medium' does not exist for font large
2009-03-05 20:06:38.007 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-03-05 20:06:38.148 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-05 20:06:38.201 Registering Internal as a media playback plugin.
2009-03-05 20:06:38.300 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-05 20:06:38.489 Failed to run 'cdrecord --scanbus'
2009-03-05 20:06:38.491 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-05 20:06:38.492 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-05 20:06:38.510 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.102:5060 NAT address 192.168.0.102
SIP: Cannot register; proxy, username or password not set
2009-03-05 20:06:38.640 No theme dir: /home/marquarc/.mythtv/themes/Mythbuntu-8.04

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Mar  5 20:06:25 beholder bluetoothd[5371]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar  5 20:06:25 beholder kernel: [   24.670584] Bluetooth: RFCOMM socket layer initialized
Mar  5 20:06:25 beholder kernel: [   24.670600] Bluetooth: RFCOMM TTY layer initialized
Mar  5 20:06:25 beholder kernel: [   24.670602] Bluetooth: RFCOMM ver 1.10
Mar  5 20:06:25 beholder ntpd_initres[5174]: couldn't resolve `ntp.ubuntu.com', giving up on it
Mar  5 20:06:25 beholder NetworkManager: <info>  starting... 
Mar  5 20:06:25 beholder NetworkManager: <info>  eth0: driver is 'r8169'. 
Mar  5 20:06:25 beholder NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar  5 20:06:25 beholder NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1f_d0_d7_8e_36 
Mar  5 20:06:25 beholder NetworkManager: <info>  Trying to start the supplicant... 
Mar  5 20:06:25 beholder NetworkManager: <info>  Trying to start the system settings daemon... 
Mar  5 20:06:25 beholder nm-system-settings:    SCPlugin-Ifupdown: init!
Mar  5 20:06:25 beholder nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar  5 20:06:25 beholder nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar  5 20:06:25 beholder nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_1f_d0_d7_8e_36, iface: eth0)
Mar  5 20:06:25 beholder nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar  5 20:06:25 beholder nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar  5 20:06:25 beholder nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar  5 20:06:25 beholder nm-system-settings:    SCPlugin-Ifupdown: (163465968) ... get_connections.
Mar  5 20:06:25 beholder nm-system-settings:    SCPlugin-Ifupdown: (163465968) connections count: 0
Mar  5 20:06:25 beholder nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Mar  5 20:06:27 beholder gdm[5466]: WARNING: Didn't understand `' (expected true or false) 
Mar  5 20:06:27 beholder acpid: client connected from 5474[0:0] 
Mar  5 20:06:27 beholder kernel: [   26.504578] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Mar  5 20:06:28 beholder /usr/sbin/cron[5572]: (CRON) INFO (pidfile fd = 3)
Mar  5 20:06:28 beholder /usr/sbin/cron[5573]: (CRON) STARTUP (fork ok)
Mar  5 20:06:28 beholder /usr/sbin/cron[5573]: (CRON) INFO (Running @reboot jobs)
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): bringing up device. 
Mar  5 20:06:29 beholder kernel: [   28.756446] r8169: eth0: link up
Mar  5 20:06:29 beholder kernel: [   28.756456] r8169: eth0: link up
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): preparing device. 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Mar  5 20:06:29 beholder nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1f_d0_d7_8e_36
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar  5 20:06:29 beholder NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar  5 20:06:29 beholder NetworkManager: <info>  dhclient started with pid 5762 
Mar  5 20:06:29 beholder NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar  5 20:06:29 beholder dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar  5 20:06:29 beholder dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar  5 20:06:29 beholder dhclient: All rights reserved.
Mar  5 20:06:29 beholder dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar  5 20:06:29 beholder dhclient: 
Mar  5 20:06:29 beholder NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Mar  5 20:06:29 beholder kernel: [   29.017893] NET: Registered protocol family 17
Mar  5 20:06:29 beholder dhclient: Listening on LPF/eth0/00:1f:d0:d7:8e:36
Mar  5 20:06:29 beholder dhclient: Sending on   LPF/eth0/00:1f:d0:d7:8e:36
Mar  5 20:06:29 beholder dhclient: Sending on   Socket/fallback
Mar  5 20:06:30 beholder dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar  5 20:06:30 beholder dhclient: DHCPOFFER of 192.168.0.102 from 192.168.0.1
Mar  5 20:06:30 beholder dhclient: DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
Mar  5 20:06:30 beholder dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Mar  5 20:06:30 beholder dhclient: bound to 192.168.0.102 -- renewal in 278695 seconds.
Mar  5 20:06:30 beholder NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Mar  5 20:06:30 beholder NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar  5 20:06:30 beholder NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar  5 20:06:30 beholder NetworkManager: <info>    address 192.168.0.102 
Mar  5 20:06:30 beholder NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar  5 20:06:30 beholder NetworkManager: <info>    gateway 192.168.0.1 
Mar  5 20:06:30 beholder NetworkManager: <info>    nameserver '192.168.0.1' 
Mar  5 20:06:30 beholder NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar  5 20:06:30 beholder NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar  5 20:06:30 beholder NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar  5 20:06:30 beholder avahi-daemon[4688]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Mar  5 20:06:30 beholder avahi-daemon[4688]: New relevant interface eth0.IPv4 for mDNS.
Mar  5 20:06:30 beholder avahi-daemon[4688]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Mar  5 20:06:31 beholder NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Mar  5 20:06:31 beholder NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Mar  5 20:06:31 beholder NetworkManager: <info>  Activation (eth0) successful, device activated. 
Mar  5 20:06:31 beholder NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar  5 20:06:31 beholder avahi-daemon[4688]: Registering new address record for fe80::21f:d0ff:fed7:8e36 on eth0.*.
Mar  5 20:06:31 beholder ntpd[5150]: ntpd exiting on signal 15
Mar  5 20:06:31 beholder ntpdate[5857]: adjust time server 91.189.94.4 offset 0.013972 sec
Mar  5 20:06:32 beholder ntpd[5900]: ntpd 4.2.4p4@1.1520-o Wed Aug 20 17:03:52 UTC 2008 (1)
Mar  5 20:06:32 beholder ntpd[5901]: precision = 1.000 usec
Mar  5 20:06:32 beholder ntpd[5901]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar  5 20:06:32 beholder ntpd[5901]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Mar  5 20:06:32 beholder ntpd[5901]: Listening on interface #2 eth0, 192.168.0.102#123 Enabled
Mar  5 20:06:32 beholder ntpd[5901]: kernel time sync status 0040
Mar  5 20:06:32 beholder ntpd[5901]: frequency initialized -16.602 PPM from /var/lib/ntp/ntp.drift
Mar  5 20:06:32 beholder ntpd[5901]: getaddrinfo: "::1" invalid host address, ignored
Mar  5 20:06:36 beholder lircd-0.8.3[3661]: accepted new client on /dev/lircd
Mar  5 20:06:40 beholder kernel: [   39.316014] eth0: no IPv6 routers present
Mar  5 20:09:01 beholder /USR/SBIN/CRON[5995]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Mar  5 20:10:53 beholder ntpd[5901]: synchronized to 91.189.94.4, stratum 2
Mar  5 20:10:53 beholder ntpd[5901]: kernel time sync status change 0001

==> /var/log/Xorg.0.log <==
(II) RADEON(0): Ranges: V min: 48 V max: 88 Hz, H min: 31 H max: 100 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: LG TV
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d010001010101
(II) RADEON(0): 	00110103807341960acf74a3574cb023
(II) RADEON(0): 	09484cafcf003140454061408180a940
(II) RADEON(0): 	010101010101023a801871382d40582c
(II) RADEON(0): 	4500c48e2100001e662150b051001b30
(II) RADEON(0): 	40703600c48e2100001e000000fd0030
(II) RADEON(0): 	581f6411000a202020202020000000fc
(II) RADEON(0): 	004c472054560a20202020202020018a
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "GSM", prod id 1
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "GSM", prod id 1
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   23.86  640 656 720 800  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) RADEON(0): Modeline "800x600"x60.0   38.22  800 832 912 1024  600 601 604 622 -hsync +vsync (37.3 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   64.11  1024 1080 1184 1344  768 769 772 795 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: GSM  Model: 1  Serial#: 16843009
(II) RADEON(0): Year: 2007  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 115  vert.: 65
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.300 greenY: 0.690
(II) RADEON(0): blueX: 0.138 blueY: 0.038   whiteX: 0.282 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 85.5 MHz   Image Size:  708 x 398 mm
(II) RADEON(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 88 Hz, H min: 31 H max: 100 kHz, PixClock max 170 MHz
(II) RADEON(0): Monitor name: LG TV
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff001e6d010001010101
(II) RADEON(0): 	00110103807341960acf74a3574cb023
(II) RADEON(0): 	09484cafcf003140454061408180a940
(II) RADEON(0): 	010101010101023a801871382d40582c
(II) RADEON(0): 	4500c48e2100001e662150b051001b30
(II) RADEON(0): 	40703600c48e2100001e000000fd0030
(II) RADEON(0): 	581f6411000a202020202020000000fc
(II) RADEON(0): 	004c472054560a20202020202020018a
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "GSM", prod id 1
(II) RADEON(0): Output: None, Detected Monitor Type: 0
Dac detection success

==> /home/marquarc/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2009-03-05 20:06:29.630 Using runtime prefix = /usr
2009-03-05 20:06:29.637 Empty LocalHostName.
2009-03-05 20:06:29.637 Using localhost value of beholder
/usr/bin/startxfce4: X server already running on display :0
2009-03-05 20:06:29.671 New DB connection, total: 1
2009-03-05 20:06:29.675 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:29.676 Closing DB connection named 'DBManager0'
2009-03-05 20:06:29.676 Connected to database 'mythconverg' at host: localhost
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-QMYzMy5640/agent.5640
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2009-03-05 20:06:33.286 Using runtime prefix = /usr

** (nm-applet:5925): WARNING **: No connections defined
2009-03-05 20:06:33.860 XScreenSaver support enabled
2009-03-05 20:06:33.860 DPMS is active.
2009-03-05 20:06:33.860 Empty LocalHostName.
2009-03-05 20:06:33.860 Using localhost value of beholder
2009-03-05 20:06:33.874 New DB connection, total: 1
2009-03-05 20:06:33.878 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:33.879 Closing DB connection named 'DBManager0'
2009-03-05 20:06:33.880 Primary screen 0.
2009-03-05 20:06:33.880 Connected to database 'mythconverg' at host: localhost
2009-03-05 20:06:33.881 Using screen 0, 1920x1080 at 0,0

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.3G  8.3G  22% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  364K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  2.8M  1.4G   1% /dev
tmpfs                 1.4G     0  1.4G   0% /dev/shm
lrm                   1.4G  2.0M  1.4G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6             920G  172M  920G   1% /var/lib

==> uname -a <==
Linux beholder 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

==> lsusb <==
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00f6 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1784:0001 TopSeed Technology Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

==> lshw <==
computer
    description: Desktop Computer
    product: GA-MA78GM-US2H
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303146-4430-4437-3845-3336FFFFFFFF
  *-core
       description: Motherboard
       product: GA-MA78GM-US2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2 (01/02/2009)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) Dual Core Processor 5050e
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.2
          slot: Socket M2
          size: 2600MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cache:0
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-cache:1 DISABLED
          description: L2 cache
          physical id: d
          slot: External Cache
          capacity: 1MiB
          capabilities: synchronous internal write-through
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: [REMOVED]
             slot: A2
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns) [empty]
             product: None
             vendor: None
             physical id: 3
             serial: [REMOVED]
             slot: A3
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.11.2
          size: 18EHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon HD 3200 Graphics
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=0
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-multimedia
                description: Multimedia video controller
                product: Conexant Systems, Inc.
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 0f
                width: 64 bits
                clock: 33MHz
                capabilities: pciexpress pm vpd msi bus_master cap_list
                configuration: driver=cx23885 latency=0 module=cx23885
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi1
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=32 module=ahci
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22NS30
                vendor: HL-DT-ST
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: WDC WD10EADS-00L
                vendor: Western Digital
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: [REMOVED]
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b44ef
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
                   configuration: created=2009-03-04 18:31:26 filesystem=ext3 modified=2009-03-05 20:00:11 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-03-05 19:52:46 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 920GiB
                   capacity: 920GiB
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
                      capacity: 919GiB
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=32 module=pata_atiixp
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:04:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
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

Any help, pointers, or comments will be greatly appreciated!

---

### Post by marquarc on 2009-03-15
I don't mean to dredge up a dead thread, but I really want to post the cause of this channel scan freeze. I don't know how to change the thread title to SOLVED, or I would. It was a pretty simple fix, but it took me a long time to figure it out. The simple answer is that I needed the firmware for the card. Here's how I fixed it in case anyone else has the same problem:

1. Download the firmware here: [http://steventoth.net/linux/hvr1800/](http://steventoth.net/linux/hvr1800/) - You need the .zip and the .sh files.
2. Make sure you have the zip package. 
```

sudo apt-get install zip

```
3. extract the package
```

sudo sh extract.sh

```
4. That's going to extract two .fw files. You then need to copy these to, I believe, the /lib/firmware/[kernel version] folder. It will tell you onscreen exactly where to copy them and what the command is. 
5. Reboot

That's all it took for me to get the channel scan to work. I still had video problems, but those were mostly solved by switching to the latest ATI proprietary driver. For others who have the WinTV-HVR-1800 card and need more help, I highly recommend this thread over here:

[http://ubuntuforums.org/showthread.php?p=6129026#post6129026](http://ubuntuforums.org/showthread.php?p=6129026#post6129026)

It's a long thread, but there is a lot of good information in there if you take the time to read it. Hope this helps somebody out there!

---

