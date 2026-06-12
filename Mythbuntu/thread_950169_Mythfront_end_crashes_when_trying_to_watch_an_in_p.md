---
title: "Mythfront end crashes when trying to watch an in progress recording"
date: 2008-10-16
forum: Mythbuntu
---

### Post by stevenc413 on 2008-10-16
Hello,

Forgive my ignorance here.  I am pretty familiar with computers in general, but a real newbie when it comes to linux/ubuntu.  A while back my sound card died on a perfectly working mythbuntu setup. I only figured out it was a dead sound card after I installed the latest version of mythbuntu.  I went out and bought a new one and it installed fine, but now the front end seems unstable when I try to watch a recording as it is being recorded.  Watching a recording after it has already finished recording always works just fine, but when I try to watch an in progress recording it occasionally works, but also sometimes goes to a blackscreen for 30 seconds before the show starts.  Sometimes the front end will crash after the blackscreen has been on there for a little while and sometimes the program will start after 30 seconds just fine, but the when I try to pause it or skip commercials I learn that it has stopped responding to the remote.  Anyone know what could be causing this?  Tonight when I was watching Grey's Anatomomy with my wife we started it about 20 minutes into the program and the screen was black for the first 30 seconds and the program finally started, but when I tried to pause it a few minutes in, nothing happened.  I continued watching it until the commercials came on and I tried to skip the commercials and the front end crashed to the desktop.  I restarted the front end and when I tried to restart Grey's the front end crashed again.  Does anyone know what could be causing this?  I do apologize if I have given too much information, or not the information needed to diagnose the problem, but I would really appreciate any help or pointers anyone has.  This is the log from the front end, since most of it is gibberish to me I have to post the whole thing from 9pm on.  If you need the backend log let me know I can post that as well.

