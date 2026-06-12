---
title: "Attempting to Watch In Progress Recording Crashes Frontend"
date: 2008-03-23
forum: Mythbuntu
---

### Post by stevenc413 on 2008-03-23
Almost every time I try to watch an in progress recording under Manage Recordings page.  The screen goes black for a little bit then crashes.  This started a few weeks ago, and I don't remember fooling around with anything at that time that would have caused this.  Sometimes, if the screen goes black for a little while I press the skip button it'll start playing the in progress recording, but sometimes that trick doesn't work.  Luckily the backend doesn't crash so at least it keeps recording!  Any help would be great appreciated as multiple searches of this forum and the internet hasn't turned up anything!  This is what the Front-End says when I run it from the command line:
```

@mythtvbox:~$ mythfrontend
2008-03-23 20:45:59.986 Using runtime prefix = /usr
2008-03-23 20:46:00.006 Gnome-Screensaver support enabled
2008-03-23 20:46:00.007 DPMS is disabled.
2008-03-23 20:46:00.053 New DB connection, total: 1
2008-03-23 20:46:00.089 Connected to database 'mythconverg' at host: localhost
2008-03-23 20:46:00.092 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-23 20:46:00.098 Using screen 0, 1024x768 at 0,0
2008-03-23 20:46:00.202 Current Schema Version: 1160
2008-03-23 20:46:00.266 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-03-23 20:46:00.266 Enabled verbose msgs:  important general
2008-03-23 20:46:02.923 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-23 20:46:02.930 Using screen 0, 1024x768 at 0,0
2008-03-23 20:46:03.008 Switching to square mode (MythCenter)
2008-03-23 20:46:03.575 Using the Qt painter
2008-03-23 20:46:04.784 Joystick disabled.
2008-03-23 20:46:10.322 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-23 20:46:11.455 Registering Internal as a media playback plugin.
2008-03-23 20:46:11.862 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-23 20:46:11.865 Registering MythDVD VCD Media Handler as a media handler ext()
2008-03-23 20:46:12.226 Registering MythGallery Media Handler 1/2 as a media handler ext()
2008-03-23 20:46:12.227 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2008-03-23 20:46:13.378 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-23 20:46:13.379 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.55:5060 NAT address 192.168.2.55
SIP: Cannot register; proxy, username or password not set
2008-03-23 20:46:21.778 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-03-23 20:46:22.814 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-23 20:46:22.817 Using protocol version 31
2008-03-23 20:46:25.318 New DB connection, total: 2
2008-03-23 20:46:25.320 Connected to database 'mythconverg' at host: localhost
0: start_time: 0.036 duration: 250.345
1: start_time: 0.026 duration: 250.325
stream: start_time: 0.289 duration: 2781.723 bitrate=5191 kb/s
2008-03-23 20:46:25.565 AFD: Opened codec 0x82bd240, id(MPEG2VIDEO) type(Video)
2008-03-23 20:46:25.631 TV: Attempting to change from None to WatchingRecording
2008-03-23 20:46:25.869 Using protocol version 31
2008-03-23 20:46:26.129 AFD: Opened codec 0x81de5b0, id(MP2) type(Audio)
0: start_time: 0.036 duration: 250.549
1: start_time: 0.026 duration: 250.523
stream: start_time: 0.289 duration: 2783.992 bitrate=5191 kb/s
2008-03-23 20:46:28.650 AFD: Opened codec 0xb08dd900, id(MPEG2VIDEO) type(Video)
2008-03-23 20:46:28.651 AFD: Opened codec 0xb08ddcf0, id(MP2) type(Audio)
2008-03-23 20:46:28.889 Opening ALSA audio device 'default'.
2008-03-23 20:46:46.349 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-03-23 20:46:46.358 TV: Changing from None to WatchingRecording
2008-03-23 20:46:46.431 TV: Attempting to change from WatchingRecording to None
2008-03-23 20:46:52.747 VideoOutputXv: XvMCTex: Init failed
2008-03-23 20:46:52.755 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  142
  Minor opcode:  14
  Resource id:  0x197
2008-03-23 20:46:55.139 Realtime priority would require SUID as root.
2008-03-23 20:46:55.342 Video timing method: USleep with busy wait
2008-03-23 20:46:55.525 TV: Changing from WatchingRecording to None
0: start_time: 0.036 duration: 253.117
1: start_time: 0.026 duration: 253.087
stream: start_time: 0.289 duration: 2812.521 bitrate=5190 kb/s
2008-03-23 20:46:56.373 AFD: Opened codec 0x83ab5e0, id(MPEG2VIDEO) type(Video)
2008-03-23 20:46:56.373 AFD: Opened codec 0x86a9bc0, id(MP2) type(Audio)
0: start_time: 0.036 duration: 253.219
1: start_time: 0.026 duration: 253.197
stream: start_time: 0.289 duration: 2813.655 bitrate=5190 kb/s
2008-03-23 20:46:57.585 AFD: Opened codec 0x83ab5e0, id(MPEG2VIDEO) type(Video)
2008-03-23 20:46:57.585 AFD: Opened codec 0x86a9bc0, id(MP2) type(Audio)
2008-03-23 20:46:58.824 NVP: prebuffering pause
2008-03-23 20:46:59.897 NVP: prebuffering pause
2008-03-23 20:47:01.130 NVP: prebuffering pause
2008-03-23 20:47:02.368 NVP: prebuffering pause
2008-03-23 20:47:03.990 NVP: prebuffering pause
2008-03-23 20:47:07.307 NVP: prebuffering pause
2008-03-23 20:47:08.941 NVP: prebuffering pause
2008-03-23 20:47:10.319 NVP: prebuffering pause
Destroying SipFsm object 




```

---

### Post by foxbuntu on 2008-04-02
One thing you might try:

Exit the frontend then start it back up from terminal:
```
mythfrontend -O ThemePainter=OpenGL
```

Also, is you machine up-to-date? (video drivers espically?)

---

