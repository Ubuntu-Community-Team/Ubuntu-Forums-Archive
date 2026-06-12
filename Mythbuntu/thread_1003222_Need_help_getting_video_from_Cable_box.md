---
title: "Need help getting video from Cable box"
date: 2008-12-05
forum: Mythbuntu
---

### Post by rschapman on 2008-12-05
I was using Mythbuntu 8.04 with my Scientific Atlantic 4240HDC cable box with intermittent success. I upgraded to Mythbuntu 8.10 and it has not worked at all. I set up my backend to use all of the related cable box types, point-to-point, broadcast, 100mb and 400 mb, and still can't get any video. Below is an link to an image of the error I get every time and the relevant error log. Thanks for your help. 

[Error Image]("http://drop.io/hidden/xx3gh1jcjbeyrl/asset/ZXJyb3I=")

[HTML]==> /var/log/mythtv/mtd.log <==
mtd started at Thu Dec 4 18:15:50 2008
mtd is running on a host called mythbox
18:15:50: Waiting for connections/jobs
18:15:50: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2008-12-04 18:17:29.699 LFireDev(001E6B86A1140000), Warning: No Input in 100 msec...
2008-12-04 18:17:29.755 LFireDev(001E6B86A1140000), Warning: No Input in 150 msec...
2008-12-04 18:17:29.815 LFireDev(001E6B86A1140000), Warning: No Input in 200 msec...
2008-12-04 18:17:29.867 LFireDev(001E6B86A1140000), Warning: No Input in 250 msec...
2008-12-04 18:17:29.919 LFireDev(001E6B86A1140000), Warning: No Input in 300 msec...
2008-12-04 18:17:29.971 LFireDev(001E6B86A1140000), Warning: No Input in 350 msec...
2008-12-04 18:17:30.028 LFireDev(001E6B86A1140000), Warning: No Input in 400 msec...
2008-12-04 18:17:30.079 LFireDev(001E6B86A1140000), Warning: No Input in 450 msec...
2008-12-04 18:17:30.135 LFireDev(001E6B86A1140000), Warning: No Input in 500 msec...
2008-12-04 18:17:30.187 LFireDev(001E6B86A1140000), Warning: No Input in 550 msec...
2008-12-04 18:17:30.239 LFireDev(001E6B86A1140000), Warning: No Input in 600 msec...
2008-12-04 18:17:30.291 LFireDev(001E6B86A1140000), Warning: No Input in 650 msec...
2008-12-04 18:17:30.343 LFireDev(001E6B86A1140000), Warning: No Input in 700 msec...
2008-12-04 18:17:30.395 LFireDev(001E6B86A1140000), Warning: No Input in 750 msec...
2008-12-04 18:17:30.447 LFireDev(001E6B86A1140000), Warning: No Input in 800 msec...
2008-12-04 18:17:30.499 LFireDev(001E6B86A1140000), Warning: No Input in 850 msec...
2008-12-04 18:17:30.551 LFireDev(001E6B86A1140000), Warning: No Input in 900 msec...
2008-12-04 18:17:30.603 LFireDev(001E6B86A1140000), Warning: No Input in 950 msec...
2008-12-04 18:17:30.655 LFireDev(001E6B86A1140000), Warning: No Input in 1000 msec...
2008-12-04 18:17:30.707 LFireDev(001E6B86A1140000), Warning: No Input in 1050 msec...
2008-12-04 18:17:30.708 LFireDev(001E6B86A1140000): ResetBus() -- begin
2008-12-04 18:17:30.710 LFireDev(001E6B86A1140000): ResetBus() -- end
2008-12-04 18:17:30.712 LFireDev(001E6B86A1140000): SignalReset(74->75)
2008-12-04 18:17:30.713 LFireDev(001E6B86A1140000): SignalReset(74->75): Updating device list -- begin
2008-12-04 18:17:30.721 LFireDev(001E6B86A1140000): SignalReset(74->75): Updating device list -- end
2008-12-04 18:17:30.728 LFireDev(001E6B86A1140000): SignalReset(75->76)
2008-12-04 18:17:30.736 LFireDev(001E6B86A1140000): SignalReset(75->76): Updating device list -- begin
2008-12-04 18:17:30.745 LFireDev(001E6B86A1140000): SignalReset(75->76): Updating device list -- end
2008-12-04 18:17:30.807 LFireDev(001E6B86A1140000), Warning: No Input in 50 msec...
2008-12-04 18:17:30.859 LFireDev(001E6B86A1140000), Warning: No Input in 100 msec...
2008-12-04 18:17:30.917 LFireDev(001E6B86A1140000), Warning: No Input in 150 msec...
2008-12-04 18:17:30.967 LFireDev(001E6B86A1140000), Warning: No Input in 200 msec...
2008-12-04 18:17:31.019 LFireDev(001E6B86A1140000), Warning: No Input in 250 msec...
2008-12-04 18:17:31.071 LFireDev(001E6B86A1140000), Warning: No Input in 300 msec...
2008-12-04 18:17:31.123 LFireDev(001E6B86A1140000), Warning: No Input in 350 msec...
2008-12-04 18:17:31.175 LFireDev(001E6B86A1140000), Warning: No Input in 400 msec...
2008-12-04 18:17:31.227 LFireDev(001E6B86A1140000), Warning: No Input in 450 msec...
2008-12-04 18:17:31.279 LFireDev(001E6B86A1140000), Warning: No Input in 500 msec...
2008-12-04 18:17:31.331 LFireDev(001E6B86A1140000), Warning: No Input in 550 msec...
2008-12-04 18:17:31.386 LFireDev(001E6B86A1140000), Warning: No Input in 600 msec...
2008-12-04 18:17:31.435 LFireDev(001E6B86A1140000), Warning: No Input in 650 msec...
2008-12-04 18:17:31.487 LFireDev(001E6B86A1140000), Warning: No Input in 700 msec...
2008-12-04 18:17:31.539 LFireDev(001E6B86A1140000), Warning: No Input in 750 msec...
2008-12-04 18:17:31.591 LFireDev(001E6B86A1140000), Warning: No Input in 800 msec...
2008-12-04 18:17:31.643 LFireDev(001E6B86A1140000), Warning: No Input in 850 msec...
2008-12-04 18:17:31.699 LFireDev(001E6B86A1140000), Warning: No Input in 900 msec...
2008-12-04 18:17:31.751 LFireDev(001E6B86A1140000), Warning: No Input in 950 msec...
2008-12-04 18:17:31.803 LFireDev(001E6B86A1140000), Warning: No Input in 1000 msec...
2008-12-04 18:17:31.855 LFireDev(001E6B86A1140000), Warning: No Input in 1050 msec...
2008-12-04 18:17:31.856 LFireDev(001E6B86A1140000): ResetBus() -- begin
2008-12-04 18:17:31.858 LFireDev(001E6B86A1140000): ResetBus() -- end
2008-12-04 18:17:31.862 LFireDev(001E6B86A1140000): SignalReset(76->77)
2008-12-04 18:17:31.868 LFireDev(001E6B86A1140000): SignalReset(76->77): Updating device list -- begin
2008-12-04 18:17:31.877 LFireDev(001E6B86A1140000): SignalReset(76->77): Updating device list -- end
2008-12-04 18:17:31.888 LFireDev(001E6B86A1140000): SignalReset(77->78)
2008-12-04 18:17:31.896 LFireDev(001E6B86A1140000): SignalReset(77->78): Updating device list -- begin
2008-12-04 18:17:31.905 LFireDev(001E6B86A1140000): SignalReset(77->78): Updating device list -- end
2008-12-04 18:17:31.963 LFireDev(001E6B86A1140000), Warning: No Input in 50 msec...
2008-12-04 18:17:32.015 LFireDev(001E6B86A1140000), Warning: No Input in 100 msec...
2008-12-04 18:17:32.071 LFireDev(001E6B86A1140000), Warning: No Input in 150 msec...
2008-12-04 18:17:32.123 LFireDev(001E6B86A1140000), Warning: No Input in 200 msec...
2008-12-04 18:17:32.175 LFireDev(001E6B86A1140000), Warning: No Input in 250 msec...
2008-12-04 18:17:32.227 LFireDev(001E6B86A1140000), Warning: No Input in 300 msec...
2008-12-04 18:17:32.279 LFireDev(001E6B86A1140000), Warning: No Input in 350 msec...
2008-12-04 18:17:32.331 LFireDev(001E6B86A1140000), Warning: No Input in 400 msec...
2008-12-04 18:17:32.383 LFireDev(001E6B86A1140000), Warning: No Input in 450 msec...
2008-12-04 18:17:32.435 LFireDev(001E6B86A1140000), Warning: No Input in 500 msec...
2008-12-04 18:17:32.487 LFireDev(001E6B86A1140000), Warning: No Input in 550 msec...
2008-12-04 18:17:32.539 LFireDev(001E6B86A1140000), Warning: No Input in 600 msec...
2008-12-04 18:17:32.591 LFireDev(001E6B86A1140000), Warning: No Input in 650 msec...
2008-12-04 18:17:32.643 LFireDev(001E6B86A1140000), Warning: No Input in 700 msec...
2008-12-04 18:17:32.695 LFireDev(001E6B86A1140000), Warning: No Input in 750 msec...
2008-12-04 18:17:32.747 LFireDev(001E6B86A1140000), Warning: No Input in 800 msec...
2008-12-04 18:17:32.800 LFireDev(001E6B86A1140000), Warning: No Input in 850 msec...
2008-12-04 18:17:32.851 LFireDev(001E6B86A1140000), Warning: No Input in 900 msec...
2008-12-04 18:17:32.903 LFireDev(001E6B86A1140000), Warning: No Input in 950 msec...
2008-12-04 18:17:32.955 LFireDev(001E6B86A1140000), Warning: No Input in 1000 msec...
2008-12-04 18:17:33.007 LFireDev(001E6B86A1140000), Warning: No Input in 1050 msec...
2008-12-04 18:17:33.016 LFireDev(001E6B86A1140000): ResetBus() -- begin
2008-12-04 18:17:33.018 LFireDev(001E6B86A1140000): ResetBus() -- end
2008-12-04 18:17:33.019 LFireDev(001E6B86A1140000): SignalReset(78->79)
2008-12-04 18:17:33.024 LFireDev(001E6B86A1140000): SignalReset(78->79): Updating device list -- begin
2008-12-04 18:17:33.033 LFireDev(001E6B86A1140000): SignalReset(78->79): Updating device list -- end
2008-12-04 18:17:33.040 LFireDev(001E6B86A1140000): SignalReset(79->80)
2008-12-04 18:17:33.048 LFireDev(001E6B86A1140000): SignalReset(79->80): Updating device list -- begin
2008-12-04 18:17:33.057 LFireDev(001E6B86A1140000): SignalReset(79->80): Updating device list -- end
2008-12-04 18:17:33.119 LFireDev(001E6B86A1140000), Warning: No Input in 50 msec...
2008-12-04 18:17:33.171 LFireDev(001E6B86A1140000), Warning: No Input in 100 msec...
2008-12-04 18:17:33.227 LFireDev(001E6B86A1140000), Warning: No Input in 150 msec...
2008-12-04 18:17:33.279 LFireDev(001E6B86A1140000), Warning: No Input in 200 msec...
2008-12-04 18:17:33.335 LFireDev(001E6B86A1140000), Warning: No Input in 250 msec...
2008-12-04 18:17:33.388 LFireDev(001E6B86A1140000), Warning: No Input in 300 msec...
2008-12-04 18:17:33.439 LFireDev(001E6B86A1140000), Warning: No Input in 350 msec...
2008-12-04 18:17:33.491 LFireDev(001E6B86A1140000), Warning: No Input in 400 msec...
2008-12-04 18:17:33.543 LFireDev(001E6B86A1140000), Warning: No Input in 450 msec...
2008-12-04 18:17:33.589 TVRec(2): Changing from WatchingLiveTV to None
2008-12-04 18:17:33.603 LFireDev(001E6B86A1140000), Warning: No Input in 500 msec...
2008-12-04 18:17:33.659 LFireDev(001E6B86A1140000), Warning: No Input in 550 msec...
2008-12-04 18:17:33.707 Finished recording Deal or No Deal: channel 1011
2008-12-04 18:17:33.711 scheduler: Finished recording: Deal or No Deal: channel 1011

