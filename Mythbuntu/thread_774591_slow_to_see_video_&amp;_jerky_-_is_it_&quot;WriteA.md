---
title: "slow to see video &amp; jerky - is it &quot;WriteAudio:buffer underrun&quot; or &quot;IOBOUND&quot; logs??"
date: 2008-04-29
forum: Mythbuntu
---

### Post by callagga on 2008-04-29
Hi,

Just got mythtv working (via mythbuntu) however it is taking about 20-30 seconds for the video to been visible after I go WATCH TV.  Also it is jerky/unwatchable. (it actually was watchable working during my installation phase, however after fault finding one issue that arose I am now seeing this behavior).

Could it be due to the "WriteAudio: buffer underrun" I am seeing in front end logs, or "IOBOUND" in backend log?  What does these mean / how do I resolve do you know?



_Backend Log_
```

2008-04-30 05:04:22.258 Empty LocalHostName.
2008-04-30 05:04:22.351 Using localhost value of mythtv
2008-04-30 05:04:23.119 New DB connection, total: 1
2008-04-30 05:04:23.231 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:04:23.291 Closing DB connection named 'DBManager0'
2008-04-30 05:04:23.346 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:04:23.509 New DB connection, total: 2
2008-04-30 05:04:23.522 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:04:23.580 Current Schema Version: 1214
Starting up as the master server.
2008-04-30 05:04:24.312 New DB connection, total: 3
2008-04-30 05:04:24.328 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:04:24.607 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-04-30 05:04:24.961 New DB scheduler connection
2008-04-30 05:04:24.963 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-04-30 05:04:25.086 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-30 05:04:25.088 Main::Registering HttpStatus Extension
2008-04-30 05:04:25.088 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-30 05:04:25.089 Enabled verbose msgs:  important general
2008-04-30 05:04:25.092 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-30 05:04:27.197 MainServer::HandleAnnounce Monitor
2008-04-30 05:04:27.212 adding: mythtv as a client (events: 0)
2008-04-30 05:04:27.213 MainServer::HandleAnnounce Monitor
2008-04-30 05:04:27.214 adding: mythtv as a client (events: 1)
2008-04-30 05:04:28.042 Reschedule requested for id -1.
2008-04-30 05:04:28.235 Scheduled 0 items in 0.2 = 0.11 match + 0.08 place
2008-04-30 05:04:28.246 Seem to be woken up by USER
2008-04-30 05:05:44.980 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-30 05:06:00.977 MainServer::HandleAnnounce Monitor
2008-04-30 05:06:00.982 adding: mythtv as a client (events: 0)
2008-04-30 05:06:00.983 MainServer::HandleAnnounce Monitor
2008-04-30 05:06:00.984 adding: mythtv as a client (events: 1)
2008-04-30 05:06:01.083 MainServer::HandleAnnounce Playback
2008-04-30 05:06:01.122 adding: mythtv as a client (events: 0)
2008-04-30 05:06:01.127 TVRec(1): Changing from None to WatchingLiveTV
2008-04-30 05:06:01.185 TVRec(1): HW Tuner: 1->1
2008-04-30 05:06:01.195 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-04-30 05:06:02.430 DVBSM(0), Warning: Can not measure Bit Error Rate
                        eno: Operation not supported (95)
2008-04-30 05:06:02.434 DVBSM(0), Warning: Can not count Uncorrected Blocks
                        eno: Operation not supported (95)
2008-04-30 05:06:02.486 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-04-30 05:06:04.168 Finished recording Unknown: channel 2001
2008-04-30 05:06:05.228 Finished recording Unknown: channel 2001
2008-04-30 05:06:05.354 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-04-30 05:06:05.555 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-30 05:06:05.558 Empty LocalHostName.
2008-04-30 05:06:05.559 Using localhost value of mythtv
2008-04-30 05:06:05.572 New DB connection, total: 1
2008-04-30 05:06:05.578 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:06:05.580 Closing DB connection named 'DBManager0'
2008-04-30 05:06:05.582 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:06:05.584 New DB connection, total: 2
2008-04-30 05:06:05.585 Connected to database 'mythconverg' at host: localhost
2008-04-30 05:06:05.589 Current Schema Version: 1214
2008-04-30 05:06:05.600 Preview Error: Previewer file '/var/lib/mythtv/recordings/2001_20080430050601.mpg' is not valid.
2008-04-30 05:06:05.603 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2001_20080430050601.mpg'
2008-04-30 05:06:05.610 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/2001_20080430050601.mpg.png) exists: 0 readable: 0 size: 0
2008-04-30 05:06:15.326 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(1151)
2008-04-30 05:06:16.009 TFW, Error: Write() -- IOBOUND end
2008-04-30 05:06:23.017 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(3407)
2008-04-30 05:06:23.709 TFW, Error: Write() -- IOBOUND end
2008-04-30 05:07:31.091 TVRec(1): Changing from WatchingLiveTV to None
2008-04-30 05:07:32.546 Finished recording Unknown: channel 2001
2008-04-30 05:08:45.457 Expiring 0 MBytes for 2001 @ Wed Apr 30 05:06:01 2008 => Unknown
2008-04-30 05:10:45.479 Expiring 170 MBytes for 2001 @ Wed Apr 30 05:06:04 2008 => Unknown
greg@mythtv:/var/log/mythtv$ 


```


