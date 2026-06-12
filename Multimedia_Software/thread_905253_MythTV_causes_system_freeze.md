---
title: "MythTV causes system freeze"
date: 2008-08-30
forum: Multimedia Software
---

### Post by rich86 on 2008-08-30
Hi, i have been having this problem for a while now and i thought it was about time i posted a thread to see if anyone knows of a solution.
I am running Ubuntu 8.04.1 on my desktop pc with a myth frontend/backend set-up running so i can record and what some tv every now and again. I have an MSI usb tuner than and all was working ok on 7.10 but every now and again i get complete system freezes when changing channel or trying to bring up the tv guide while watching live tv. The only way out is to hit the reset button and do a reboot.
It seems to be recording tv in the background ok and i can watch one channel continuously without any problems its just when i try to flick around some channels or open the tv guide i have had problems.

Ignore the lirc errors they are to avoid a double key press issue i was having with my remote control.
Here is the frontend log of the last crash: **(this crash was when changing through channels)**
```
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
2008-08-29 22:30:52.294 NVP: prebuffering pause
2008-08-29 22:30:52.389 WriteAudio: buffer underrun
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
2008-08-29 22:31:06.122 New DB connection, total: 4
2008-08-29 22:31:06.130 Connected to database 'mythconverg' at host: localhost
2008-08-29 22:31:09.392 NVP: Prebuffer wait timed out 10 times.
2008-08-29 22:31:10.993 NVP: Prebuffer wait timed out 10 times.
2008-08-29 22:31:11.882 AFD: Opened codec 0x9163680, id(MPEG2VIDEO) type(Video)
2008-08-29 22:31:11.882 AFD: codec MP3 has 2 channels
2008-08-29 22:31:11.882 AFD: Opened codec 0x94b48c0, id(MP3) type(Audio)
2008-08-29 22:31:11.883 AFD: Opened codec 0xa47a0f0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-29 22:31:11.883 AFD: codec MP3 has 0 channels
2008-08-29 22:31:11.883 AFD: Opened codec 0x9b417e0, id(MP3) type(Audio)
```

And the backend log:
```
2008-08-29 22:31:06.988 New DB connection, total: 2
2008-08-29 22:31:06.991 Connected to database 'mythconverg' at host: localhost
2008-08-29 22:31:06.997 Current Schema Version: 1214
2008-08-29 22:31:07.054 Preview Error: Previewer file '/media/data/other docs/mythtv/Recorded/1001_20080829223051.mpg' is not valid.
2008-08-29 22:31:07.058 Preview Error: Run() file not local: '/media/data/other docs/mythtv/Recorded/1001_20080829223051.mpg'
2008-08-29 22:31:07.085 Preview Error: Preview process not ok.
			fileinfo(/media/data/other docs/mythtv/Recorded/1001_20080829223051.mpg.png) exists: 0 readable: 0 size: 0
2008-08-29 22:31:07.877 Finished recording Newsnight: channel 1002
2008-08-29 22:31:07.963 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-29 22:31:07.979 Reschedule requested for id -1.
2008-08-29 22:31:08.299 Scheduled 8 items in 0.3 = 0.14 match + 0.17 place
2008-08-29 22:31:08.669 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-29 22:31:08.677 Empty LocalHostName.
2008-08-29 22:31:08.687 Using localhost value of richards
QSettings::sync: filename is null/empty
2008-08-29 22:31:08.732 New DB connection, total: 1
2008-08-29 22:31:08.743 Connected to database 'mythconverg' at host: localhost
2008-08-29 22:31:08.756 Closing DB connection named 'DBManager0'
2008-08-29 22:31:08.758 Connected to database 'mythconverg' at host: localhost
QSettings::sync: filename is null/empty
2008-08-29 22:31:08.779 New DB connection, total: 2
2008-08-29 22:31:08.781 Connected to database 'mythconverg' at host: localhost
2008-08-29 22:31:08.799 Current Schema Version: 1214
2008-08-29 22:31:08.855 Preview Error: Previewer file '/media/data/other docs/mythtv/Recorded/1002_20080829223104.mpg' is not valid.
2008-08-29 22:31:08.859 Preview Error: Run() file not local: '/media/data/other docs/mythtv/Recorded/1002_20080829223104.mpg'
2008-08-29 22:31:08.882 Preview Error: Preview process not ok.
			fileinfo(/media/data/other docs/mythtv/Recorded/1002_20080829223104.mpg.png) exists: 0 readable: 0 size: 0

---this is after the reboot-----
2008-08-29 22:33:51.221 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-29 22:33:51.318 Empty LocalHostName.
2008-08-29 22:33:51.321 Using localhost value of richards
```