```
2008-10-16 20:21:03.394 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-10-16 20:21:05.063 AFD: Opened codec 0x9dc5320, id(MPEG2VIDEO) type(Video)
2008-10-16 20:21:05.063 AFD: codec MP2 has 2 channels
2008-10-16 20:21:05.063 AFD: Opened codec 0x8c03d30, id(MP2) type(Audio)
2008-10-16 20:21:07.614 AFD: Opened codec 0x9dc5320, id(MPEG2VIDEO) type(Video)
2008-10-16 20:21:07.614 AFD: codec MP2 has 2 channels
2008-10-16 20:21:07.614 AFD: Opened codec 0x8c03d30, id(MP2) type(Audio)
2008-10-16 20:21:09.944 AFD: Opened codec 0x9dc5320, id(MPEG2VIDEO) type(Video)
2008-10-16 20:21:09.944 AFD: codec MP2 has 2 channels
2008-10-16 20:21:09.944 AFD: Opened codec 0x9c295d0, id(MP2) type(Audio)
2008-10-16 20:21:10.578 AFD: Opened codec 0x9dc5320, id(MPEG2VIDEO) type(Video)
2008-10-16 20:21:10.578 AFD: codec MP2 has 2 channels
2008-10-16 20:21:10.578 AFD: Opened codec 0x8c03d30, id(MP2) type(Audio)
2008-10-16 20:21:10.742 TV: Attempting to change from None to WatchingPreRecorded
2008-10-16 20:21:10.769 DPMS Deactivated 
2008-10-16 20:21:11.136 AFD: Opened codec 0xa32d0c0, id(MPEG2VIDEO) type(Video)
2008-10-16 20:21:11.137 AFD: codec MP2 has 2 channels
2008-10-16 20:21:11.137 AFD: Opened codec 0x8d03050, id(MP2) type(Audio)
2008-10-16 20:21:11.151 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-16 20:21:11.152 Opening ALSA audio device 'default'.
2008-10-16 20:21:11.174 Mixer unable to find control Master
2008-10-16 20:21:11.174 Mixer unable to find control Master
2008-10-16 20:21:11.175 Mixer unable to find control PCM
2008-10-16 20:21:11.175 Mixer unable to find control PCM
2008-10-16 20:21:11.176 Mixer unable to find control PCM
2008-10-16 20:21:11.245 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-10-16 20:21:11.262 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-16 20:21:11.412 OSD Theme Dimensions W: 640 H: 480
2008-10-16 20:21:12.725 TV: Changing from None to WatchingPreRecorded
2008-10-16 20:21:12.731 FilterManager: failed to load filter 'none', no such filter exists
2008-10-16 20:21:12.732 Couldn't load deinterlace filter none
2008-10-16 20:21:12.732 Realtime priority would require SUID as root.
2008-10-16 20:21:12.830 Video timing method: USleep with busy wait
2008-10-16 20:21:13.910 DPMS Reactivated.
2008-10-16 20:21:15.037 DPMS Deactivated 
2008-10-16 20:21:18.292 DPMS Reactivated.
2008-10-16 20:21:33.655 DPMS Deactivated 
2008-10-16 20:23:00.379 WriteAudio: buffer underrun
2008-10-16 20:23:00.402 WriteAudio: buffer underrun
2008-10-16 20:29:43.634 Mixer unable to find control PCM
2008-10-16 20:29:43.635 Mixer unable to find control PCM
2008-10-16 20:29:44.518 Mixer unable to find control PCM
2008-10-16 20:29:44.518 Mixer unable to find control PCM
2008-10-16 20:37:58.544 DPMS Reactivated.
2008-10-16 20:38:16.069 WriteAudio: buffer underrun
2008-10-16 20:38:16.091 WriteAudio: buffer underrun
2008-10-16 20:38:25.606 DPMS Deactivated 
2008-10-16 20:41:25.285 Mixer unable to find control PCM
2008-10-16 20:41:25.291 Mixer unable to find control PCM
2008-10-16 20:41:25.424 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 20:41:25.434 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 20:41:26.166 Mixer unable to find control PCM
2008-10-16 20:41:26.167 Mixer unable to find control PCM
2008-10-16 20:42:26.123 DPMS Reactivated.
2008-10-16 20:42:26.786 DPMS Deactivated 
2008-10-16 20:49:25.913 Mixer unable to find control PCM
2008-10-16 20:49:25.915 Mixer unable to find control PCM
2008-10-16 20:49:26.168 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 20:49:26.169 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 20:49:26.845 Mixer unable to find control PCM
2008-10-16 20:49:26.845 Mixer unable to find control PCM
2008-10-16 20:52:05.567 WriteAudio: buffer underrun
2008-10-16 20:52:05.590 WriteAudio: buffer underrun
2008-10-16 20:53:03.672 DPMS Reactivated.
2008-10-16 20:53:05.065 DPMS Deactivated 
2008-10-16 20:53:58.731 WriteAudio: buffer underrun
2008-10-16 20:53:58.748 WriteAudio: buffer underrun
2008-10-16 20:55:22.236 Mixer unable to find control PCM
2008-10-16 20:55:22.237 Mixer unable to find control PCM
2008-10-16 20:55:22.389 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 20:55:23.147 Mixer unable to find control PCM
2008-10-16 20:55:23.148 Mixer unable to find control PCM
2008-10-16 20:56:36.262 DPMS Reactivated.
2008-10-16 20:59:26.258 WriteAudio: buffer underrun
2008-10-16 20:59:26.280 WriteAudio: buffer underrun
2008-10-16 21:00:48.590 DPMS Deactivated 
2008-10-16 21:05:10.517 WriteAudio: buffer underrun
2008-10-16 21:05:10.543 WriteAudio: buffer underrun
2008-10-16 21:08:37.397 WriteAudio: buffer underrun
2008-10-16 21:08:51.770 WriteAudio: buffer underrun
2008-10-16 21:08:52.093 WriteAudio: buffer underrun
2008-10-16 21:08:52.289 WriteAudio: buffer underrun
2008-10-16 21:09:49.219 Mixer unable to find control PCM
2008-10-16 21:09:49.237 Mixer unable to find control PCM
2008-10-16 21:09:50.781 Mixer unable to find control PCM
2008-10-16 21:09:50.782 Mixer unable to find control PCM
2008-10-16 21:09:52.637 Mixer unable to find control PCM
2008-10-16 21:09:52.637 Mixer unable to find control PCM
2008-10-16 21:09:52.806 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:09:53.573 Mixer unable to find control PCM
2008-10-16 21:09:53.573 Mixer unable to find control PCM
2008-10-16 21:09:54.459 Mixer unable to find control PCM
2008-10-16 21:09:54.460 Mixer unable to find control PCM
2008-10-16 21:09:54.689 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 21:09:55.350 Mixer unable to find control PCM
2008-10-16 21:09:55.350 Mixer unable to find control PCM
2008-10-16 21:09:57.030 Mixer unable to find control PCM
2008-10-16 21:09:57.030 Mixer unable to find control PCM
2008-10-16 21:09:57.125 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:09:57.142 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 21:09:57.904 Mixer unable to find control PCM
2008-10-16 21:09:57.904 Mixer unable to find control PCM
2008-10-16 21:09:58.638 Mixer unable to find control PCM
2008-10-16 21:09:58.639 Mixer unable to find control PCM
2008-10-16 21:09:58.808 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:09:58.827 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 21:09:58.829 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 21:09:59.660 Mixer unable to find control PCM
2008-10-16 21:09:59.660 Mixer unable to find control PCM
2008-10-16 21:10:04.032 Mixer unable to find control PCM
2008-10-16 21:10:04.032 Mixer unable to find control PCM
2008-10-16 21:10:04.236 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:10:04.968 Mixer unable to find control PCM
2008-10-16 21:10:04.968 Mixer unable to find control PCM
2008-10-16 21:10:06.231 Mixer unable to find control PCM
2008-10-16 21:10:06.232 Mixer unable to find control PCM
2008-10-16 21:10:06.432 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:10:07.132 Mixer unable to find control PCM
2008-10-16 21:10:07.132 Mixer unable to find control PCM
2008-10-16 21:10:07.772 Mixer unable to find control PCM
2008-10-16 21:10:07.772 Mixer unable to find control PCM
2008-10-16 21:10:07.869 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:10:08.737 Mixer unable to find control PCM
2008-10-16 21:10:08.737 Mixer unable to find control PCM
2008-10-16 21:10:08.879 Mixer unable to find control PCM
2008-10-16 21:10:08.879 Mixer unable to find control PCM
2008-10-16 21:10:09.006 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:10:09.862 Mixer unable to find control PCM
2008-10-16 21:10:09.862 Mixer unable to find control PCM
2008-10-16 21:10:10.199 Mixer unable to find control PCM
2008-10-16 21:10:10.199 Mixer unable to find control PCM
2008-10-16 21:10:10.343 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 21:10:11.118 Mixer unable to find control PCM
2008-10-16 21:10:11.118 Mixer unable to find control PCM
2008-10-16 21:10:12.557 Mixer unable to find control PCM
2008-10-16 21:10:12.558 Mixer unable to find control PCM
2008-10-16 21:10:12.708 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:10:13.495 Mixer unable to find control PCM
2008-10-16 21:10:13.495 Mixer unable to find control PCM
2008-10-16 21:10:14.243 Mixer unable to find control PCM
2008-10-16 21:10:14.243 Mixer unable to find control PCM
2008-10-16 21:10:14.323 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
2008-10-16 21:10:15.193 Mixer unable to find control PCM
2008-10-16 21:10:15.194 Mixer unable to find control PCM
2008-10-16 21:10:15.626 Mixer unable to find control PCM
2008-10-16 21:10:15.626 Mixer unable to find control PCM
2008-10-16 21:10:16.559 Mixer unable to find control PCM
2008-10-16 21:10:16.560 Mixer unable to find control PCM
2008-10-16 21:10:37.808 DPMS Reactivated.
2008-10-16 21:10:39.921 WriteAudio: buffer underrun
2008-10-16 21:10:40.018 DPMS Deactivated 
2008-10-16 21:10:47.643 TV: Attempting to change from WatchingPreRecorded to None
2008-10-16 21:10:50.299 TV: Changing from WatchingPreRecorded to None
2008-10-16 21:10:51.911 DPMS Reactivated.
2008-10-16 21:10:54.092 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:10:54.110 AFD: codec MP2 has 2 channels
2008-10-16 21:10:54.135 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:10:55.357 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:10:55.358 AFD: codec MP2 has 2 channels
2008-10-16 21:10:55.358 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:10:56.424 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:10:56.424 AFD: codec MP2 has 2 channels
2008-10-16 21:10:56.424 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:11:00.220 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:11:00.221 AFD: codec MP2 has 2 channels
2008-10-16 21:11:00.221 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:11:04.862 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:11:04.862 AFD: codec MP2 has 2 channels
2008-10-16 21:11:04.862 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:11:09.731 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:11:09.731 AFD: codec MP2 has 2 channels
2008-10-16 21:11:09.732 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:29:48.333 [mpeg2video @ 0xb73b4b88]invalid cbp at 2 21
2008-10-16 21:29:48.341 [mpeg2video @ 0xb73b4b88]Warning MVs not available
2008-10-16 21:29:50.280 AFD: Opened codec 0x8c03d30, id(MPEG2VIDEO) type(Video)
2008-10-16 21:29:50.280 AFD: codec MP2 has 2 channels
2008-10-16 21:29:50.280 AFD: Opened codec 0x8b2e670, id(MP2) type(Audio)
2008-10-16 21:29:52.197 TV: Attempting to change from None to WatchingRecording
2008-10-16 21:29:52.211 DPMS Deactivated 
2008-10-16 21:29:52.270 Using protocol version 40
2008-10-16 21:29:52.701 AFD: Opened codec 0x8e59010, id(MPEG2VIDEO) type(Video)
2008-10-16 21:29:52.701 AFD: codec MP2 has 2 channels
2008-10-16 21:29:52.701 AFD: Opened codec 0x9dc5320, id(MP2) type(Audio)
2008-10-16 21:29:52.713 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-16 21:29:52.730 Opening ALSA audio device 'default'.
2008-10-16 21:29:52.918 Mixer unable to find control Master
2008-10-16 21:29:52.918 Mixer unable to find control Master
2008-10-16 21:29:52.918 Mixer unable to find control PCM
2008-10-16 21:29:52.918 Mixer unable to find control PCM
2008-10-16 21:29:52.918 Mixer unable to find control PCM
2008-10-16 21:30:10.461 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-10-16 21:30:10.472 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-16 21:30:10.719 OSD Theme Dimensions W: 640 H: 480
2008-10-16 21:30:12.465 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-10-16 21:30:12.474 TV: Changing from None to WatchingRecording
2008-10-16 21:30:12.580 FilterManager: failed to load filter 'none', no such filter exists
2008-10-16 21:30:12.580 Couldn't load deinterlace filter none
2008-10-16 21:30:12.581 Realtime priority would require SUID as root.
2008-10-16 21:30:12.678 Video timing method: USleep with busy wait
2008-10-16 21:34:43.549 WriteAudio: buffer underrun
2008-10-16 21:34:43.572 WriteAudio: buffer underrun
Starting mythfrontend.real..
2008-10-16 21:40:10.555 New DB connection, total: 2
2008-10-16 21:40:10.556 Connected to database 'mythconverg' at host: localhost
2008-10-16 21:40:10.563 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-10-16 21:40:10.563 Enabled verbose msgs:  important general
2008-10-16 21:40:16.477 Could not open settings file /home/stevenc413/.mythtv/mysql.txt for writing
2008-10-16 21:40:16.515 Primary screen 0.
2008-10-16 21:40:16.517 Using screen 0, 1024x768 at 0,0
2008-10-16 21:40:16.608 Switching to square mode (MythCenter)
2008-10-16 21:40:17.154 Using the OpenGL painter
2008-10-16 21:40:17.163 JoystickMenuClient Error: Joystick disabled - Failed to read /home/stevenc413/.mythtv/joystickmenurc
2008-10-16 21:40:17.188 lirc init success using configuration file: /home/stevenc413/.mythtv/lircrc
2008-10-16 21:40:24.613 Loading from: /usr/share/mythtv/themes/MythCenter/base.xml
2008-10-16 21:40:24.740 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-10-16 21:40:25.137 Registering Internal as a media playback plugin.
2008-10-16 21:40:25.896 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-10-16 21:40:26.711 Failed to run 'cdrecord --scanbus'
2008-10-16 21:40:26.733 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-10-16 21:40:26.740 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-10-16 21:40:26.863 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.55:5060 NAT address 192.168.2.55
SIP: Cannot register; proxy, username or password not set
2008-10-16 21:40:28.802 Using NV NPOT texture extension
2008-10-16 21:40:51.318 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-16 21:40:51.332 Using protocol version 40
2008-10-16 21:40:53.762 TV: Attempting to change from None to WatchingRecording
2008-10-16 21:40:53.825 Using protocol version 40
2008-10-16 21:40:53.928 New DB connection, total: 3
2008-10-16 21:40:53.933 Connected to database 'mythconverg' at host: localhost
2008-10-16 21:40:55.135 AFD: Opened codec 0x8dda770, id(MPEG2VIDEO) type(Video)
2008-10-16 21:40:55.135 AFD: codec MP2 has 2 channels
2008-10-16 21:40:55.135 AFD: Opened codec 0x8ddaaf0, id(MP2) type(Audio)
2008-10-16 21:40:55.195 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-16 21:40:55.200 Opening ALSA audio device 'default'.
2008-10-16 21:40:55.529 Mixer unable to find control Master
2008-10-16 21:40:55.529 Mixer unable to find control Master
2008-10-16 21:40:55.531 Mixer unable to find control PCM
2008-10-16 21:40:55.532 Mixer unable to find control PCM
2008-10-16 21:40:55.532 Mixer unable to find control PCM
2008-10-16 21:41:14.097 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-10-16 21:41:14.116 TV: Changing from None to WatchingRecording
2008-10-16 21:41:14.124 TV: Attempting to change from WatchingRecording to None
2008-10-16 21:41:14.886 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-10-16 21:41:14.898 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-16 21:41:17.075 OSD Theme Dimensions W: 640 H: 480
2008-10-16 21:41:19.917 Realtime priority would require SUID as root.
2008-10-16 21:41:20.254 FilterManager: failed to load filter 'none', no such filter exists
2008-10-16 21:41:20.254 Couldn't load deinterlace filter none
2008-10-16 21:41:20.595 Video timing method: USleep with busy wait
2008-10-16 21:41:21.174 TV: Changing from WatchingRecording to None
2008-10-16 21:41:28.807 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter/ui.xml
2008-10-16 21:41:31.512 AFD: Opened codec 0x8e94600, id(MPEG2VIDEO) type(Video)
2008-10-16 21:41:31.513 AFD: codec MP2 has 2 channels
2008-10-16 21:41:31.513 AFD: Opened codec 0x8e94980, id(MP2) type(Audio)
2008-10-16 21:41:32.421 TV: Attempting to change from None to WatchingRecording
2008-10-16 21:41:32.579 Using protocol version 40
2008-10-16 21:41:33.254 AFD: Opened codec 0x8debc40, id(MPEG2VIDEO) type(Video)
2008-10-16 21:41:33.254 AFD: codec MP2 has 2 channels
2008-10-16 21:41:33.255 AFD: Opened codec 0x8dd6fb0, id(MP2) type(Audio)
2008-10-16 21:41:33.279 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-16 21:41:33.343 Opening ALSA audio device 'default'.
2008-10-16 21:41:33.814 Mixer unable to find control Master
2008-10-16 21:41:33.814 Mixer unable to find control Master
2008-10-16 21:41:33.814 Mixer unable to find control PCM
2008-10-16 21:41:33.815 Mixer unable to find control PCM
2008-10-16 21:41:33.815 Mixer unable to find control PCM
2008-10-16 21:41:53.112 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-10-16 21:41:53.126 TV: Changing from None to WatchingRecording
2008-10-16 21:41:53.132 TV: Attempting to change from WatchingRecording to None
2008-10-16 21:41:53.953 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-10-16 21:41:53.962 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-16 21:41:54.143 OSD Theme Dimensions W: 640 H: 480
2008-10-16 21:41:55.036 FilterManager: failed to load filter 'none', no such filter exists
2008-10-16 21:41:55.036 Couldn't load deinterlace filter none
2008-10-16 21:41:55.039 Realtime priority would require SUID as root.
2008-10-16 21:41:55.134 Video timing method: USleep with busy wait
2008-10-16 21:41:55.216 TV: Changing from WatchingRecording to None
2008-10-16 21:41:55.672 AFD: Opened codec 0x82f5dc0, id(MPEG2VIDEO) type(Video)
2008-10-16 21:41:55.672 AFD: codec MP2 has 2 channels
2008-10-16 21:41:55.672 AFD: Opened codec 0x8e95860, id(MP2) type(Audio)
2008-10-16 21:41:56.120 AFD: Opened codec 0x82f5dc0, id(MPEG2VIDEO) type(Video)
2008-10-16 21:41:56.121 AFD: codec MP2 has 2 channels
2008-10-16 21:41:56.121 AFD: Opened codec 0x8e9c010, id(MP2) type(Audio)
2008-10-16 21:41:57.263 AFD: Opened codec 0x82f5dc0, id(MPEG2VIDEO) type(Video)
2008-10-16 21:41:57.263 AFD: codec MP2 has 2 channels
2008-10-16 21:41:57.263 AFD: Opened codec 0x8e9c010, id(MP2) type(Audio)
Destroying SipFsm object 
2008-10-16 21:42:43.318 Deleting UPnP client...

```