_Frontend Log_
```

2008-04-30 05:06:00.976 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-30 05:06:00.977 Using protocol version 40
2008-04-30 05:06:01.082 TV: Attempting to change from None to WatchingLiveTV
2008-04-30 05:06:01.083 Using protocol version 40
2008-04-30 05:06:02.522 DPMS Deactivated 
2008-04-30 05:06:02.705 New DB connection, total: 3
2008-04-30 05:06:02.706 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-30 05:06:02.729 NVP: Disabling Audio, params(-1,2,44100)
2008-04-30 05:06:02.826 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-04-30 05:06:02.915 OSD Theme Dimensions W: 640 H: 480
2008-04-30 05:06:03.376 TV: Changing from None to WatchingLiveTV
2008-04-30 05:06:03.395 New DB connection, total: 4
2008-04-30 05:06:03.395 Realtime priority would require SUID as root.
2008-04-30 05:06:03.397 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-30 05:06:06.649 Video timing method: USleep with busy wait
2008-04-30 05:06:06.842 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
2008-04-30 05:06:08.874 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'opengl,xv-blit,xshm,xlib,' available, using 'opengl' instead.
2008-04-30 05:06:29.265 AFD: Opened codec 0x8360ea0, id(MPEG2VIDEO) type(Video)
2008-04-30 05:06:29.343 AFD: codec AC3 has 2 channels
No accelerated IMDCT transform found
2008-04-30 05:06:29.464 AFD: Opened codec 0x865afc0, id(AC3) type(Audio)
2008-04-30 05:06:30.933 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-30 05:06:30.933 Opening ALSA audio device 'default'.
2008-04-30 05:06:34.772 NVP: Enabling Audio
2008-04-30 05:06:39.756 NVP: Timed out waiting for free video buffers.
2008-04-30 05:06:41.795 NVP: Timed out waiting for free video buffers.
2008-04-30 05:06:43.816 NVP: Timed out waiting for free video buffers.
2008-04-30 05:06:45.841 NVP: Timed out waiting for free video buffers.
2008-04-30 05:06:47.021 WriteAudio: buffer underrun
2008-04-30 05:06:47.117 WriteAudio: buffer underrun
2008-04-30 05:06:47.169 WriteAudio: buffer underrun
2008-04-30 05:06:47.281 WriteAudio: buffer underrun
2008-04-30 05:06:47.384 WriteAudio: buffer underrun
2008-04-30 05:06:47.429 WriteAudio: buffer underrun
2008-04-30 05:06:47.557 WriteAudio: buffer underrun
2008-04-30 05:06:47.617 WriteAudio: buffer underrun
2008-04-30 05:06:47.686 WriteAudio: buffer underrun
2008-04-30 05:06:47.918 WriteAudio: buffer underrun
2008-04-30 05:06:47.984 WriteAudio: buffer underrun
2008-04-30 05:06:48.047 WriteAudio: buffer underrun
2008-04-30 05:06:48.113 WriteAudio: buffer underrun
2008-04-30 05:06:48.240 WriteAudio: buffer underrun
2008-04-30 05:06:48.308 WriteAudio: buffer underrun
2008-04-30 05:06:48.377 WriteAudio: buffer underrun
2008-04-30 05:06:48.507 WriteAudio: buffer underrun
2008-04-30 05:06:48.570 WriteAudio: buffer underrun
2008-04-30 05:06:48.638 WriteAudio: buffer underrun
2008-04-30 05:06:48.705 WriteAudio: buffer underrun
2008-04-30 05:06:48.934 WriteAudio: buffer underrun
2008-04-30 05:06:49.005 WriteAudio: buffer underrun
2008-04-30 05:06:49.071 WriteAudio: buffer underrun
2008-04-30 05:06:49.200 WriteAudio: buffer underrun
2008-04-30 05:06:49.262 WriteAudio: buffer underrun
2008-04-30 05:06:49.328 WriteAudio: buffer underrun
2008-04-30 05:06:49.393 WriteAudio: buffer underrun
2008-04-30 05:06:49.461 WriteAudio: buffer underrun
2008-04-30 05:06:49.524 WriteAudio: buffer underrun
2008-04-30 05:06:49.594 WriteAudio: buffer underrun
2008-04-30 05:06:49.724 WriteAudio: buffer underrun
2008-04-30 05:06:49.962 WriteAudio: buffer underrun
2008-04-30 05:06:50.029 WriteAudio: buffer underrun
2008-04-30 05:06:50.153 WriteAudio: buffer underrun
2008-04-30 05:06:50.220 WriteAudio: buffer underrun
2008-04-30 05:06:50.283 WriteAudio: buffer underrun
2008-04-30 05:06:50.352 WriteAudio: buffer underrun
2008-04-30 05:06:50.411 WriteAudio: buffer underrun
2008-04-30 05:06:50.472 WriteAudio: buffer underrun
2008-04-30 05:06:50.538 WriteAudio: buffer underrun
2008-04-30 05:06:50.608 WriteAudio: buffer underrun
2008-04-30 05:06:50.670 WriteAudio: buffer underrun
2008-04-30 05:06:50.903 WriteAudio: buffer underrun
2008-04-30 05:06:50.965 WriteAudio: buffer underrun
2008-04-30 05:06:51.109 WriteAudio: buffer underrun
2008-04-30 05:06:51.173 WriteAudio: buffer underrun
2008-04-30 05:06:51.236 WriteAudio: buffer underrun
2008-04-30 05:06:51.368 WriteAudio: buffer underrun
2008-04-30 05:06:51.430 WriteAudio: buffer underrun
2008-04-30 05:06:51.495 WriteAudio: buffer underrun
2008-04-30 05:06:51.641 [mpeg2video @ 0xb73f7148]00 motion_type at 31 49
2008-04-30 05:06:51.642 [mpeg2video @ 0xb73f7148]00 motion_type at 1 42
2008-04-30 05:06:51.642 [mpeg2video @ 0xb73f7148]00 motion_type at 1 43
2008-04-30 05:06:51.642 [mpeg2video @ 0xb73f7148]00 motion_type at 5 44
2008-04-30 05:06:51.642 [mpeg2video @ 0xb73f7148]slice mismatch
2008-04-30 05:06:51.642 [mpeg2video @ 0xb73f7148]invalid mb type in B Frame at 10 46
2008-04-30 05:06:51.642 [mpeg2video @ 0xb73f7148]invalid mb type in B Frame at 4 47
2008-04-30 05:06:51.643 [mpeg2video @ 0xb73f7148]invalid mb type in B Frame at 25 48
2008-04-30 05:06:51.644 [mpeg2video @ 0xb73f7148]invalid mb type in B Frame at 25 49
2008-04-30 05:06:51.644 [mpeg2video @ 0xb73f7148]mb incr damaged
2008-04-30 05:06:51.644 [mpeg2video @ 0xb73f7148]slice mismatch
2008-04-30 05:06:51.645 [mpeg2video @ 0xb73f7148]slice mismatch
2008-04-30 05:06:51.645 [mpeg2video @ 0xb73f7148]00 motion_type at 1 53
2008-04-30 05:06:51.645 [mpeg2video @ 0xb73f7148]mb incr damaged
2008-04-30 05:06:51.645 [mpeg2video @ 0xb73f7148]mb incr damaged
2008-04-30 05:06:51.646 [mpeg2video @ 0xb73f7148]ac-tex damaged at 12 56
2008-04-30 05:06:51.646 [mpeg2video @ 0xb73f7148]00 motion_type at 19 57
2008-04-30 05:06:51.646 [mpeg2video @ 0xb73f7148]slice mismatch
2008-04-30 05:06:51.646 [mpeg2video @ 0xb73f7148]00 motion_type at 8 59
2008-04-30 05:06:51.646 [mpeg2video @ 0xb73f7148]00 motion_type at 1 60
2008-04-30 05:06:51.646 [mpeg2video @ 0xb73f7148]mb incr damaged
2008-04-30 05:06:51.647 [mpeg2video @ 0xb73f7148]00 motion_type at 0 62
2008-04-30 05:06:51.647 [mpeg2video @ 0xb73f7148]00 motion_type at 4 63
2008-04-30 05:06:51.647 [mpeg2video @ 0xb73f7148]00 motion_type at 0 64
2008-04-30 05:06:51.647 [mpeg2video @ 0xb73f7148]00 motion_type at 0 65
2008-04-30 05:06:51.647 [mpeg2video @ 0xb73f7148]00 motion_type at 1 66
2008-04-30 05:06:51.733 [mpeg2video @ 0xb73f7148]Warning MVs not available
2008-04-30 05:06:51.871 WriteAudio: buffer underrun
2008-04-30 05:06:51.906 WriteAudio: buffer underrun
2008-04-30 05:06:51.941 WriteAudio: buffer underrun
2008-04-30 05:06:52.115 WriteAudio: buffer underrun
2008-04-30 05:06:52.248 WriteAudio: buffer underrun
2008-04-30 05:06:52.377 WriteAudio: buffer underrun
2008-04-30 05:06:52.448 WriteAudio: buffer underrun
2008-04-30 05:06:52.510 WriteAudio: buffer underrun
2008-04-30 05:06:52.580 WriteAudio: buffer underrun
2008-04-30 05:06:52.667 WriteAudio: buffer underrun
2008-04-30 05:06:52.773 WriteAudio: buffer underrun
2008-04-30 05:06:53.065 WriteAudio: buffer underrun
2008-04-30 05:06:53.161 WriteAudio: buffer underrun
2008-04-30 05:06:53.382 WriteAudio: buffer underrun
2008-04-30 05:06:53.517 WriteAudio: buffer underrun
2008-04-30 05:06:53.605 WriteAudio: buffer underrun
2008-04-30 05:06:53.688 WriteAudio: buffer underrun
2008-04-30 05:06:53.775 WriteAudio: buffer underrun
2008-04-30 05:06:54.043 WriteAudio: buffer underrun
2008-04-30 05:06:54.123 WriteAudio: buffer underrun
2008-04-30 05:06:54.217 WriteAudio: buffer underrun
2008-04-30 05:06:54.301 WriteAudio: buffer underrun
2008-04-30 05:06:54.389 WriteAudio: buffer underrun
2008-04-30 05:06:54.473 WriteAudio: buffer underrun
2008-04-30 05:06:54.577 WriteAudio: buffer underrun
2008-04-30 05:06:54.662 WriteAudio: buffer underrun
2008-04-30 05:06:54.754 WriteAudio: buffer underrun
2008-04-30 05:06:54.841 WriteAudio: buffer underrun
2008-04-30 05:06:55.269 WriteAudio: buffer underrun
2008-04-30 05:06:55.358 WriteAudio: buffer underrun
2008-04-30 05:06:55.563 WriteAudio: buffer underrun
2008-04-30 05:06:55.653 WriteAudio: buffer underrun
2008-04-30 05:06:55.786 WriteAudio: buffer underrun
2008-04-30 05:06:56.033 WriteAudio: buffer underrun
2008-04-30 05:06:56.151 WriteAudio: buffer underrun
2008-04-30 05:06:56.214 WriteAudio: buffer underrun
2008-04-30 05:06:56.344 WriteAudio: buffer underrun
2008-04-30 05:06:56.406 WriteAudio: buffer underrun
2008-04-30 05:06:56.468 WriteAudio: buffer underrun
2008-04-30 05:06:56.534 WriteAudio: buffer underrun
2008-04-30 05:06:56.595 WriteAudio: buffer underrun
2008-04-30 05:06:56.651 WriteAudio: buffer underrun
2008-04-30 05:06:56.716 WriteAudio: buffer underrun
2008-04-30 05:06:56.785 WriteAudio: buffer underrun
2008-04-30 05:06:56.842 WriteAudio: buffer underrun
2008-04-30 05:06:57.072 WriteAudio: buffer underrun
2008-04-30 05:06:57.135 WriteAudio: buffer underrun
2008-04-30 05:06:57.259 WriteAudio: buffer underrun
2008-04-30 05:06:57.320 WriteAudio: buffer underrun
2008-04-30 05:06:57.382 WriteAudio: buffer underrun
2008-04-30 05:06:57.516 WriteAudio: buffer underrun
2008-04-30 05:06:57.572 WriteAudio: buffer underrun
2008-04-30 05:06:57.639 WriteAudio: buffer underrun
2008-04-30 05:06:58.056 WriteAudio: buffer underrun
2008-04-30 05:06:58.478 WriteAudio: buffer underrun
2008-04-30 05:06:59.649 WriteAudio: buffer underrun
2008-04-30 05:07:03.391 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2008-04-30 05:07:03.452 AFD: Opened codec 0x8761f10, id(MPEG2VIDEO) type(Video)
2008-04-30 05:07:03.454 AFD: codec AC3 has 2 channels
No accelerated IMDCT transform found
2008-04-30 05:07:03.454 AFD: Opened codec 0x932bfb0, id(AC3) type(Audio)
2008-04-30 05:07:06.328 NVP: Timed out waiting for free video buffers.
2008-04-30 05:07:08.359 NVP: Timed out waiting for free video buffers.
2008-04-30 05:07:10.383 NVP: Timed out waiting for free video buffers.
2008-04-30 05:07:11.222 WriteAudio: buffer underrun
2008-04-30 05:07:13.721 Waited too long for video out to unpause
2008-04-30 05:07:17.293 NVP: Timed out waiting for free video buffers.
2008-04-30 05:07:19.312 NVP: Timed out waiting for free video buffers.
2008-04-30 05:07:21.333 NVP: Timed out waiting for free video buffers.
2008-04-30 05:07:22.559 WriteAudio: buffer underrun
2008-04-30 05:07:22.628 WriteAudio: buffer underrun
2008-04-30 05:07:22.693 WriteAudio: buffer underrun
2008-04-30 05:07:22.751 WriteAudio: buffer underrun
2008-04-30 05:07:22.813 WriteAudio: buffer underrun
2008-04-30 05:07:23.046 WriteAudio: buffer underrun
2008-04-30 05:07:23.169 WriteAudio: buffer underrun
2008-04-30 05:07:23.240 WriteAudio: buffer underrun
2008-04-30 05:07:23.301 WriteAudio: buffer underrun
2008-04-30 05:07:23.366 WriteAudio: buffer underrun
2008-04-30 05:07:23.428 WriteAudio: buffer underrun
2008-04-30 05:07:23.485 WriteAudio: buffer underrun
2008-04-30 05:07:23.546 WriteAudio: buffer underrun
2008-04-30 05:07:23.612 WriteAudio: buffer underrun
2008-04-30 05:07:23.668 WriteAudio: buffer underrun
2008-04-30 05:07:23.731 WriteAudio: buffer underrun
2008-04-30 05:07:23.789 WriteAudio: buffer underrun
2008-04-30 05:07:24.079 WriteAudio: buffer underrun
2008-04-30 05:07:24.143 WriteAudio: buffer underrun
2008-04-30 05:07:24.203 WriteAudio: buffer underrun
2008-04-30 05:07:24.268 WriteAudio: buffer underrun
2008-04-30 05:07:24.323 WriteAudio: buffer underrun
2008-04-30 05:07:24.389 WriteAudio: buffer underrun
2008-04-30 05:07:24.449 WriteAudio: buffer underrun
2008-04-30 05:07:24.514 WriteAudio: buffer underrun
2008-04-30 05:07:24.573 WriteAudio: buffer underrun
2008-04-30 05:07:24.632 WriteAudio: buffer underrun
2008-04-30 05:07:24.694 WriteAudio: buffer underrun
2008-04-30 05:07:24.814 WriteAudio: buffer underrun
2008-04-30 05:07:24.877 WriteAudio: buffer underrun
2008-04-30 05:07:25.107 WriteAudio: buffer underrun
2008-04-30 05:07:25.172 WriteAudio: buffer underrun
2008-04-30 05:07:25.234 WriteAudio: buffer underrun
2008-04-30 05:07:25.288 WriteAudio: buffer underrun
2008-04-30 05:07:25.358 WriteAudio: buffer underrun
2008-04-30 05:07:25.425 WriteAudio: buffer underrun
2008-04-30 05:07:25.488 WriteAudio: buffer underrun
2008-04-30 05:07:25.547 WriteAudio: buffer underrun
2008-04-30 05:07:25.606 WriteAudio: buffer underrun
2008-04-30 05:07:25.722 WriteAudio: buffer underrun
2008-04-30 05:07:25.785 WriteAudio: buffer underrun
2008-04-30 05:07:25.856 WriteAudio: buffer underrun
2008-04-30 05:07:26.083 WriteAudio: buffer underrun
2008-04-30 05:07:26.143 WriteAudio: buffer underrun
2008-04-30 05:07:26.209 WriteAudio: buffer underrun
2008-04-30 05:07:26.277 WriteAudio: buffer underrun
2008-04-30 05:07:26.346 [liba52 @ 0xb73f7148]Error decoding frame
2008-04-30 05:07:26.348 WriteAudio: buffer underrun
2008-04-30 05:07:26.479 WriteAudio: buffer underrun
2008-04-30 05:07:26.550 WriteAudio: buffer underrun
2008-04-30 05:07:26.629 WriteAudio: buffer underrun
2008-04-30 05:07:26.687 WriteAudio: buffer underrun
2008-04-30 05:07:26.746 WriteAudio: buffer underrun
2008-04-30 05:07:26.802 WriteAudio: buffer underrun
2008-04-30 05:07:27.081 WriteAudio: buffer underrun
2008-04-30 05:07:27.140 WriteAudio: buffer underrun
2008-04-30 05:07:27.227 [mpeg2video @ 0xb73f7148]skipped MB in I frame at 25 3
2008-04-30 05:07:27.243 [mpeg2video @ 0xb73f7148]Warning MVs not available
2008-04-30 05:07:27.345 WriteAudio: buffer underrun
2008-04-30 05:07:27.380 WriteAudio: buffer underrun
2008-04-30 05:07:27.477 WriteAudio: buffer underrun
2008-04-30 05:07:27.589 WriteAudio: buffer underrun
2008-04-30 05:07:27.646 WriteAudio: buffer underrun
2008-04-30 05:07:27.706 WriteAudio: buffer underrun
2008-04-30 05:07:27.827 WriteAudio: buffer underrun
2008-04-30 05:07:28.053 WriteAudio: buffer underrun
2008-04-30 05:07:28.113 WriteAudio: buffer underrun
2008-04-30 05:07:28.178 WriteAudio: buffer underrun
2008-04-30 05:07:28.234 WriteAudio: buffer underrun
2008-04-30 05:07:28.294 WriteAudio: buffer underrun
2008-04-30 05:07:28.352 WriteAudio: buffer underrun
2008-04-30 05:07:28.472 WriteAudio: buffer underrun
2008-04-30 05:07:28.533 WriteAudio: buffer underrun
2008-04-30 05:07:28.593 WriteAudio: buffer underrun
2008-04-30 05:07:28.702 WriteAudio: buffer underrun
2008-04-30 05:07:28.763 WriteAudio: buffer underrun
2008-04-30 05:07:28.826 WriteAudio: buffer underrun
2008-04-30 05:07:28.899 WriteAudio: buffer underrun
2008-04-30 05:07:29.113 WriteAudio: buffer underrun
2008-04-30 05:07:29.171 WriteAudio: buffer underrun
2008-04-30 05:07:29.228 WriteAudio: buffer underrun
2008-04-30 05:07:29.344 WriteAudio: buffer underrun
2008-04-30 05:07:29.401 WriteAudio: buffer underrun
2008-04-30 05:07:29.458 WriteAudio: buffer underrun
2008-04-30 05:07:29.585 WriteAudio: buffer underrun
2008-04-30 05:07:29.649 WriteAudio: buffer underrun
2008-04-30 05:07:29.712 WriteAudio: buffer underrun
2008-04-30 05:07:29.827 WriteAudio: buffer underrun
2008-04-30 05:07:30.052 WriteAudio: buffer underrun
2008-04-30 05:07:30.111 WriteAudio: buffer underrun
2008-04-30 05:07:30.227 WriteAudio: buffer underrun
2008-04-30 05:07:30.287 WriteAudio: buffer underrun
2008-04-30 05:07:30.346 WriteAudio: buffer underrun
2008-04-30 05:07:30.466 WriteAudio: buffer underrun
2008-04-30 05:07:30.524 WriteAudio: buffer underrun
2008-04-30 05:07:30.584 WriteAudio: buffer underrun
2008-04-30 05:07:30.654 WriteAudio: buffer underrun
2008-04-30 05:07:30.701 TV: Attempting to change from WatchingLiveTV to None
2008-04-30 05:07:30.846 WriteAudio: buffer underrun
2008-04-30 05:07:33.181 TV: Changing from WatchingLiveTV to None
2008-04-30 05:07:33.408 DPMS Reactivated.


```