==> /var/log/mythtv/mythfrontend.log <==
2008-12-04 18:13:11.589 Using protocol version 40
2008-12-04 18:13:19.214 RingBuf(/var/lib/mythtv/recordings/1002_20081204181311.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1002_20081204181311.mpg'.
2008-12-04 18:13:19.231 NVP: Disabling Audio, params(-1,2,44100)
2008-12-04 18:13:19.257 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-12-04 18:13:19.263 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-04 18:13:19.366 OSD Theme Dimensions W: 640 H: 480
2008-12-04 18:13:20.323 LiveTVChain(live-mythbox-2008-12-04T18:12:57): SwitchTo() not switching to current
2008-12-04 18:13:20.325 FilterManager: failed to load filter 'none', no such filter exists
2008-12-04 18:13:20.325 Couldn't load deinterlace filter none
2008-12-04 18:13:20.335 Realtime priority would require SUID as root.
2008-12-04 18:13:20.427 OpenGLVideoSync()
2008-12-04 18:13:20.479 Video timing method: SGI OpenGL
2008-12-04 18:13:37.705 New DB connection, total: 4
2008-12-04 18:13:37.711 Connected to database 'mythconverg' at host: localhost
2008-12-04 18:13:50.386 TV: Attempting to change from WatchingLiveTV to None
2008-12-04 18:13:50.493 ~OpenGLVideoSync() -- begin
2008-12-04 18:13:50.494 ~OpenGLVideoSync() -- middle
2008-12-04 18:13:50.494 ~OpenGLVideoSync() -- end
2008-12-04 18:13:50.627 TV: Changing from WatchingLiveTV to None
2008-12-04 18:13:50.718 DPMS Reactivated.
2008-12-04 18:13:52.041 No theme dir: /home/mythbox/.mythtv/themes/blootube-wide
2008-12-04 18:13:59.979 No theme dir: /home/mythbox/.mythtv/themes/blootube-wide
2008-12-04 18:14:10.798 Deleting UPnP client...
Starting mythfrontend.real..
2008-12-04 18:16:03.749 New DB connection, total: 2
2008-12-04 18:16:03.753 Connected to database 'mythconverg' at host: localhost
2008-12-04 18:16:03.757 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-04 18:16:03.757 Enabled verbose msgs:  important general
2008-12-04 18:16:07.581 No theme dir: /home/mythbox/.mythtv/themes/blootube-wide
2008-12-04 18:16:07.584 Primary screen 0.
2008-12-04 18:16:07.584 Using screen 0, 1920x1080 at 0,0
2008-12-04 18:16:07.586 No theme dir: /home/mythbox/.mythtv/themes/blootube-wide
2008-12-04 18:16:07.587 Switching to wide mode (blootube-wide)
2008-12-04 18:16:07.627 Using the Qt painter
2008-12-04 18:16:07.632 lirc init success using configuration file: /home/mythbox/.mythtv/lircrc
2008-12-04 18:16:07.632 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythbox/.mythtv/joystickmenurc
2008-12-04 18:16:10.202 Specified base font 'medium' does not exist for font clock
2008-12-04 18:16:10.202 Specified base font 'medium' does not exist for font small
2008-12-04 18:16:10.202 Specified base font 'medium' does not exist for font medium
2008-12-04 18:16:10.203 Specified base font 'medium' does not exist for font large
2008-12-04 18:16:10.204 Loading from: /usr/share/mythtv/themes/blootube-wide/base.xml
2008-12-04 18:16:10.395 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-04 18:16:10.572 Registering Internal as a media playback plugin.
2008-12-04 18:16:10.777 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-12-04 18:16:11.110 Failed to run 'cdrecord --scanbus'
2008-12-04 18:16:11.114 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-12-04 18:16:11.119 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-12-04 18:16:11.193 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-12-04 18:16:11.453 Starting update of NWS-XML
2008-12-04 18:16:11.461 Starting update of NDFD-6_day
2008-12-04 18:16:11.485 NetworkControl: Listening for remote connections on port 6546
2008-12-04 18:16:11.490 No theme dir: /home/mythbox/.mythtv/themes/blootube-wide
2008-12-04 18:16:21.934 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/mythbox/.mythtv/MythWeather/NWS-XML KSAT has exited
2008-12-04 18:16:23.246 Connecting to backend server: 192.168.2.147:6543 (try 1 of 5)
2008-12-04 18:16:23.265 Using protocol version 40
2008-12-04 18:16:23.349 TV: Attempting to change from None to WatchingLiveTV
2008-12-04 18:16:23.351 Using protocol version 40
2008-12-04 18:16:25.432 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/mythbox/.mythtv/MythWeather/NDFD-6_day +29.31,-098.27 has exited
2008-12-04 18:16:26.737 DPMS Deactivated 
2008-12-04 18:16:26.807 New DB connection, total: 3
2008-12-04 18:16:26.810 Connected to database 'mythconverg' at host: localhost
2008-12-04 18:16:27.687 AFD: Opened codec 0x9416b30, id(MPEG2VIDEO) type(Video)
2008-12-04 18:16:27.688 AFD: codec MP2 has 2 channels
2008-12-04 18:16:27.688 AFD: Opened codec 0x93c0420, id(MP2) type(Audio)
2008-12-04 18:16:27.872 Opening audio device 'default'. ch 2(2) sr 48000
2008-12-04 18:16:27.872 Opening ALSA audio device 'default'.
2008-12-04 18:16:28.146 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-12-04 18:16:28.152 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-04 18:16:28.392 OSD Theme Dimensions W: 640 H: 480
2008-12-04 18:16:29.602 TV: Changing from None to WatchingLiveTV
2008-12-04 18:16:29.619 FilterManager: failed to load filter 'none', no such filter exists
2008-12-04 18:16:29.619 Couldn't load deinterlace filter none
2008-12-04 18:16:29.623 Realtime priority would require SUID as root.
2008-12-04 18:16:29.723 OpenGLVideoSync()
2008-12-04 18:16:29.942 Video timing method: SGI OpenGL
2008-12-04 18:16:35.296 ~OpenGLVideoSync() -- begin
2008-12-04 18:16:35.296 ~OpenGLVideoSync() -- middle
2008-12-04 18:16:35.297 ~OpenGLVideoSync() -- end
2008-12-04 18:16:35.782 Using protocol version 40
2008-12-04 18:16:43.457 RingBuf(/var/lib/mythtv/recordings/1002_20081204181635.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1002_20081204181635.mpg'.
2008-12-04 18:16:43.473 NVP: Disabling Audio, params(-1,2,44100)
2008-12-04 18:16:43.497 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-12-04 18:16:43.503 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-04 18:16:43.630 OSD Theme Dimensions W: 640 H: 480
2008-12-04 18:16:44.426 FilterManager: failed to load filter 'none', no such filter exists
2008-12-04 18:16:44.426 Couldn't load deinterlace filter none
2008-12-04 18:16:44.439 Realtime priority would require SUID as root.
2008-12-04 18:16:44.442 LiveTVChain(live-mythbox-2008-12-04T18:16:23): SwitchTo() not switching to current
2008-12-04 18:16:44.527 OpenGLVideoSync()
2008-12-04 18:16:44.573 Video timing method: SGI OpenGL
2008-12-04 18:17:33.542 TV: Attempting to change from WatchingLiveTV to None
2008-12-04 18:17:33.715 ~OpenGLVideoSync() -- begin
2008-12-04 18:17:33.715 ~OpenGLVideoSync() -- middle
2008-12-04 18:17:33.716 ~OpenGLVideoSync() -- end
2008-12-04 18:17:33.817 TV: Changing from WatchingLiveTV to None
2008-12-04 18:17:33.896 DPMS Reactivated.
2008-12-04 18:17:39.575 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Dec  4 18:15:43 mythbox NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_c0_a8_7f_75_4b 
Dec  4 18:15:43 mythbox NetworkManager: <info>  Trying to start the supplicant... 
Dec  4 18:15:43 mythbox NetworkManager: <info>  Trying to start the system settings daemon... 
Dec  4 18:15:44 mythbox nm-system-settings:    SCPlugin-Ifupdown: init!
Dec  4 18:15:44 mythbox nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Dec  4 18:15:44 mythbox nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Dec  4 18:15:44 mythbox nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_c0_a8_7f_75_4b, iface: eth0): not well known
Dec  4 18:15:44 mythbox nm-system-settings:    SCPlugin-Ifupdown: end _init.
Dec  4 18:15:44 mythbox nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec  4 18:15:44 mythbox nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec  4 18:15:44 mythbox nm-system-settings:    SCPlugin-Ifupdown: (160219368) ... get_connections.
Dec  4 18:15:44 mythbox nm-system-settings:    SCPlugin-Ifupdown: (160219368) ... get_connections (managed=false): return empty list.
Dec  4 18:15:44 mythbox nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Dec  4 18:15:45 mythbox gdm[5405]: WARNING: Didn't understand `' (expected true or false) 
Dec  4 18:15:45 mythbox acpid: client connected from 5413[0:0] 
Dec  4 18:15:46 mythbox kernel: [   41.571100] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Dec  4 18:15:46 mythbox kernel: [   41.571132] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Dec  4 18:15:46 mythbox kernel: [   41.571178] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
Dec  4 18:15:47 mythbox kernel: [   42.370097] lirc_dev: IR Remote Control driver registered, major 61 
Dec  4 18:15:47 mythbox kernel: [   42.636481] bttv: driver version 0.9.17 loaded
Dec  4 18:15:47 mythbox kernel: [   42.636495] bttv: using 8 buffers with 2080k (520 pages) each for capture
Dec  4 18:15:47 mythbox kernel: [   42.931348] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
Dec  4 18:15:47 mythbox kernel: [   42.959232] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
Dec  4 18:15:47 mythbox kernel: [   42.960557] lirc_dev: lirc_register_plugin: sample_rate: 10
Dec  4 18:15:47 mythbox lircd-0.8.4a[5532]: lircd(default) ready
Dec  4 18:15:47 mythbox NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Dec  4 18:15:47 mythbox NetworkManager: <info>  (eth0): bringing up device. 
Dec  4 18:15:47 mythbox kernel: [   43.328735] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Dec  4 18:15:47 mythbox NetworkManager: <info>  (eth0): preparing device. 
Dec  4 18:15:47 mythbox NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Dec  4 18:15:47 mythbox NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Dec  4 18:15:47 mythbox NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Dec  4 18:15:48 mythbox nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_c0_a8_7f_75_4b
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Dec  4 18:15:48 mythbox NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec  4 18:15:48 mythbox NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec  4 18:15:48 mythbox NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec  4 18:15:48 mythbox NetworkManager: <info>  dhclient started with pid 5549 
Dec  4 18:15:48 mythbox NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec  4 18:15:48 mythbox dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec  4 18:15:48 mythbox dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec  4 18:15:48 mythbox dhclient: All rights reserved.
Dec  4 18:15:48 mythbox dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec  4 18:15:48 mythbox dhclient: 
Dec  4 18:15:48 mythbox NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Dec  4 18:15:48 mythbox kernel: [   43.816880] NET: Registered protocol family 17
Dec  4 18:15:48 mythbox dhclient: Listening on LPF/eth0/00:c0:a8:7f:75:4b
Dec  4 18:15:48 mythbox dhclient: Sending on   LPF/eth0/00:c0:a8:7f:75:4b
Dec  4 18:15:48 mythbox dhclient: Sending on   Socket/fallback
Dec  4 18:15:49 mythbox avahi-daemon[4500]: Registering new address record for fe80::2c0:a8ff:fe7f:754b on eth0.*.
Dec  4 18:15:52 mythbox dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec  4 18:15:52 mythbox dhclient: DHCPOFFER of 192.168.2.147 from 192.168.2.2
Dec  4 18:15:52 mythbox dhclient: DHCPREQUEST of 192.168.2.147 on eth0 to 255.255.255.255 port 67
Dec  4 18:15:52 mythbox dhclient: DHCPACK of 192.168.2.147 from 192.168.2.2
Dec  4 18:15:52 mythbox NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Dec  4 18:15:52 mythbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec  4 18:15:52 mythbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Dec  4 18:15:52 mythbox NetworkManager: <info>    address 192.168.2.147 
Dec  4 18:15:52 mythbox NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec  4 18:15:52 mythbox NetworkManager: <info>    gateway 192.168.2.2 
Dec  4 18:15:52 mythbox NetworkManager: <info>    hostname 'mythbox' 
Dec  4 18:15:52 mythbox NetworkManager: <info>    nameserver '192.168.2.2' 
Dec  4 18:15:52 mythbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec  4 18:15:52 mythbox NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Dec  4 18:15:52 mythbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Dec  4 18:15:52 mythbox avahi-daemon[4500]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.147.
Dec  4 18:15:52 mythbox avahi-daemon[4500]: New relevant interface eth0.IPv4 for mDNS.
Dec  4 18:15:52 mythbox avahi-daemon[4500]: Registering new address record for 192.168.2.147 on eth0.IPv4.
Dec  4 18:15:52 mythbox dhclient: bound to 192.168.2.147 -- renewal in 34496 seconds.
Dec  4 18:15:53 mythbox NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Dec  4 18:15:53 mythbox NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec  4 18:15:53 mythbox NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec  4 18:15:53 mythbox NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec  4 18:15:53 mythbox ntpd[5091]: ntpd exiting on signal 15
Dec  4 18:15:54 mythbox ntpdate[5807]: adjust time server 91.189.94.4 offset -0.000671 sec
Dec  4 18:15:54 mythbox ntpd[5836]: ntpd 4.2.4p4@1.1520-o Wed Aug 20 17:03:52 UTC 2008 (1)
Dec  4 18:15:54 mythbox ntpd[5837]: precision = 1.000 usec
Dec  4 18:15:54 mythbox ntpd[5837]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec  4 18:15:54 mythbox ntpd[5837]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Dec  4 18:15:54 mythbox ntpd[5837]: Listening on interface #2 eth0, 192.168.2.147#123 Enabled
Dec  4 18:15:54 mythbox ntpd[5837]: kernel time sync status 0040
Dec  4 18:15:54 mythbox ntpd[5837]: frequency initialized -37.043 PPM from /var/lib/ntp/ntp.drift
Dec  4 18:15:54 mythbox ntpd[5837]: getaddrinfo: "::1" invalid host address, ignored
Dec  4 18:15:58 mythbox kernel: [   54.060019] eth0: no IPv6 routers present
Dec  4 18:16:03 mythbox /usr/sbin/cron[5936]: (CRON) INFO (pidfile fd = 3)
Dec  4 18:16:03 mythbox /usr/sbin/cron[5937]: (CRON) STARTUP (fork ok)
Dec  4 18:16:04 mythbox /usr/sbin/cron[5937]: (CRON) INFO (Running @reboot jobs)
Dec  4 18:16:07 mythbox lircd-0.8.4a[5532]: accepted new client on /dev/lircd
Dec  4 18:17:01 mythbox /USR/SBIN/CRON[6082]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  4 18:17:41 mythbox lircd-0.8.4a[5532]: removed client

==> /var/log/Xorg.0.log <==
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 420 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.45.42
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 420 at PCI:1:0:0:
(--) NVIDIA(0):     SAMSUNG (CRT-0)
(--) NVIDIA(0): SAMSUNG (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event2"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**)   USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**)   USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**)   USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event1"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**)   USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**)   USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**)   USB Keyboard: xkb_layout: "us"

