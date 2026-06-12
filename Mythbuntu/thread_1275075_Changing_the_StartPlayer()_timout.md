---
title: "Changing the StartPlayer() timout"
date: 2009-09-25
forum: Mythbuntu
---

### Post by stevenc2 on 2009-09-25
I'm having issues when I try to watch an in progress rerecording (watching something once it's fully recorded works fine).  It goes black and then after a while goes back to the Menu on the front end.  I have an older computer so I'm thinking it might just take a little while for it to get up and running.  I found this person who was able to change the timeout from 20 seconds to 40 seconds, but don't know how to do it myself.
 
[http://www.mail-archive.com/mythtv-dev@mythtv.org/msg14538.html](http://www.mail-archive.com/mythtv-dev@mythtv.org/msg14538.html)
 
I'd be fine waiting around for a minute or two for it to start up, anyone know how to change a setting to make the timeout longer?

---

### Post by SiHa on 2009-09-25
Not sure it's related to the problem in the link - that seems to be something to do with the RingBuffer, AFAIK, Myth doesn't use this from 0.21.
Do your Frontend / Backend logs show anything? (they should be in **/var/log/mythtv/**)

---

### Post by stevenc2 on 2009-09-25
> **SiHa said:**
> Not sure it's related to the problem in the link - that seems to be something to do with the RingBuffer, AFAIK, Myth doesn't use this from 0.21.
Do your Frontend / Backend logs show anything? (they should be in **/var/log/mythtv/**)
 
The log is below. It's an issue with the front end only when I try to watch an currently recording program. If I try to watch from another computer using MythTVPlayer on windows it works fine. I'm guessing it has something to do with my sound card, but find it odd that the sounds works everywhere else. I can even watch a previously recorded program when another is recording. Sounds it doesn't seem like it's because my computer is on the older side. Thought it would be easier and quicker to just try to change the timeout see if that works.
 
> 2009-09-24 21:42:26.330 TV: Attempting to change from None to WatchingRecording
2009-09-24 21:42:26.468 Using protocol version 40
2009-09-24 21:42:26.495 DPMS Deactivated 
2009-09-24 21:42:27.030 AFD: Opened codec 0x8320dd0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:42:27.030 AFD: codec MP2 has 2 channels
2009-09-24 21:42:27.031 AFD: Opened codec 0x8d1c770, id(MP2) type(Audio)
2009-09-24 21:42:27.048 Opening audio device 'default'. ch 2(2) sr 48000
2009-09-24 21:42:27.048 Opening ALSA audio device 'default'.
2009-09-24 21:42:27.110 Mixer unable to find control Master
2009-09-24 21:42:27.110 Mixer unable to find control Master
2009-09-24 21:42:27.129 Mixer unable to find control PCM
2009-09-24 21:42:27.130 Mixer unable to find control PCM
2009-09-24 21:42:27.130 Mixer unable to find control PCM
2009-09-24 21:42:46.703 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-09-24 21:42:46.707 TV: Changing from None to WatchingRecording
2009-09-24 21:42:46.714 TV: Attempting to change from WatchingRecording to None
2009-09-24 21:42:50.382 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-09-24 21:42:50.598 OSD Theme Dimensions W: 640 H: 480
2009-09-24 21:42:52.050 Realtime priority would require SUID as root.
2009-09-24 21:42:52.168 Video timing method: USleep with busy wait
2009-09-24 21:42:52.237 TV: Changing from WatchingRecording to None
2009-09-24 21:42:52.294 DPMS Reactivated.
2009-09-24 21:42:57.045 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2009-09-24 21:42:58.843 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:42:58.843 AFD: codec MP2 has 2 channels
2009-09-24 21:42:58.843 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:42:59.111 TV: Attempting to change from None to WatchingRecording
2009-09-24 21:42:59.120 Using protocol version 40
2009-09-24 21:42:59.148 DPMS Deactivated 
2009-09-24 21:42:59.586 AFD: Opened codec 0x8365560, id(MPEG2VIDEO) type(Video)
2009-09-24 21:42:59.586 AFD: codec MP2 has 2 channels
2009-09-24 21:42:59.586 AFD: Opened codec 0x85bab20, id(MP2) type(Audio)
2009-09-24 21:42:59.589 Opening audio device 'default'. ch 2(2) sr 48000
2009-09-24 21:42:59.590 Opening ALSA audio device 'default'.
2009-09-24 21:42:59.634 Mixer unable to find control Master
2009-09-24 21:42:59.635 Mixer unable to find control Master
2009-09-24 21:42:59.635 Mixer unable to find control PCM
2009-09-24 21:42:59.635 Mixer unable to find control PCM
2009-09-24 21:42:59.635 Mixer unable to find control PCM
2009-09-24 21:43:19.227 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-09-24 21:43:19.229 TV: Changing from None to WatchingRecording
2009-09-24 21:43:19.235 TV: Attempting to change from WatchingRecording to None
2009-09-24 21:43:23.623 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-09-24 21:43:23.809 OSD Theme Dimensions W: 640 H: 480
2009-09-24 21:43:24.810 Realtime priority would require SUID as root.
2009-09-24 21:43:24.904 Video timing method: USleep with busy wait
2009-09-24 21:43:24.989 TV: Changing from WatchingRecording to None
2009-09-24 21:43:25.098 DPMS Reactivated.
2009-09-24 21:43:25.305 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:25.305 AFD: codec MP2 has 2 channels
2009-09-24 21:43:25.305 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:25.886 AFD: Opened codec 0x8ff7390, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:25.886 AFD: codec MP2 has 2 channels
2009-09-24 21:43:25.887 AFD: Opened codec 0x8f5c4e0, id(MP2) type(Audio)
2009-09-24 21:43:27.054 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:27.054 AFD: codec MP2 has 2 channels
2009-09-24 21:43:27.054 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:34.695 AFD: Opened codec 0x8ff7390, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:34.695 AFD: codec MP2 has 2 channels
2009-09-24 21:43:34.695 AFD: Opened codec 0x8f5c4e0, id(MP2) type(Audio)
2009-09-24 21:43:37.756 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:37.777 AFD: codec MP2 has 2 channels
2009-09-24 21:43:37.777 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:40.461 AFD: Opened codec 0x8ff7390, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:40.461 AFD: codec MP2 has 2 channels
2009-09-24 21:43:40.461 AFD: Opened codec 0x8f5c4e0, id(MP2) type(Audio)
2009-09-24 21:43:41.612 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:41.613 AFD: codec MP2 has 2 channels
2009-09-24 21:43:41.613 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:46.801 AFD: Opened codec 0x8ff7390, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:46.801 AFD: codec MP2 has 2 channels
2009-09-24 21:43:46.827 AFD: Opened codec 0x8f5c4e0, id(MP2) type(Audio)
2009-09-24 21:43:51.348 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:51.348 AFD: codec MP2 has 2 channels
2009-09-24 21:43:51.349 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:51.799 AFD: Opened codec 0x8ff7390, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:51.799 AFD: codec MP2 has 2 channels
2009-09-24 21:43:51.799 AFD: Opened codec 0x8f5c4e0, id(MP2) type(Audio)
2009-09-24 21:43:53.629 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:53.630 AFD: codec MP2 has 2 channels
2009-09-24 21:43:53.630 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:56.223 AFD: Opened codec 0x8ff7390, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:56.224 AFD: codec MP2 has 2 channels
2009-09-24 21:43:56.224 AFD: Opened codec 0x8f5c4e0, id(MP2) type(Audio)
2009-09-24 21:43:56.899 AFD: Opened codec 0x8f5c4e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:56.899 AFD: codec MP2 has 2 channels
2009-09-24 21:43:56.899 AFD: Opened codec 0x8ff7390, id(MP2) type(Audio)
2009-09-24 21:43:58.580 TV: Attempting to change from None to WatchingRecording
2009-09-24 21:43:58.589 Using protocol version 40
2009-09-24 21:43:58.606 DPMS Deactivated 
2009-09-24 21:43:58.870 AFD: Opened codec 0x8491610, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:58.870 AFD: codec MP2 has 2 channels
2009-09-24 21:43:58.871 AFD: Opened codec 0x8320dd0, id(MP2) type(Audio)
2009-09-24 21:43:58.885 Opening audio device 'default'. ch 2(2) sr 48000
2009-09-24 21:43:58.886 Opening ALSA audio device 'default'.
2009-09-24 21:43:58.914 Mixer unable to find control Master
2009-09-24 21:43:58.914 Mixer unable to find control Master
2009-09-24 21:43:58.914 Mixer unable to find control PCM
2009-09-24 21:43:58.914 Mixer unable to find control PCM
2009-09-24 21:43:58.915 Mixer unable to find control PCM
2009-09-24 21:43:59.344 AFD: Opened codec 0x8c67f00, id(MPEG2VIDEO) type(Video)
2009-09-24 21:43:59.344 AFD: codec MP2 has 2 channels
2009-09-24 21:43:59.345 AFD: Opened codec 0x8c68280, id(MP2) type(Audio)
2009-09-24 21:44:00.677 NVP: prebuffering pause
2009-09-24 21:44:04.578 NVP: prebuffering pause
2009-09-24 21:44:07.037 NVP: prebuffering pause
2009-09-24 21:44:08.344 NVP: prebuffering pause
2009-09-24 21:44:11.294 NVP: prebuffering pause
2009-09-24 21:44:13.816 NVP: prebuffering pause
2009-09-24 21:44:16.459 NVP: prebuffering pause
2009-09-24 21:44:18.105 NVP: prebuffering pause
2009-09-24 21:44:18.719 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-09-24 21:44:18.721 TV: Changing from None to WatchingRecording
2009-09-24 21:44:18.774 TV: Attempting to change from WatchingRecording to None
2009-09-24 21:44:35.167 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-09-24 21:44:35.361 OSD Theme Dimensions W: 640 H: 480
2009-09-24 21:44:37.307 Realtime priority would require SUID as root.
2009-09-24 21:44:37.432 Video timing method: USleep with busy wait
2009-09-24 21:44:37.573 TV: Changing from WatchingRecording to None
2009-09-24 21:44:37.866 DPMS Reactivated.
2009-09-24 21:44:39.550 AFD: Opened codec 0x99c4240, id(MPEG2VIDEO) type(Video)
2009-09-24 21:44:39.550 AFD: codec MP2 has 2 channels
2009-09-24 21:44:39.551 AFD: Opened codec 0x843bd80, id(MP2) type(Audio)
2009-09-24 21:44:40.139 AFD: Opened codec 0x8353c00, id(MPEG2VIDEO) type(Video)
2009-09-24 21:44:40.139 AFD: codec MP2 has 2 channels
2009-09-24 21:44:40.139 AFD: Opened codec 0x8353f80, id(MP2) type(Audio)
2009-09-24 21:44:41.203 TV: Attempting to change from None to WatchingRecording
2009-09-24 21:44:41.213 DPMS Deactivated 
2009-09-24 21:44:41.216 Using protocol version 40
2009-09-24 21:44:41.567 AFD: Opened codec 0x836c550, id(MPEG2VIDEO) type(Video)
2009-09-24 21:44:41.568 AFD: codec MP2 has 2 channels
2009-09-24 21:44:41.568 AFD: Opened codec 0x836c8c0, id(MP2) type(Audio)
2009-09-24 21:44:41.576 Opening audio device 'default'. ch 2(2) sr 48000
2009-09-24 21:44:41.577 Opening ALSA audio device 'default'.
2009-09-24 21:44:41.598 Mixer unable to find control Master
2009-09-24 21:44:41.614 Mixer unable to find control Master
2009-09-24 21:44:41.615 Mixer unable to find control PCM
2009-09-24 21:44:41.615 Mixer unable to find control PCM
2009-09-24 21:44:41.615 Mixer unable to find control PCM
2009-09-24 21:44:41.943 AFD: Opened codec 0x99d8370, id(MPEG2VIDEO) type(Video)
2009-09-24 21:44:41.943 AFD: codec MP2 has 2 channels
2009-09-24 21:44:41.943 AFD: Opened codec 0x8355700, id(MP2) type(Audio)
2009-09-24 21:45:00.061 NVP: prebuffering pause
2009-09-24 21:45:01.327 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-09-24 21:45:01.329 TV: Changing from None to WatchingRecording
2009-09-24 21:45:01.334 TV: Attempting to change from WatchingRecording to None
2009-09-24 21:45:14.276 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-09-24 21:45:14.689 OSD Theme Dimensions W: 640 H: 480
2009-09-24 21:45:15.993 Realtime priority would require SUID as root.
2009-09-24 21:45:16.088 Video timing method: USleep with busy wait
2009-09-24 21:45:16.192 TV: Changing from WatchingRecording to None
2009-09-24 21:45:16.339 DPMS Reactivated.
2009-09-24 21:45:20.594 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/status-ui.xml
2009-09-24 21:45:46.702 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2009-09-24 21:45:48.422 AFD: Opened codec 0x8c6a1e0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:45:48.422 AFD: codec MP2 has 2 channels
2009-09-24 21:45:48.423 AFD: Opened codec 0x8d73370, id(MP2) type(Audio)
2009-09-24 21:45:51.226 AFD: Opened codec 0x8d6c850, id(MPEG2VIDEO) type(Video)
2009-09-24 21:45:51.226 AFD: codec MP2 has 2 channels
2009-09-24 21:45:51.226 AFD: Opened codec 0x8d6cbc0, id(MP2) type(Audio)
2009-09-24 21:45:52.508 AFD: Opened codec 0x8d3de20, id(MPEG2VIDEO) type(Video)
2009-09-24 21:45:52.508 AFD: codec MP2 has 2 channels
2009-09-24 21:45:52.508 AFD: Opened codec 0x8c7e1e0, id(MP2) type(Audio)
2009-09-24 21:45:53.648 TV: Attempting to change from None to WatchingRecording
2009-09-24 21:45:53.659 Using protocol version 40
2009-09-24 21:45:53.753 DPMS Deactivated 
2009-09-24 21:45:54.008 AFD: Opened codec 0x99d6520, id(MPEG2VIDEO) type(Video)
2009-09-24 21:45:54.008 AFD: codec MP2 has 2 channels
2009-09-24 21:45:54.008 AFD: Opened codec 0x8c7e1e0, id(MP2) type(Audio)
2009-09-24 21:45:54.028 Opening audio device 'default'. ch 2(2) sr 48000
2009-09-24 21:45:54.028 Opening ALSA audio device 'default'.
2009-09-24 21:45:54.058 Mixer unable to find control Master
2009-09-24 21:45:54.058 Mixer unable to find control Master
2009-09-24 21:45:54.064 Mixer unable to find control PCM
2009-09-24 21:45:54.064 Mixer unable to find control PCM
2009-09-24 21:45:54.065 Mixer unable to find control PCM
2009-09-24 21:45:54.378 AFD: Opened codec 0x8d2d5c0, id(MPEG2VIDEO) type(Video)
2009-09-24 21:45:54.378 AFD: codec MP2 has 2 channels
2009-09-24 21:45:54.378 AFD: Opened codec 0x8d2da40, id(MP2) type(Audio)
2009-09-24 21:46:01.852 NVP: prebuffering pause
2009-09-24 21:46:05.379 NVP: prebuffering pause
2009-09-24 21:46:08.767 NVP: prebuffering pause
2009-09-24 21:46:10.910 NVP: prebuffering pause
2009-09-24 21:46:11.993 NVP: prebuffering pause


---

