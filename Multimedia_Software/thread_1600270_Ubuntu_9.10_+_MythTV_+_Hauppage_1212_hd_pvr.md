---
title: "Ubuntu 9.10 + MythTV + Hauppage 1212 hd pvr"
date: 2010-10-18
forum: Multimedia Software
---

### Post by kireol on 2010-10-18
tldr; Brand new hdpvr, first time using mythtv, get error: MythTV is using all inputs, but there are no active recordings.


My PC is my client and server and is running Ubuntu 9.10

I installed Mythtv from repositories.

```
MythTV Version   : 22594
MythTV Branch    : branches/release-0-22-fixes
Network Protocol : 50
Library API      : 0.22.20091023-1
QT Version       : 4.5.2
Options compiled in:
 linux profile using_oss using_alsa using_pulse using_jack using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg
```


I have a brand new Hauppage HD PVR which is on /dev/video0
When I ran 'mplayer /dev/video0' I got a still image of live TV.  It was a bit interlaced and only 1 frame, but it was live TV, so that part tells me at least something is working.
```
dmesg | grep video
[    0.541900] pci 0000:01:00.0: Boot video device
[    7.451089] Linux video capture interface: v2.00
[    7.811656] hdpvr 1-2:1.0: device now attached to /dev/video0
[  561.650095] hdpvr 1-2:1.0: device /dev/video0 disconnected
[  565.951847] hdpvr 1-2:1.0: device now attached to /dev/video0
[  853.341331] hdpvr 1-2:1.0: device /dev/video0 disconnected
[  856.250698] hdpvr 1-2:1.0: device now attached to /dev/video0
[  859.010112] hdpvr 1-2:1.0: device /dev/video0 disconnected
[  864.330908] hdpvr 1-2:1.0: device now attached to /dev/video0
[  870.640086] hdpvr 1-2:1.0: device /dev/video0 disconnected
[  878.151229] hdpvr 1-2:1.0: device now attached to /dev/video0
[ 2561.600071] hdpvr 1-2:1.0: device /dev/video0 disconnected
[ 3086.683264] hdpvr 1-2:1.0: device now attached to /dev/video0
[ 3242.551684] hdpvr 1-2:1.0: device /dev/video0 disconnected
[ 3247.271496] hdpvr 1-2:1.0: device now attached to /dev/video0
[ 3268.671316] hdpvr 1-2:1.0: device /dev/video0 disconnected
[ 3281.471128] hdpvr 1-2:1.0: device now attached to /dev/video0
[ 3284.481343] hdpvr 1-2:1.0: device /dev/video0 disconnected
[ 3309.072541] hdpvr 1-2:1.0: device now attached to /dev/video0

```


The PVR is hooked up to my cable box.

Here's my log from startup for the mythtv-backend
```
2010-10-18 19:25:31.634 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-10-18 19:25:31.636 Using runtime prefix = /usr
2010-10-18 19:25:31.637 Using configuration directory = /home/mythtv/.mythtv
2010-10-18 19:25:31.638 Empty LocalHostName.
2010-10-18 19:25:31.639 Using localhost value of brutus
2010-10-18 19:25:31.643 New DB connection, total: 1
2010-10-18 19:25:31.647 Connected to database 'mythconverg' at host: 127.0.0.1
2010-10-18 19:25:31.648 Closing DB connection named 'DBManager0'
2010-10-18 19:25:31.649 Connected to database 'mythconverg' at host: 127.0.0.1
2010-10-18 19:25:31.653 Current MythTV Schema Version (DBSchemaVer): 1244
2010-10-18 19:25:31.658 MythBackend: Starting up as the master server.
2010-10-18 19:25:31.662 New DB connection, total: 2
2010-10-18 19:25:31.663 Connected to database 'mythconverg' at host: 127.0.0.1
2010-10-18 19:25:31.667 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2010-10-18 19:25:31.670 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2010-10-18 19:25:31.671 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2010-10-18 19:25:31.674 New DB connection, total: 3
2010-10-18 19:25:31.677 Connected to database 'mythconverg' at host: 127.0.0.1
2010-10-18 19:25:31.695 Enabling Upnpmedia rebuild thread.
2010-10-18 19:25:33.264 Main::Registering HttpStatus Extension
2010-10-18 19:25:33.265 Enabled verbose msgs:  important general
2010-10-18 19:25:33.267 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-10-18 19:25:41.697 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.

```

Here's my log for the front end
```
2010-10-18 19:30:28.500 Current MythTV Schema Version (DBSchemaVer): 1244
2010-10-18 19:30:28.594 Desktop video mode: 3600x1200 59.9556 Hz
2010-10-18 19:30:28.685 Registering Internal as a media playback plugin.
2010-10-18 19:30:28.686 No plugins directory /usr/lib/mythtv/plugins
2010-10-18 19:30:28.698 MMUnix::AddDevice() Error: failed to stat /dev/bdi,
                        eno: No such file or directory (2)
2010-10-18 19:30:28.704 MMUnix::AddDevice() Error: failed to stat /dev/power,
                        eno: No such file or directory (2)
2010-10-18 19:30:28.707 MMUnix::AddDevice() Error: failed to stat /dev/trace,
                        eno: No such file or directory (2)
2010-10-18 19:30:28.712 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-10-18 19:30:28.730 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-10-18 19:30:28.732 Found mainmenu.xml for theme 'Mythbuntu'
2010-10-18 19:30:29.351 MythContext: Connecting to backend server: 192.168.2.100:6543 (try 1 of 1)
2010-10-18 19:30:29.352 Using protocol version 50
2010-10-18 19:31:20.327 AudioPulseUtil: Resume Success
2010-10-18 19:31:20.327 Deleting UPnP client...

```

When I click "watch TV" i get the error

error: MythTV is using all inputs, but there are no active recordings.

---