==> /home/mythbox/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2008-12-04 18:15:50.788 Using runtime prefix = /usr
2008-12-04 18:15:50.807 Empty LocalHostName.
2008-12-04 18:15:50.807 Using localhost value of mythbox
2008-12-04 18:15:50.929 New DB connection, total: 1
2008-12-04 18:15:50.936 Connected to database 'mythconverg' at host: localhost
2008-12-04 18:15:50.937 Closing DB connection named 'DBManager0'
2008-12-04 18:15:50.938 Connected to database 'mythconverg' at host: localhost
04/12/2008 18:15:51 passing arg to libvncserver: -rfbauth
04/12/2008 18:15:51 passing arg to libvncserver: /root/.vnc/passwd
04/12/2008 18:15:51 passing arg to libvncserver: -rfbport
04/12/2008 18:15:51 passing arg to libvncserver: 5900
04/12/2008 18:15:51 x11vnc version: 0.9.3 lastmod: 2007-09-30
04/12/2008 18:15:51 Using X display :0
04/12/2008 18:15:51 
04/12/2008 18:15:51 ------------------ USEFUL INFORMATION ------------------
04/12/2008 18:15:51 X DAMAGE available on display, using it for polling hints.
04/12/2008 18:15:51   To disable this behavior use: '-noxdamage'
04/12/2008 18:15:51 
04/12/2008 18:15:51 XFIXES available on display, resetting cursor mode
04/12/2008 18:15:51   to: '-cursor most'.
04/12/2008 18:15:51   to disable this behavior use: '-cursor arrow'
04/12/2008 18:15:51   or '-noxfixes'.
04/12/2008 18:15:51 using XFIXES for cursor drawing.
04/12/2008 18:15:51 GrabServer control via XTEST.
04/12/2008 18:15:51 
04/12/2008 18:15:51 Scroll Detection: -scrollcopyrect mode is in effect to
04/12/2008 18:15:51   use RECORD extension to try to detect scrolling windows
04/12/2008 18:15:51   (induced by either user keystroke or mouse input).
04/12/2008 18:15:51   If this yields undesired behavior (poor response, painting
04/12/2008 18:15:51   errors, etc) it may be disabled via: '-noscr'
04/12/2008 18:15:51   Also see the -help entry for tuning parameters.
04/12/2008 18:15:51   You can press 3 Alt_L's (Left "Alt" key) in a row to 
04/12/2008 18:15:51   repaint the screen, also see the -fixscreen option for
04/12/2008 18:15:51   periodic repaints.
04/12/2008 18:15:51 
04/12/2008 18:15:51 XKEYBOARD: number of keysyms per keycode 6 is greater
04/12/2008 18:15:51   than 4 and 287 keysyms are mapped above 4.
04/12/2008 18:15:51   Automatically switching to -xkb mode.
04/12/2008 18:15:51   If this makes the key mapping worse you can
04/12/2008 18:15:51   disable it with the "-noxkb" option.
04/12/2008 18:15:51   Also, remember "-remap DEAD" for accenting characters.
04/12/2008 18:15:51 X FBPM extension not supported.
04/12/2008 18:15:51 X display is capable of DPMS.
04/12/2008 18:15:51 --------------------------------------------------------
04/12/2008 18:15:51 
04/12/2008 18:15:51 Default visual ID: 0x21
04/12/2008 18:15:51 Read initial data from X display into framebuffer.
04/12/2008 18:15:51 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/7680
04/12/2008 18:15:51 
04/12/2008 18:15:51 X display :0.0 is 32bpp depth=24 true color
04/12/2008 18:15:51 
04/12/2008 18:15:51 Listening for VNC connections on TCP port 5900
04/12/2008 18:15:51 fb read rate: 96 MB/sec
04/12/2008 18:15:51 screen setup finished.
04/12/2008 18:15:51 