---

### Post by laga on 2008-04-29
What version of Mythbuntu is that? Can you show me the output of *mythbackend --version*?

---

### Post by callagga on 2008-04-29
> **laga said:**
> What version of Mythbuntu is that? Can you show me the output of *mythbackend --version*?Here it is here:

```

greg@mythtv:/var/log/mythtv$ mythbackend --version
Please include all output in bug reports.
MythTV Version   : 16468
MythTV Branch    : tags/release-0-21
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 using_live
greg@mythtv:/var/log/mythtv$ 

```

---

### Post by callagga on 2008-04-29
PS.  I did put in an dedicate audio card in the PC which I haven't configured yet (not sure how to in fact).  The sound for the moment is coming out of the PC speaker at the moment.  Perhaps this is not significant

---

### Post by laga on 2008-04-29
Ah, you're still running Mythbuntu 7.10.

The problem is that it can't use XvMC, and the fakllback is the opengl renderer which probably brings your box to its knees.

Either configure your playback profiles properly or upgrade to Mythbuntu 8.04 or use at least the weekly builds for 7.10: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) - the "problem" is fixed there and it uses a different fallback video renderer.

There's plenty of information available on the forums if you want to configure the display profiles.

---

### Post by callagga on 2008-04-30
thanks

> **laga said:**
> upgrade to Mythbuntu 8.04 or use at least the weekly builds for 7.10: what are most people running?  what would you recommend 

