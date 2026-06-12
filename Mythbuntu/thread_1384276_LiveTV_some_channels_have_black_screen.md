---
title: "LiveTV: some channels have black screen"
date: 2010-01-18
forum: Mythbuntu
---

### Post by hineas on 2010-01-18
I installed Mythbuntu this past week and I have been struggling to get everything working.  Two days ago I got the Hauppauge  WinTV-HVR-1950 capture card (USB).  After two days of googling and searching forums, I finally got it working.  Last night as I was finalizing the setup, I realized that HALF of my channels don't work.  I can watch channels 2-13 flawlessly (audio and video are working great).  However, any channel 14 and above act as if there is no signal.  On those channels I get "white" noise and a blank screen.

I am using the pvrusb2 drivers.  My signal is NTSC analog cable.  I know the tuner card works since I plugged it into my windows laptop and I was able to install it and watch all of my channels.  To me it sounds like there might be something wrong with the decoder, but I'm  not sure.  Any ideas would be welcome!

When I run mythfrontend in a terminal, this is the output:

2010-01-18 08:22:10.092 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-01-18 08:22:10.141 Using runtime prefix = /usr
2010-01-18 08:22:10.141 Using configuration directory = /home/carl/.mythtv
^[`2010-01-18 08:22:11.013 Empty LocalHostName.
2010-01-18 08:22:11.014 Using localhost value of linux-mythtv
2010-01-18 08:22:11.024 New DB connection, total: 1
2010-01-18 08:22:11.030 Connected to database 'mythconverg' at host: localhost
2010-01-18 08:22:11.037 Closing DB connection named 'DBManager0'
2010-01-18 08:22:11.091 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-18 08:22:11.093 DPMS is active.
2010-01-18 08:22:11.095 Primary screen: 0.
2010-01-18 08:22:11.096 Connected to database 'mythconverg' at host: localhost
2010-01-18 08:22:11.098 Using screen 0, 1280x1024 at 0,0
2010-01-18 08:22:11.139 MythUI Image Cache size set to 20971520 bytes
2010-01-18 08:22:11.140 Enabled verbose msgs:  important general
2010-01-18 08:22:11.174 Primary screen: 0.
2010-01-18 08:22:11.175 Using screen 0, 1280x1024 at 0,0
2010-01-18 08:22:11.206 Using theme base resolution of 800x600
2010-01-18 08:22:11.255 LIRC: Successfully initialized '/dev/lircd' using '/home/carl/.mythtv/lircrc' config
2010-01-18 08:22:11.255 JoystickMenuThread Error: Joystick disabled - Failed to read /home/carl/.mythtv/joystickmenurc
2010-01-18 08:22:11.635 Using the Qt painter
2010-01-18 08:22:11.687 Loaded base theme from /usr/share/mythtv/themes/MythCenter/base.xml
2010-01-18 08:22:11.914 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-18 08:22:11.982 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-18 08:22:12.031 New DB connection, total: 2
2010-01-18 08:22:12.035 Connected to database 'mythconverg' at host: localhost
2010-01-18 08:22:12.705 Desktop video mode: 1280x1024 60.0204 Hz
2010-01-18 08:22:13.080 Registering Internal as a media playback plugin.
2010-01-18 08:22:13.264 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-01-18 08:22:13.276 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-01-18 08:22:13.281 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-01-18 08:22:13.289 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-01-18 08:22:13.388 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-01-18 08:22:13.461 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-01-18 08:22:13.487 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-01-18 08:22:13.581 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-01-18 08:22:13.739 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-01-18 08:22:13.742 Found mainmenu.xml for theme 'MythCenter'
2010-01-18 08:22:14.598 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-18 08:22:14.599 Using protocol version 50
2010-01-18 08:22:37.098 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-18 08:22:37.099 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-18 08:22:37.100 Using protocol version 50
2010-01-18 08:22:37.162 Spawning LiveTV Recorder -- begin
2010-01-18 08:22:38.013 Spawning LiveTV Recorder -- end
2010-01-18 08:22:38.036 We have a playbackURL(/storage/livetv/1013_20100118082237.mpg) & cardtype(MPEG)
2010-01-18 08:22:38.833 We have a RingBuffer
2010-01-18 08:22:38.884 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2010-01-18 08:22:39.497 AFD: Opened codec 0x919d0e0, id(MPEG2VIDEO) type(Video)
2010-01-18 08:22:39.497 AFD: codec MP2 has 2 channels
2010-01-18 08:22:39.497 AFD: Opened codec 0x919d490, id(MP2) type(Audio)
2010-01-18 08:22:39.615 Opening audio device 'default'. ch 6(2) sr 32000
2010-01-18 08:22:39.615 Opening ALSA audio device 'default'.
2010-01-18 08:22:41.275 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-01-18 08:22:41.350 OSD Theme Dimensions W: 1280 H: 720
2010-01-18 08:22:41.367 New DB connection, total: 3
2010-01-18 08:22:41.373 Connected to database 'mythconverg' at host: localhost
2010-01-18 08:22:41.994 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2010-01-18 08:22:41.994 TV: Changing from None to Watching WatchingLiveTV
2010-01-18 08:22:41.994 TV: State is LiveTV & mctx == ctx
2010-01-18 08:22:41.995 Video timing method: USleep with busy wait
2010-01-18 08:22:41.996 TV: UpdateOSDInput done
2010-01-18 08:22:41.996 TV: UpdateLCD done
2010-01-18 08:22:41.996 TV: ITVRestart done
2010-01-18 08:22:42.003 Realtime priority would require SUID as root.
2010-01-18 08:22:42.022 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-18 08:23:11.572 WriteAudio: buffer underrun
2010-01-18 08:23:11.658 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.658 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:11.659 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:29.873 [mp2 @ 0x1a516c0]incomplete frame
2010-01-18 08:23:29.873 AFD Error: Unknown audio decoding error
2010-01-18 08:23:32.168 WriteAudio: buffer underrun
2010-01-18 08:23:46.732 WriteAudio: buffer underrun
2010-01-18 08:23:46.904 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.904 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.904 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.904 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.905 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.905 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.905 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.905 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:23:46.905 [mpeg2video @ 0x1a516c0]Missing picture start code
2010-01-18 08:24:05.925 TV: Attempting to change from Watching WatchingLiveTV to None
2010-01-18 08:24:05.925 [mp2 @ 0x1a516c0]incomplete frame
2010-01-18 08:24:05.925 AFD Error: Unknown audio decoding error
2010-01-18 08:24:06.172 TV: Changing from Watching WatchingLiveTV to None
2010-01-18 08:24:06.173 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-18 08:24:09.116 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

---

### Post by hineas on 2010-01-18
I finally figured it out after 8 hours a searching in the wrong direction.  I asked my dad and he said, "Channels 2 though 13 is the old range of channels that used to be on TV."  That's when I realized that in mythtv-setup under general configuration I had the input set to "US-Bcast."  Switching it to US-Cable was all it took!

I'm glad I was able to solve it, and I hope anyone having the same problem finds this post!

---