The VNC desktop is:      mythbox:0
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
** Message: another SSH agent is running at: /tmp/ssh-SzQGtw5571/agent.5571
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (nm-applet:5871): WARNING **: No connections defined
2008-12-04 18:16:02.855 Using runtime prefix = /usr

** (update-notifier:5865): WARNING **: already running?

2008-12-04 18:16:03.510 XScreenSaver support enabled
2008-12-04 18:16:03.510 DPMS is active.
2008-12-04 18:16:03.511 Empty LocalHostName.
2008-12-04 18:16:03.512 Using localhost value of mythbox
2008-12-04 18:16:03.539 New DB connection, total: 1
2008-12-04 18:16:03.597 Connected to database 'mythconverg' at host: localhost
2008-12-04 18:16:03.599 Closing DB connection named 'DBManager0'
2008-12-04 18:16:03.606 Primary screen 0.
2008-12-04 18:16:03.607 Connected to database 'mythconverg' at host: localhost
2008-12-04 18:16:03.616 Using screen 0, 1920x1080 at 0,0

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.7G  7.9G  25% /
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  340K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.8M  375M   1% /dev
tmpfs                 378M     0  378M   0% /dev/shm
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-10-generic/volatile
/dev/sda6             268G  2.6G  265G   1% /var/lib

