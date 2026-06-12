---
title: "Instaling codecs for AVI broke MythTV"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by gizzard on 2007-10-16
I have a fresh Feisty 64bit install with MythTV. Everything with respect to Myth was working well - I have a DVB card which was tuning channels perfectly. I then tried to play an AVI file using mplayer-nogui and VLC but got a pink / green screen with vertical lines. The audio was normal. I read about w64codecs and libdvdcss2 and following [these directions]("https://help.ubuntu.com/community/Medibuntu"), I installed both. Afterwards, both VLC and mplayer was able to play the AVI without difficulty. However, MythTV frontend now could not display any video; when watching live TV, the video is garbled but the audio is normal. I am guessing the installation of either w64codecs or libdvdcss2 has somehow messed up my Myth installation, but I'm not sure how to fix it.

When I start mythfrontend and try to watch TV, here's the output:
```

X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-10-16 19:12:12.962 Using runtime prefix = /usr
2007-10-16 19:12:12.968 Gnome-Screensaver support enabled
2007-10-16 19:12:12.968 DPMS is active.
2007-10-16 19:12:12.977 New DB connection, total: 1
2007-10-16 19:12:12.981 Connected to database 'mythconverg' at host: localhost
2007-10-16 19:12:12.982 Total desktop dim: 1024x768, with 2 screen[s].
2007-10-16 19:12:12.983 Using screen 0, 1024x768 at 0,0
2007-10-16 19:12:12.991 Current Schema Version: 1160
2007-10-16 19:12:12.992 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-10-16 19:12:12.992 Enabled verbose msgs:  important general
2007-10-16 19:12:13.198 Total desktop dim: 1024x768, with 2 screen[s].
2007-10-16 19:12:13.199 Using screen 0, 1024x768 at 0,0
2007-10-16 19:12:13.200 Switching to square mode (Retro)
2007-10-16 19:12:13.214 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-10-16 19:12:13.620 Joystick disabled.
2007-10-16 19:12:13.782 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-10-16 19:12:13.852 Registering Internal as a media playback plugin.
2007-10-16 19:12:13.871 Registering MythDVD DVD Media Handler as a media handler ext()
2007-10-16 19:12:13.872 Registering MythDVD VCD Media Handler as a media handler ext()
2007-10-16 19:12:14.546 Using NV NPOT texture extension
2007-10-16 19:12:16.058 New DB connection, total: 2
2007-10-16 19:12:16.058 Connected to database 'mythconverg' at host: localhost
2007-10-16 19:12:16.092 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-10-16 19:12:16.092 Using protocol version 31
2007-10-16 19:12:16.107 TV: Attempting to change from None to WatchingLiveTV
2007-10-16 19:12:16.108 Using protocol version 31
2007-10-16 19:12:16.268 DPMS Deactivated 
2007-10-16 19:12:16.283 NVP: Disabling Audio, params(-1,2,44100)
2007-10-16 19:12:16.303 VideoOutputXv: XvMCTex: Init failed
2007-10-16 19:12:16.304 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x1b6
2007-10-16 19:12:16.670 New DB connection, total: 3
2007-10-16 19:12:16.670 Realtime priority would require SUID as root.
2007-10-16 19:12:16.671 Connected to database 'mythconverg' at host: localhost
2007-10-16 19:12:16.671 TV: Changing from None to WatchingLiveTV
2007-10-16 19:12:16.775 Video timing method: USleep with busy wait
2007-10-16 19:12:17.445 VideoOutputXv: XvMCTex: Init failed
2007-10-16 19:12:17.446 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x1b6
2007-10-16 19:12:17.770 AFD: Opened codec 0x31c2bc0, id(MPEG2VIDEO) type(Video)
2007-10-16 19:12:17.771 AFD: Opened codec 0x34e4200, id(AC3) type(Audio)
2007-10-16 19:12:17.814 Opening ALSA audio device 'default'.
2007-10-16 19:12:17.889 Mixer unable to find control Master
2007-10-16 19:12:17.889 Mixer unable to find control Master
2007-10-16 19:12:17.891 NVP: Enabling Audio
2007-10-16 19:12:18.892 NVP: Prebuffer wait timed out 10 times.
2007-10-16 19:12:21.896 TV: Attempting to change from WatchingLiveTV to None
2007-10-16 19:12:22.169 TV: Changing from WatchingLiveTV to None
2007-10-16 19:12:22.185 DPMS Reactivated.

```

I would really appreciate any help, especially on how to figure out what I did wrong.

---

