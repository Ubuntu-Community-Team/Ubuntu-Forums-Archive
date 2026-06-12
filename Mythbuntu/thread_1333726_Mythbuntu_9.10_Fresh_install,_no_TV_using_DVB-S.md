---
title: "Mythbuntu 9.10: Fresh install, no TV using DVB-S"
date: 2009-11-21
forum: Mythbuntu
---

### Post by Morgennebel on 2009-11-21
Hi there,


I just installed mythbuntu 9.10 three times (two times 64 bit, 1 time 32 bit with mythtv-repos updates). Fresh setup, new database, no recordings migrated.

All installations result in no Live TV - I do get a black screen with OSD and (LMs) status. After a few minutes I get a "Error opening jump program file buffer" popup.

After I added a transponder the system finds six channels (ZDF, Kika, ..) using a channel scan - so I assume that I correctly entered the values for the transponder in kHz.

Details:
MythTV Version   : 22869
MythTV Branch    : branches/release-0-22-fixes

mythbackend.log:
```

2009-11-21 23:52:30.621 New DB scheduler connection
2009-11-21 23:52:30.622 Connected to database 'mythconverg' at host: 192.168.1.25
2009-11-21 23:52:30.641 Enabling Upnpmedia rebuild thread.
2009-11-21 23:52:32.094 Main::Registering HttpStatus Extension
2009-11-21 23:52:32.097 Enabled verbose msgs:  important general
2009-11-21 23:52:32.103 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-21 23:52:33.626 Reschedule requested for id -1.
2009-11-21 23:52:33.653 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-11-21 23:52:33.659 Seem to be woken up by USER
2009-11-21 23:52:36.482 MainServer::ANN Monitor
2009-11-21 23:52:36.485 adding: mythtv-desktop as a client (events: 0)
2009-11-21 23:52:36.488 MainServer::ANN Monitor
2009-11-21 23:52:36.491 adding: mythtv-desktop as a client (events: 1)
2009-11-21 23:52:36.521 MainServer::ANN Playback
2009-11-21 23:52:36.524 adding: mythtv-desktop as a client (events: 0)
2009-11-21 23:52:36.527 TVRec(1): Changing from None to Watching WatchingLiveTV
2009-11-21 23:52:36.533 TVRec(1): HW Tuner: 1->1
2009-11-21 23:52:36.866 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-21 23:52:40.643 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-11-21 23:53:50.633 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-21 23:53:58.751 TVRec(1): Changing from Watching WatchingLiveTV to None
2009-11-21 23:53:58.860 Finished recording Unknown: channel 29007
2009-11-21 23:54:15.596 Reloading backend settings
2009-11-21 23:54:35.326 Reschedule requested for id 0.
2009-11-21 23:54:35.368 Scheduled 0 items in 0.0 = 0.00 match + 0.04 place
2009-11-21 23:54:50.659 Expiring 0 MBytes for 29007 @ Sat Nov 21 23:51:23 2009 => Unknown
2009-11-21 23:54:51.857 MainServer::ANN Playback
2009-11-21 23:54:51.857 MainServer::ANN Playback
2009-11-21 23:54:51.858 adding: mythtv-desktop as a client (events: 0)
2009-11-21 23:54:51.860 TVRec(1): Changing from None to Watching WatchingLiveTV
2009-11-21 23:54:51.865 TVRec(1): HW Tuner: 1->1
2009-11-21 23:54:52.210 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-21 23:55:02.479 TVRec(1): Changing from Watching WatchingLiveTV to None
2009-11-21 23:55:02.757 Finished recording Unknown: channel 29007
2009-11-21 23:55:02.771 MainServer::ANN Playback
2009-11-21 23:55:02.772 adding: mythtv-desktop as a client (events: 0)
2009-11-21 23:55:02.775 TVRec(3): Changing from None to Watching WatchingLiveTV
2009-11-21 23:55:02.780 TVRec(3): HW Tuner: 3->3
2009-11-21 23:55:02.786 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Your frequency setting (11954000) is out of range. (min/max:950000/2150000)
2009-11-21 23:55:02.832 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-21 23:56:50.665 Expiring 0 MBytes for 29007 @ Sat Nov 21 23:52:36 2009 => Unknown
2009-11-21 23:56:50.666 Expiring 0 MBytes for 29007 @ Sat Nov 21 23:54:51 2009 => Unknown
2009-11-22 00:00:00.876 Finished recording Unknown: channel 29007
2009-11-22 00:00:00.886 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-22 00:00:07.621 TVRec(3): Changing from Watching WatchingLiveTV to None
2009-11-22 00:00:07.631 Finished recording Unknown: channel 29007
2009-11-22 00:00:07.684 MainServer::ANN Playback
2009-11-22 00:00:07.685 adding: mythtv-desktop as a client (events: 0)
2009-11-22 00:00:07.687 TVRec(1): Changing from None to Watching WatchingLiveTV
2009-11-22 00:00:07.691 TVRec(1): HW Tuner: 1->1
2009-11-22 00:00:08.215 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-22 00:00:08.270 TVRec(1): Changing from Watching WatchingLiveTV to None
2009-11-22 00:00:08.525 Finished recording Unknown: channel 29007
2009-11-22 00:02:50.681 Expiring 0 MBytes for 29007 @ Sun Nov 22 00:00:07 2009 => Unknown

```mythfrontend.log:
```

2009-11-21 23:52:36.520 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-21 23:52:36.520 MythContext: Connecting to backend server: 192.168.1.25:6543 (try 1 of 1)
2009-11-21 23:52:36.520 Using protocol version 50
2009-11-21 23:52:36.527 Spawning LiveTV Recorder -- begin
2009-11-21 23:52:36.867 Spawning LiveTV Recorder -- end
2009-11-21 23:52:36.894 We have a playbackURL(/var/lib/mythtv/livetv/29007_20091121235236.mpg) & cardtype(DUMMY)
2009-11-21 23:52:36.894 We have a RingBuffer
2009-11-21 23:52:36.945 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-21 23:52:36.954 NVP(1): Disabling Audio, params(-1,2,44100)
2009-11-21 23:52:36.966 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-21 23:52:36.994 OSD Theme Dimensions W: 1280 H: 720
2009-11-21 23:52:37.258 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-11-21 23:52:37.258 TV: Changing from None to Watching WatchingLiveTV
2009-11-21 23:52:37.258 TV: State is LiveTV & mctx == ctx
2009-11-21 23:52:37.258 TV: UpdateOSDInput done
2009-11-21 23:52:37.258 TV: UpdateLCD done
2009-11-21 23:52:37.258 TV: ITVRestart done
2009-11-21 23:52:37.259 Video timing method: USleep with busy wait
2009-11-21 23:52:37.259 Realtime priority would require SUID as root.
2009-11-21 23:52:37.281 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-21 23:53:58.749 TV: Attempting to change from Watching WatchingLiveTV to None
2009-11-21 23:53:58.864 TV: Changing from Watching WatchingLiveTV to None
2009-11-21 23:53:58.865 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-21 23:54:02.207 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2009-11-21 23:54:03.209 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2009-11-21 23:54:15.599 Received a remote 'Clear Cache' request
2009-11-21 23:54:17.114 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2009-11-21 23:54:35.325 Received a remote 'Clear Cache' request
2009-11-21 23:54:46.397 Received a remote 'Clear Cache' request
2009-11-21 23:54:51.855 TV: Attempting to change from None to Watching WatchingLiveTV
2009-11-21 23:54:51.857 MythContext: Connecting to backend server: 192.168.1.25:6543 (try 1 of 1)
2009-11-21 23:54:51.857 Using protocol version 50
2009-11-21 23:54:51.860 Spawning LiveTV Recorder -- begin
2009-11-21 23:54:52.193 Spawning LiveTV Recorder -- end
2009-11-21 23:54:52.212 We have a playbackURL(/var/lib/mythtv/livetv/29007_20091121235451.mpg) & cardtype(DUMMY)
2009-11-21 23:54:52.212 We have a RingBuffer
2009-11-21 23:54:52.262 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-11-21 23:54:52.277 NVP(2): Disabling Audio, params(-1,2,44100)
2009-11-21 23:54:52.292 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-21 23:54:52.322 OSD Theme Dimensions W: 1280 H: 720
2009-11-21 23:54:52.603 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-11-21 23:54:52.603 TV: Changing from None to Watching WatchingLiveTV
2009-11-21 23:54:52.603 TV: State is LiveTV & mctx == ctx
2009-11-21 23:54:52.604 Realtime priority would require SUID as root.
2009-11-21 23:54:52.604 TV: UpdateOSDInput done
2009-11-21 23:54:52.604 TV: UpdateLCD done
2009-11-21 23:54:52.605 OpenGLVideoSync()
2009-11-21 23:54:52.605 TV: ITVRestart done
2009-11-21 23:54:52.631 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-21 23:54:52.642 Video timing method: SGI OpenGL
2009-11-21 23:55:02.523 ~OpenGLVideoSync() -- closing opengl vsync
2009-11-21 23:55:02.771 MythContext: Connecting to backend server: 192.168.1.25:6543 (try 1 of 1)
2009-11-21 23:55:02.771 Using protocol version 50
2009-11-21 23:55:02.842 NVP(2): Disabling Audio, params(-1,2,44100)
2009-11-21 23:55:02.853 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-21 23:55:02.882 OSD Theme Dimensions W: 1280 H: 720
2009-11-21 23:55:03.163 OpenGLVideoSync()
2009-11-21 23:55:03.163 Realtime priority would require SUID as root.
2009-11-21 23:55:03.184 LiveTVChain(live-mythtv-desktop-2009-11-21T23:54:51): SwitchTo() not switching to current
2009-11-21 23:55:03.190 Video timing method: SGI OpenGL
2009-11-22 00:00:07.402 RingBuf(/var/lib/mythtv/livetv/29007_20091122000000.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/livetv/29007_20091122000000.mpg'.
2009-11-22 00:00:07.403 NVP(2), Error: JumpToProgram's OpenFile failed.
2009-11-22 00:00:07.403 NVP(2), Error: Unknown recorder error, exiting decoder
2009-11-22 00:00:07.413 ~OpenGLVideoSync() -- closing opengl vsync
2009-11-22 00:00:07.619 TV: Attempting to change from Watching WatchingLiveTV to None

```/var/lib/mythtv/livetv contains three files, all 0 Bytes long:
```

root@mythtv-desktop:/var/lib/mythtv/livetv# ls -la
total 4
drwxrwsr-x  2 mythtv mythtv   99 2009-11-22 00:02 .
drwxr-xr-x 13 root   root   4096 2009-10-28 21:28 ..
-rw-r--r--  1 mythtv mythtv    0 2009-11-21 23:55 29007_20091121235502.mpg
-rw-r--r--  1 mythtv mythtv    0 2009-11-22 00:00 29007_20091122000000.mpg
-rw-r--r--  1 mythtv mythtv    0 2009-11-21 23:31 29011_20091121233134.mpg
root@mythtv-desktop:/var/lib/mythtv/livetv#

```Both DVB cards worked fine in mythbuntu 9.04 and after an update to 9.10:
```

root@mythtv-desktop:/var/lib# dmesg | grep DVB
[    5.755866] DVB: registering new adapter (TT-Budget-S-1401 PCI)
[    5.854556] DVB: registering adapter 0 frontend 0 (Philips TDA10086 DVB-S)...
[    5.854646] DVB: registering new adapter (TT-Budget-S-1401 PCI)
[    5.905810] DVB: registering adapter 1 frontend 0 (Philips TDA10086 DVB-S)...

```I searched Google, did not found a solution.

Thanks, -MN

---

### Post by Morgennebel on 2009-11-25
Back to 9.04 and everything works again like a charm :-(

---