==> uname -a <==
Linux mythbox 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)

==> lsusb <==
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==> /proc/driver/nvidia/agp <==

==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
VideoMemoryTypeOverride: 1
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
SoftEDIDs: 1
Mobile: 4294967295
ResmanDebugLevel: 4294967295
FlatPanelMode: 0
DevicesConnected: 0
RmLogonRC: 1
VbiosFromROM: 0
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
DetectPrimaryVga: 1
EnableBrightnessControl: 0
PanelPWMFrequency: 1018
PanelBrightnessLimits: 65280
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
MapRegistersEarly: 0

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA Linux x86 Kernel Module  96.43.09  Mon Oct 27 14:23:30 PST 2008
GCC version:  gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce4 MX 420
IRQ:   		 16
Video BIOS: 	 04.17.00.45.42
Card Type: 	 AGP
DMA Size: 	 32 bits
DMA Mask: 	 0xffffffff

==> lshw <==
computer
    description: Mini Tower Computer
    product: DIM4500
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=44454C4C-5300-1043-8050-B2C04F523131
  *-core
       description: Motherboard
       product: D845EPT2
       vendor: Intel Corporation
       physical id: 0
       version: AAA83422-107
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 1
          version: A02 (05/22/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.4
          slot: X1
          size: 2GHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 768MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: [REMOVED]
             slot: DIMM1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: [REMOVED]
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 420]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
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
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV26 IEEE-1394 Controller (Link)
                vendor: Texas Instruments
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3 module=ohci1394
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
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: Maxtor 6L300R0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BAJ4
                serial: [REMOVED]
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2184fe3a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: [REMOVED]
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-02 21:09:27 filesystem=ext3 modified=2008-12-04 18:15:22 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-12-04 18:15:22 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 268GiB
                   capacity: 268GiB
                   capabilities: primary extended partitioned partitioned:extended

                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 972MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /var/lib
                      capacity: 267GiB
                      configuration: mount.fstype=xfs mount.options=rw,attr2,noquota state=mounted
           *-cdrom
                description: DVD writer
                product: DVDRW SHW-1635S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: YS0R
                capabilities: removable audio cd-r cd-rw dvd dvd-r
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
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 [/HTML]