(I just installed from the mythbuntu ISO as I'd assumed this would be the stable version.  I did actually do a software update for critical software patches too)

---

### Post by callagga on 2008-04-30
actually having some upgrade issues here.  Posted this issue at:

[http://ubuntuforums.org/showthread.php?t=775654](http://ubuntuforums.org/showthread.php?t=775654)

---

### Post by callagga on 2008-05-01
done the upgrade - video is coming up, albeit a little, jerky, however I see the following in the logs - any advice on how to fix these?

Backend Log
```
2008-05-01 19:07:05.482 MainServer::HandleAnnounce Playback
2008-05-01 19:07:05.484 adding: mythtv as a client (events: 0)
2008-05-01 19:07:05.486 TVRec(1): Changing from None to WatchingLiveTV
2008-05-01 19:07:05.595 TVRec(1): HW Tuner: 1->1
[B]2008-05-01 19:07:05.670 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-05-01 19:07:06.856 DVBSM(0), Warning: Can not measure Bit Error Rate
                        eno: Operation not supported (95)
2008-05-01 19:07:06.859 DVBSM(0), Warning: Can not count Uncorrected Blocks
                        eno: Operation not supported (95)[/B]
2008-05-01 19:07:06.998 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-01 19:07:08.011 Finished recording Unknown: channel 2001
2008-05-01 19:07:09.129 Finished recording Unknown: channel 2001
2008-05-01 19:07:09.340 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-01 19:07:10.580 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-01 19:07:10.634 Empty LocalHostName.
2008-05-01 19:07:10.637 Using localhost value of mythtv
2008-05-01 19:07:12.314 New DB connection, total: 1
2008-05-01 19:07:12.725 Connected to database 'mythconverg' at host: localhost
2008-05-01 19:07:12.876 Closing DB connection named 'DBManager0'
2008-05-01 19:07:13.012 Connected to database 'mythconverg' at host: localhost
2008-05-01 19:07:13.142 New DB connection, total: 2
2008-05-01 19:07:13.148 Connected to database 'mythconverg' at host: localhost
2008-05-01 19:07:13.202 Current Schema Version: 1214
[B]2008-05-01 19:07:13.396 Preview Error: Previewer file '/var/lib/mythtv/recordings/2001_20080501190705.mpg' is not valid.
2008-05-01 19:07:13.405 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2001_20080501190705.mpg'
2008-05-01 19:07:13.678 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/2001_20080501190705.mpg.png) exists: 0 readable: 0 size: 0[/B]
2008-05-01 19:07:20.432 TVRec(1): Changing from WatchingLiveTV to None
2008-05-01 19:07:20.531 Finished recording Unknown: channel 2001
```


FrontEnd Log

```
2008-05-01 19:07:05.305 TV: Attempting to change from None to WatchingLiveTV
2008-05-01 19:07:05.482 Using protocol version 40
2008-05-01 19:07:07.132 DPMS Deactivated 
2008-05-01 19:07:07.765 NVP: Disabling Audio, params(-1,2,44100)
2008-05-01 19:07:07.802 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-05-01 19:07:07.871 OSD Theme Dimensions W: 640 H: 480
2008-05-01 19:07:08.315 TV: Changing from None to WatchingLiveTV
2008-05-01 19:07:08.317 Realtime priority would require SUID as root.
[B]2008-05-01 19:07:10.636 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2008-05-01 19:07:10.644 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.[/B]
2008-05-01 19:07:10.649 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-05-01 19:07:11.886 Video timing method: USleep with busy wait
2008-05-01 19:07:12.676 AFD: Opened codec 0x8fdb360, id(MPEG2VIDEO) type(Video)
2008-05-01 19:07:12.676 AFD: codec AC3 has 2 channels
2008-05-01 19:07:12.677 AFD: Opened codec 0x904e390, id(AC3) type(Audio)
2008-05-01 19:07:12.681 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-01 19:07:12.681 Opening ALSA audio device 'default'.
2008-05-01 19:07:12.891 NVP: Enabling Audio
2008-05-01 19:07:20.408 TV: Attempting to change from WatchingLiveTV to None
2008-05-01 19:07:20.565 TV: Changing from WatchingLiveTV to None
2008-05-01 19:07:20.614 DPMS Reactivated.
2008-05-01 19:07:21.947 MythThemedMenuPrivate: Unknown tag image in background
```

---