Here are logs of another crash, this time when trying to look at tv guide while in livetv: frontend
```
2008-08-25 19:44:00.023 DPMS Deactivated 
2008-08-25 19:44:00.059 New DB connection, total: 3
2008-08-25 19:44:00.060 Connected to database 'mythconverg' at host: localhost
2008-08-25 19:44:00.140 NVP: Disabling Audio, params(-1,2,44100)
2008-08-25 19:44:00.259 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
LircClient warning: attempt to convert 'echo '' > /dev/null' to a key sequence failed. Fix your key mappings.
2008-08-25 19:44:00.517 OSD Theme Dimensions W: 640 H: 480
2008-08-25 19:44:02.411 TV: Changing from None to WatchingLiveTV
2008-08-25 19:44:02.429 Realtime priority would require SUID as root.
2008-08-25 19:44:02.521 Video timing method: USleep with busy wait
2008-08-25 19:44:04.651 NVP: Prebuffer wait timed out 10 times.
2008-08-25 19:44:05.587 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-25 19:44:05.896 AFD: Opened codec 0x91bed30, id(MPEG2VIDEO) type(Video)
2008-08-25 19:44:05.896 AFD: codec MP3 has 2 channels
2008-08-25 19:44:05.896 AFD: Opened codec 0x9f99130, id(MP3) type(Audio)
2008-08-25 19:44:05.898 AFD: Opened codec 0x9f994b0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-25 19:44:05.898 AFD: codec MP3 has 0 channels
2008-08-25 19:44:05.898 AFD: Opened codec 0x9f99830, id(MP3) type(Audio)
2008-08-25 19:44:05.987 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-25 19:44:05.987 Opening ALSA audio device 'default'.
2008-08-25 19:44:06.000 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2008-08-25 19:44:06.082 Mixer unable to find control PCM
2008-08-25 19:44:06.083 Mixer unable to find control PCM
2008-08-25 19:44:06.085 NVP: Enabling Audio
```

backend:
```
2008-08-25 19:43:58.581 adding: richards as a client (events: 1)
2008-08-25 19:43:58.600 MainServer::HandleAnnounce Playback
2008-08-25 19:43:58.602 adding: richards as a client (events: 0)
2008-08-25 19:43:58.620 TVRec(3): Changing from None to WatchingLiveTV
2008-08-25 19:43:58.646 TVRec(3): HW Tuner: 3->3
2008-08-25 19:43:59.962 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 8 min
2008-08-25 19:44:00.352 Finished recording Reading and Leeds "Best Bits": channel 1007
2008-08-25 19:44:02.044 Finished recording Reading and Leeds "Best Bits": channel 1007
2008-08-25 19:44:02.203 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 8 min
2008-08-25 19:44:02.883 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-25 19:44:02.891 Empty LocalHostName.
2008-08-25 19:44:02.897 Using localhost value of richards
QSettings::sync: filename is null/empty
2008-08-25 19:44:02.918 New DB connection, total: 1
2008-08-25 19:44:02.928 Connected to database 'mythconverg' at host: localhost
2008-08-25 19:44:02.941 Closing DB connection named 'DBManager0'
2008-08-25 19:44:02.987 Connected to database 'mythconverg' at host: localhost
QSettings::sync: filename is null/empty
2008-08-25 19:44:03.016 New DB connection, total: 2
2008-08-25 19:44:03.018 Connected to database 'mythconverg' at host: localhost
2008-08-25 19:44:03.026 Current Schema Version: 1214
2008-08-25 19:44:03.076 Preview Error: Previewer file '/media/data/other docs/mythtv/Recorded/1007_20080825194358.mpg' is not valid.
2008-08-25 19:44:03.079 Preview Error: Run() file not local: '/media/data/other docs/mythtv/Recorded/1007_20080825194358.mpg'
2008-08-25 19:44:03.108 Preview Error: Preview process not ok.
			fileinfo(/media/data/other docs/mythtv/Recorded/1007_20080825194358.mpg.png) exists: 0 readable: 0 size: 0
```


From these is appears to be caused by preview process errors but anyone know how to resolve and what is really going on!?

Hope this is posted in the correct place.
Thanks in advance,
Rich

---

### Post by rich86 on 2008-09-01
bump, anyone got any ideas?

---