---

### Post by bmwman on 2008-12-06
I am having the same problem with Verizon Fios- Motorola 6200 cable box. I can get video working for few minutes but it is unreliableand it freezes if i try to change the channel couple times. I use firewire P2P.

---

### Post by ahood on 2008-12-06
Not sure if it will be of much help, but a few links with info are below.

[http://www.gossamer-threads.com/lists/mythtv/users/358703](http://www.gossamer-threads.com/lists/mythtv/users/358703)

[http://www.mailinglistarchive.com/mythtv-users@mythtv.org/msg80061.html](http://www.mailinglistarchive.com/mythtv-users@mythtv.org/msg80061.html)

---

### Post by rschapman on 2008-12-06
Thanks for the additional information. I've been looking through it and others. I'm all about tinkering but I'm not sure if I'm up to the fight right now. I might just hold off and buy an HDhomerun. At this I have just the most basic HD/digital package so I'm not all that worried about encrypted channels. If someone does know of a pretty reasonable fix or an update then I'll give it another go. Thanks.

---

### Post by majoridiot on 2008-12-07
> **bmwman said:**
> I am having the same problem with Verizon Fios- Motorola 6200 cable box. I can get video working for few minutes but it is unreliableand it freezes if i try to change the channel couple times. I use firewire P2P.

in my experience, the 62xx series boxes run most reliably with broadcast connections at 200Mbps.

SA boxes generally run p2p at 200 or 400Mbps but should fall-back to 100 if needed.

for everyone posting here, you may get more love from a properly primed stb and by identifying
encrypted channels and removing them from your line-up.  this is indicated if you find regular failures
changing from one channel to another and it dies for "no reason".

some more info and sources:

general:

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)  (info is out of date but good for background)

mythprime:

[http://ubuntuforums.org/showthread.php?t=884880](http://ubuntuforums.org/showthread.php?t=884880)

scanfw:

[http://ubuntuforums.org/showthread.php?t=795378](http://ubuntuforums.org/showthread.php?t=795378)

the most recent sources:

[https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

note that both mythprime and scanfw should be run with the mythtv backend server stopped:

```
$ sudo /etc/init.d/mythbackend stop
```

(to restart mythbackend, run the same command with **start** when you are finished)

my suggestion is make sure the settings for the tuner are correct in mythtv backend settings, stop
the server, run mythprime until a good prime is achieved, restart the server (being sure the starting
channel set in mythbackend is the same as the one you just primed with) and see if the connection is
any more stable.

see the READMEs for both mythprime and scanfw for more info and tips.

if priming helps or fixes your problem, you will need to make changes to /etc/init.d/mythbackend to
prime the box every time the server starts.  i am unsure what changes need to be made at this point... the
mythbuntu devs have never trusted the mythprime code enough to make it automatic and have shown 
little interest in helping support it.

if this helps, PM me and i will look into changes you need to make... i have not used firewire for years
but still provide support for those who do.

good luck!

---

### Post by rschapman on 2008-12-18
I followed the instructions for using mythprime. I got it working but it kept returning problems. It could reset the bus and communicate but that's it. In 8.10 I can change the channel but that's it. In 8.04 I could get some video to work but now nothing. Should I go back to 8.04? What has changed between the two in the firewire connection that could cause this you think? Thanks for all of the help so far.

---

### Post by 4dognight on 2008-12-19
I have 2 STB(DCH3200) using firewire. I have them set to broadcast 200 mb/s.I use 8.04. I experince loss of firewire on a somewhat regular basis. I attribute it to my cable company turning on and off encryption on some channels. I think depending on what is playing they encrypt the channel, then turn it off after. I have confirmed it by looking at the diagnostic menu of the STB. Sometimes I need to do a reboot to clear it up, sometimes it just starts working on its own. 

Make sure you are on a channel that is not encrypted. Verify it by using the diagnostic menu of the STB.

Question for the Major. Do you think it would be possible to detect an encrypted channel in Myth, and prevent myth from trying to tune it? This might help it from getting totally hosed. If Myth then sets the current channel to the encrypted channel, it keeps trying to tune it, each time you go to that tuner. Only way to fix that is to update the entry in the database manually, or go through the config and change the channel there.

---

### Post by rschapman on 2008-12-20
Thanks for the info. I've gone back and forth between trying broadcast and point to point. I've tried almost all the channels I'm supposed to get. I tried tuning the basic channels that are supposed to be clear and they still do not show. I'm about to rebuild the machine and I might give 8.04 a go again.

---

### Post by majoridiot on 2008-12-20
> **rschapman said:**
> Thanks for the info. I've gone back and forth between trying broadcast and point to point. I've tried almost all the channels I'm supposed to get. I tried tuning the basic channels that are supposed to be clear and they still do not show. I'm about to rebuild the machine and I might give 8.04 a go again.

unless you have a rare stb, you should concentrate on p2p connections, as (in my experience) all SA boxes
prefer p2p connections.  200Mbps is also very reliable in my experience.

it is possible that your issues are not due to mythtv, but lie in your stb... so taking the time to resinstall before 
further testing is not necessarily the best use of your time.  things i would look at before i went the reinstall
route:

highly recommended to stop the backend server whilst testing: ```
$ sudo /etc/init.d/mythtv-backend stop
```

1. make sure the stb returns good info when you do *plugreport*.  things to look for include GUID, etc.

2. see if you are getting *any* good connections at all using *mythprime* in verbose mode. try it on
more than one channel, to be sure you are not trying to prime an encrypted channel.  your best best will be analog
non-premium channels.  you can run mythprime in verbose mode by:

```
$ mythprime -v -c xx
```

where *xx* is the channel number to tune and prime.

this will show you whether or not you can establish a reliable connection at all... or if you are getting *anything*
good from the stb.  if you do find a channel that primes successfully, then you should survey your channels
to see the encryption status of your channels, to remove them from your SD line-up...

3. scanfw ([https://help.ubuntu.com/community/MythTV_Firewire/scanfw](https://help.ubuntu.com/community/MythTV_Firewire/scanfw)) will help you scan for encrypted channels,
should you make it this far.  you should use the channel you successfully primed with as your "safe priming" channel
for the *-p* argument.

4. if you fail at step 2, check to see if there is more than one firewire port on the *STB*... if so,
shut the computer down, change the cable to that port and try again.  it is not unusual for one port on SA boxes
(especially the 4xxx series) to be fully functional and the other one only partially functional.

if you still get no love, then your problems are due to either your cable company, the STB firmware or both...

the SA4250HDCs, especially on time-warner cable systems, are known to either have issues or to be totally useless
for firewire.  this is due entirely to their firmware and policies, *not* mythtv or the linux firewire stack.

good luck...

> **4dognight said:**
> Question for the Major. Do you think it would be possible to detect an encrypted channel in Myth, and prevent myth from trying to tune it? This might help it from getting totally hosed. If Myth then sets the current channel to the encrypted channel, it keeps trying to tune it, each time you go to that tuner. Only way to fix that is to update the entry in the database manually, or go through the config and change the channel there.

yes, this is possible... although it would require an overhaul of the mythtv firewire libraries.  honestly, i am
surprised that this was not done early-on, as encryption has always been an issue and it is not that hard to do.

the firewire tuning model introduced in mythtv .21 (i think) made firewire tuning act more like a QAM tuner, etc...
which is a good idea, but not implemented in the sanest way for the best user experience, IMO.  although better in
many ways, the "new" way does introduce problems that were much easier to work around in the past.

short of rewriting jim westfall's firewire code- or coming up with a heavy-duty channel changer that also checks
encryption status and then interacts with the database to "fix" a bad channel tune so it will not try to tune it 
again the next time, etc- it is kind of a hard nut to crack.

the encryption-checking code would not be that hard to integrate, but i have gotten nowhere trying to contact/work 
with the devs on this issue... short of "feel free to submit a patch".

unfortunately, not the best way to encourage improvements... and given that i have not used firewire as a tuner in
two years or more, i am hard-pressed to invest the time and effort to improve something that does not seem to be a
priority to the mythtv devs.

---

### Post by 4dognight on 2008-12-20
I wonder how many STB users of Myth there are. Doesn't sound like very many.

---

### Post by rschapman on 2008-12-21
So this is kind of weird and maybe someone can explain it to me. I'm still a bit of a noob. I changed it to the p2p mode with 200Mbps. Even though mythprime reported failure on multiple channels like abc, cbs, and fox, it started working. Plugreport came back okay. It's still working when I use it through the frontend but mythprime continues to report a failure. So...I'm glad it's working but I'm not sure why it is. Previously when using p2p 200 it didn't work. But I'm not going to complain. Thanks for all of the help.

---

### Post by majoridiot on 2008-12-21
> **rschapman said:**
> So this is kind of weird and maybe someone can explain it to me. I'm still a bit of a noob. I changed it to the p2p mode with 200Mbps. Even though mythprime reported failure on multiple channels like abc, cbs, and fox, it started working. Plugreport came back okay. It's still working when I use it through the frontend but mythprime continues to report a failure. So...I'm glad it's working but I'm not sure why it is. Previously when using p2p 200 it didn't work. But I'm not going to complain. Thanks for all of the help.

i can not say for sure, but the two most likely causes are either an update to your stb firmware or possibly
a change in 8.10.  i am not sure if 8.10 is using the "old" firewire stack or the new "juju" one.  either way, 
its a good thing for you :)

FYI, if your SA is going to work, it will work point-to-point... that is how they work.  most motorola stbs prefer 
broadcast but some work fine p2p.

if you are consistently getting priming failures but are recording ok- and can not find a channel that
does prime, i suggest commenting out the call to mythprime in /etc/init.d/mythtv-backend to avoid possible 
failure launching the backend.

---

### Post by rschapman on 2008-12-21
So upon further testing I've found that if I do not run mythprime, although it still reports failure, it will not tune over firewire. Once I've attempted priming it starts working like it should. I still have not added it to the startup. Should I consider adding it to the startup even though it's technically failing? I don't restart that much so guess I could just run it manually. Is there a way to tie it to a key press on my remote? Again thanks for all of the help. Should I set this one to "solved" or not since it's kind of a mystery to me?

---

### Post by majoridiot on 2008-12-21
> **rschapman said:**
> So upon further testing I've found that if I do not run mythprime, although it still reports failure, it will not tune over firewire. Once I've attempted priming it starts working like it should. I still have not added it to the startup. Should I consider adding it to the startup even though it's technically failing? I don't restart that much so guess I could just run it manually. Is there a way to tie it to a key press on my remote? Again thanks for all of the help. Should I set this one to "solved" or not since it's kind of a mystery to me?

kind of a mystery what is going on here... but if it fails recording without attempting a prime, then i would 
set it to prime... even if the prime fails.  what you describe does not make sense, but you seem to have found
something that works.

if you want to set it up on a remote button, you can do that.  the simplest way is to add an entry to ~/.lirc/mythv

```
begin
    remote = REMOTE
    prog = irexec
    button = BUTTON
    config = mythprime -c XX &
end
```

where **REMOTE** is your remote type, **BUTTON** is the remote button you want it assigned to and **XX** is 
the channel you want to (try to) prime.

then restart lirc:
```
$ sudo /etc/init.d/lirc restart
```

you may or may not need to add irexec to your rc.local file... (edited as sudo):

```
irexec -d
```

---