---

### Post by mrand on 2008-10-17
Howdy,
I think I've the log down to the most important parts:
> **stevenc413 said:**
> 
```

2008-10-16 21:10:10.343 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-10-16 21:10:11.118 Mixer unable to find control PCM
2008-10-16 21:10:12.708 [mpeg2video @ 0xb73b4b88]warning: first frame is no keyframe
<...>
2008-10-16 20:21:11.174 Mixer unable to find control Master
2008-10-16 20:21:11.175 Mixer unable to find control PCM
2008-10-16 20:21:11.245 VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.

```
What playback profile do you have selected?  Try a different one (preferrably slim) and see if that makes any difference.

Also, do you only see problems when you skip, or will it hose up even when just letting it sit there and play back?

> ```

2008-10-16 21:30:12.465 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-10-16 21:30:12.474 TV: Changing from None to WatchingRecording
2008-10-16 21:30:12.580 FilterManager: failed to load filter 'none', no such filter exists
2008-10-16 21:30:12.580 Couldn't load deinterlace filter none
2008-10-16 21:30:12.581 Realtime priority would require SUID as root.
2008-10-16 21:30:12.678 Video timing method: USleep with busy wait
2008-10-16 21:34:43.549 WriteAudio: buffer underrun
2008-10-16 21:34:43.572 WriteAudio: buffer underrun
Starting mythfrontend.real..

```

What speed and type processor are you using?

Lastly, what version are you running?  8.04.1 or 8.10?  Any chance you're on the weekly fixes?  If not, see the following URL for how to enable it:  [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

Have fun,

[INDENT]Marc[/INDENT]

---

### Post by stevenc413 on 2008-10-17
> What playback profile do you have selected?  Try a different one (preferrably slim) and see if that makes any difference.  I had CPU-- selected, but I changed it to slim.
> 
Also, do you only see problems when you skip, or will it hose up even when just letting it sit there and play back?  The only issues I see is when I skip after there has been an issue with starting an in progress recording.  If I am skipping around an already finished recording it's fine.  Although I always notice a slight pause (about a second or maybe two) when skipping I've always assumed that is normal.

> What speed and type processor are you using?
Lastly, what version are you running?  8.04.1 or 8.10?  Any chance you're on the weekly fixes?  If not, see the following URL for how to enable it:  [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) 
Took me a while to figure out how to find version and CPU info, but it 8.04.1 and a Pentium 4, 1.3ghz with 256MB ram.  What are auto-builds?  I think I'm going to try the Slim playback profile and see if that takes care of it.

Thanks a lot for your help!

---

