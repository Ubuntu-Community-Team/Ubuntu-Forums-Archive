---
title: "LiveTv craches after a few minutes"
date: 2010-06-20
forum: Mythbuntu
---

### Post by Techmanm on 2010-06-20
I'm watching livetv with mythbuntu 10.04 and have the latest updates installed.

But after a few minutes/seconds live tv stutters.

Here is my mythfrontend log file.

> 2010-06-20 22:04:30.203 TV: State is LiveTV & mctx == ctx
2010-06-20 22:04:30.206 TV: UpdateOSDInput done
2010-06-20 22:04:30.206 TV: UpdateLCD done
2010-06-20 22:04:30.206 TV: ITVRestart done
2010-06-20 22:04:30.209 Realtime priority would require SUID as root.
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2010-06-20 22:04:30.223 Video timing method: USleep with busy wait
2010-06-20 22:04:32.357 ProgramInfo(): Updated pathname '':'' -> '5011_20100620220432.mpg'
2010-06-20 22:04:33.353 [mp3 @ 0x7f32efb15380]Header missing
greedyhdeint: size changed from 0 x 0 -> 704 x 576
2010-06-20 22:04:33.942 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-06-20 22:04:34.147 AFD: Opened codec 0x22521c0, id(MPEG2VIDEO) type(Video)
2010-06-20 22:04:34.147 AFD: codec MP2 has 2 channels
2010-06-20 22:04:34.147 AFD: Opened codec 0x21db5d0, id(MP2) type(Audio)
2010-06-20 22:04:34.382 Opening audio device '/dev/dsp'. ch 2(2) sr 48000 (reenc 0)
2010-06-20 22:04:34.382 Opening OSS audio device '/dev/dsp'.
2010-06-20 22:04:34.385 AudioOuputOSS: Unable to open mixer: 'default'
2010-06-20 22:04:34.387 NVP(4): Enabling Audio
2010-06-20 22:11:11.704 [mp2 @ 0x7f32efb15380]Header missing
2010-06-20 22:11:11.704 AFD Error: Unknown audio decoding error
2010-06-20 22:11:12.560 NVP(4): prebuffering pause
2010-06-20 22:11:14.164 NVP(4): Prebuffer wait timed out 10 times.
2010-06-20 22:11:15.766 NVP(4): Prebuffer wait timed out 20 times.
2010-06-20 22:11:17.369 NVP(4): Prebuffer wait timed out 30 times.
2010-06-20 22:11:18.970 NVP(4): Prebuffer wait timed out 40 times.
2010-06-20 22:11:20.572 NVP(4): Prebuffer wait timed out 50 times.
2010-06-20 22:11:22.173 NVP(4): Prebuffer wait timed out 60 times.
2010-06-20 22:11:23.775 NVP(4): Prebuffer wait timed out 70 times.
2010-06-20 22:11:24.863 [mp2 @ 0x7f32efb15380]Header missing
2010-06-20 22:11:24.864 AFD Error: Unknown audio decoding error
2010-06-20 22:11:25.238 [mpeg2video @ 0x7f32efb15380]Warning MVs not available
2010-06-20 22:11:25.376 NVP(4): Prebuffer wait timed out 80 times.
2010-06-20 22:11:25.575 NVP(4): prebuffering pause

Can someone please help me.

---

### Post by Techmanm on 2010-06-20
Just a quick update.

I.m using 10.04 64 bit and i haven been searching on the internet for sometime and found things like change the audio input (now set to /dev/dsp).

(When i change to Alsa: analog i don't hear a thing)..

---

### Post by Techmanm on 2010-06-23
Nobody??

---

### Post by leafpaul on 2010-06-23
I get something similar but I haven't sorted out the cause yet.  See logs below.

LiveTV either freezes until an error message "Video frame buffer failed too many times" and closes or stalls for up to 20seconds seconds and then recovers.

I am getting an error "Video frame buffer failed too many times" occasionally since upgrading to mythbuntu 10.04 (mythtv 0.23).  The error occurs when watching livetv, livetv freezes and after some time the livetv screen closes and a pop up with the error is shown.  Clicking OK returns to the mythfrontend menu.  Selected log entries are included below.  Anyone with any ideas of how to solve this.

MythTV Version   : 25154
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.201000617-1
QT Version       : 4.6.2

mythbackend.log
2010-06-13 14:35:01.785 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 24 20
2010-06-13 14:35:02.874 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 19 9
2010-06-13 14:35:03.602 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 6 24
2010-06-13 14:35:06.758 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:35:09.674 [mpeg2video @ 0x7f4941961380]invalid mb type in B Frame at 27 32
2010-06-13 14:35:10.569 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 28 22
2010-06-13 14:35:10.909 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 12 4
2010-06-13 14:35:13.545 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 21 22
2010-06-13 14:35:13.875 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:35:13.904 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 24 6
2010-06-13 14:35:14.011 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 4 8
2010-06-13 14:35:14.177 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 23 9
2010-06-13 14:35:14.443 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 26 9
2010-06-13 14:35:14.543 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 1 10
2010-06-13 14:35:14.667 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 12 11
2010-06-13 14:35:14.705 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 2 25
2010-06-13 14:35:14.767 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 4 12
2010-06-13 14:35:14.982 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:15.090 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 9 14
2010-06-13 14:35:15.288 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:15.346 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 16 16
2010-06-13 14:35:15.462 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 28 17
2010-06-13 14:35:15.578 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:15.637 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 24 29
2010-06-13 14:35:15.678 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 4 19
2010-06-13 14:35:15.902 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 0 20
2010-06-13 14:35:16.010 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 0 21
2010-06-13 14:35:16.117 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:35:16.225 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:16.325 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:35:16.441 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 0 25
2010-06-13 14:35:16.549 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 10 26
2010-06-13 14:35:16.562 TFW, Error: Write() -- IOBOUND begin remaining(4125) free(0) size(2097152) cnt(1)
2010-06-13 14:35:16.602 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 18 20
2010-06-13 14:35:16.648 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 18 27
2010-06-13 14:35:16.873 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 10 28
2010-06-13 14:35:16.947 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:35:17.055 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 4 30
2010-06-13 14:35:17.171 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:17.262 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 0 32
2010-06-13 14:35:17.348 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 15 17
2010-06-13 14:35:17.370 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:17.536 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 27 34
2010-06-13 14:35:17.635 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:19.130 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 16 18
2010-06-13 14:35:19.408 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 26 3
2010-06-13 14:35:20.647 [mpeg2video @ 0x7f4941961380]invalid mb type in I Frame at 26 11
2010-06-13 14:35:21.381 RingBuf(/home/user/recordings/1014_20100613140000.mpg): Waited 2.0 seconds for data to become available...
2010-06-13 14:35:21.611 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 4 30
2010-06-13 14:35:22.437 [mpeg2video @ 0x7f4941961380]ac-tex damaged at 7 13
2010-06-13 14:35:23.427 RingBuf(/home/user/recordings/1014_20100613140000.mpg): Waited 4.0 seconds for data to become available...
2010-06-13 14:35:24.487 ProgramInfo(): Updated pathname '':'' -> '1019_20100613140000.mpg'
2010-06-13 14:35:25.481 ~MythContext waiting for threads to exit.
2010-06-13 14:35:25.533 ProgramInfo(): Updated pathname '':'' -> '1019_20100613140000.mpg'
2010-06-13 14:35:25.741 ProgramInfo(): Updated pathname '':'' -> '1019_20100613140000.mpg'
2010-06-13 14:35:25.870 mythbackend version: branches/release-0-23-fixes [25073] [www.mythtv.org](www.mythtv.org)
2010-06-13 14:35:26.112 Using runtime prefix = /usr
2010-06-13 14:35:26.435 Using configuration directory = /home/mythtv/.mythtv
2010-06-13 14:35:26.635 Empty LocalHostName.
2010-06-13 14:35:26.783 Using localhost value of pvr
2010-06-13 14:35:26.994 New DB connection, total: 1
2010-06-13 14:35:27.072 Connected to database 'mythconverg' at host: 127.0.0.1
2010-06-13 14:35:27.173 Closing DB connection named 'DBManager0'
2010-06-13 14:35:27.291 Connected to database 'mythconverg' at host: 127.0.0.1
2010-06-13 14:35:27.467 RingBuf(/home/user/recordings/1014_20100613140000.mpg): Waited 8.0 seconds for data to become available...
2010-06-13 14:35:27.519 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-13 14:35:27.731 ProgramInfo(): Updated pathname '':'' -> '1019_20100613140000.mpg'
2010-06-13 14:35:27.906 TFW, Error: Write() -- IOBOUND begin remaining(5241) free(0) size(4194304) cnt(1)
2010-06-13 14:35:28.086 TFW, Error: Write() -- IOBOUND end
2010-06-13 14:35:28.132 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143001.mpg'
2010-06-13 14:35:28.272 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 22 26
2010-06-13 14:35:28.137 TFW, Error: Write() -- IOBOUND end
2010-06-13 14:35:28.163 DevRdB(/dev/dvb/adapter0/frontend0) Error: Driver buffers overflowed
2010-06-13 14:35:28.434 TVRec(5): Changing from WatchingLiveTV to None
2010-06-13 14:35:28.847 ProgramInfo(5170_20100613143001.mpg), Error: Unknown type, recording width was 720
2010-06-13 14:35:28.946 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 30 14
2010-06-13 14:35:29.277 AFD: Opened codec 0x7f7f5805cd60, id(MPEG2VIDEO) type(Video)
2010-06-13 14:35:29.488 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143001.mpg'
2010-06-13 14:35:29.495 AFD: codec MP2 has 2 channels
2010-06-13 14:35:29.745 AFD: Opened codec 0x7f7f5805fb30, id(MP2) type(Audio)
2010-06-13 14:35:29.751 Finished recording The Super League Show: channel 5170
2010-06-13 14:35:29.770 AFD: Opened codec 0x7f7f58060190, id(DVB_SUBTITLE) type(Subtitle)
2010-06-13 14:35:29.831 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143001.mpg'
2010-06-13 14:35:29.875 MainServer::ANN Playback
2010-06-13 14:35:29.894 adding: pvr as a client (events: 0)
2010-06-13 14:35:30.038 TVRec(5): Changing from None to WatchingLiveTV
2010-06-13 14:35:30.060 TVRec(5): HW Tuner: 5->5
2010-06-13 14:35:30.122 [mpeg2video @ 0x7f7f6e6e8380]Warning MVs not available
2010-06-13 14:35:30.192 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 4 min
2010-06-13 14:35:30.203 Preview: Grabbed preview '/home/user/recordings/1019_20100613140000.mpg' 544x576@79s
2010-06-13 14:35:30.255 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:30.268 TVRec(5): Changing from WatchingLiveTV to None
2010-06-13 14:35:30.392 ~MythContext waiting for threads to exit.
2010-06-13 14:35:30.406 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:30.420 Finished recording The Super League Show: channel 5170
2010-06-13 14:35:30.437 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:30.445 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:30.454 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143001.mpg'
2010-06-13 14:35:30.477 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:30.539 ProgramInfo(): Updated pathname '':'' -> '1019_20100613140000.mpg'
2010-06-13 14:35:30.705 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 16 25
2010-06-13 14:35:30.924 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 13 23
2010-06-13 14:35:32.029 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 23 13
2010-06-13 14:35:32.734 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 25 29
2010-06-13 14:35:33.437 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 7 16
2010-06-13 14:35:33.755 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 17 27
2010-06-13 14:35:35.095 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:39.756 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:41.576 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 23 12
2010-06-13 14:35:46.831 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 0 26
2010-06-13 14:35:47.754 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 22 28
2010-06-13 14:35:50.738 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:35:51.061 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 23 25
2010-06-13 14:35:58.711 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 12 25
2010-06-13 14:36:00.593 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 30 2
2010-06-13 14:36:01.516 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 28 26
2010-06-13 14:36:03.575 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 33 14
2010-06-13 14:36:04.537 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 15 15
2010-06-13 14:36:07.588 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 13 6
2010-06-13 14:36:12.536 [mpeg2video @ 0x7f8d0137f380]invalid mb type in B Frame at 0 22
2010-06-13 14:36:14.661 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:15.747 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:16.829 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 15 22
2010-06-13 14:36:21.548 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 23 1
2010-06-13 14:36:21.553 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 2 2
2010-06-13 14:36:21.561 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 9 3
2010-06-13 14:36:21.569 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 4 5
2010-06-13 14:36:21.577 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 20 5
2010-06-13 14:36:21.586 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:21.594 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:21.602 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 3 8
2010-06-13 14:36:21.611 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 2 10
2010-06-13 14:36:21.619 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 5 11
2010-06-13 14:36:21.627 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:21.636 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:21.644 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 24 14
2010-06-13 14:36:21.652 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:21.660 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 15 16
2010-06-13 14:36:21.669 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 9 16
2010-06-13 14:36:21.677 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 3 18
2010-06-13 14:36:21.685 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 14 19
2010-06-13 14:36:21.694 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 24 21
2010-06-13 14:36:21.702 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 4 20
2010-06-13 14:36:21.710 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 5 21
2010-06-13 14:36:21.718 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 31 22
2010-06-13 14:36:21.727 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 9 24
2010-06-13 14:36:21.735 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 11 28
2010-06-13 14:36:21.743 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 3 27
2010-06-13 14:36:21.752 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 9 27
2010-06-13 14:36:21.760 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:21.768 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 1 29
2010-06-13 14:36:21.776 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 14 30
2010-06-13 14:36:21.785 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:21.793 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:21.801 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 14 33
2010-06-13 14:36:21.810 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 20 35
2010-06-13 14:36:29.617 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:30.498 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 21 25
2010-06-13 14:36:31.780 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 20 12
2010-06-13 14:36:36.875 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 30 28
2010-06-13 14:36:37.829 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
2010-06-13 14:36:39.620 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:36:42.791 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 13 13
2010-06-13 14:36:43.556 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 14 29
2010-06-13 14:36:45.588 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 7 15
2010-06-13 14:36:47.601 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 6 24
2010-06-13 14:36:49.822 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:51.596 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:52.413 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 26 26
2010-06-13 14:36:54.578 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:36:55.665 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 23 30
2010-06-13 14:36:58.709 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 23 21
2010-06-13 14:36:59.752 [mpeg2video @ 0x7f8d0137f380]skipped MB in I frame at 8 18
2010-06-13 14:37:00.873 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 14 1
2010-06-13 14:37:02.855 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 33 10
2010-06-13 14:37:03.818 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 23 14
2010-06-13 14:37:04.781 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 17 12
2010-06-13 14:37:05.864 [mpeg2video @ 0x7f8d0137f380]skipped MB in I frame at 13 5
2010-06-13 14:37:06.827 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 7 15
2010-06-13 14:37:08.268 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 3 1
2010-06-13 14:37:08.871 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 31 2
2010-06-13 14:37:10.917 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 21 12
2010-06-13 14:37:13.781 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 5 31
2010-06-13 14:37:14.862 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 9 8
2010-06-13 14:37:16.909 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 18 28
2010-06-13 14:37:17.870 [mpeg2video @ 0x7f8d0137f380]skipped MB in I frame at 18 4
2010-06-13 14:37:22.556 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 20 18
2010-06-13 14:37:23.758 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 17 11
2010-06-13 14:37:26.742 [mpeg2video @ 0x7f8d0137f380]qscale == 0
2010-06-13 14:37:30.913 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 28 17
2010-06-13 14:37:33.735 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 25 3
2010-06-13 14:37:36.826 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 23 21
2010-06-13 14:37:40.654 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 18 22
2010-06-13 14:37:46.874 [mpeg2video @ 0x7f8d0137f380]invalid mb type in I Frame at 7 7
2010-06-13 14:37:48.943 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 32 14
2010-06-13 14:37:51.955 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 13 26
2010-06-13 14:37:54.578 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 9 31
2010-06-13 14:37:56.981 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 16 11
2010-06-13 14:38:03.990 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 15 2
2010-06-13 14:38:15.949 [mpeg2video @ 0x7f8d0137f380]skipped MB in I frame at 33 7
2010-06-13 14:38:17.074 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 16 2
2010-06-13 14:38:19.899 [mpeg2video @ 0x7f8d0137f380]invalid cbp at 19 29
2010-06-13 14:38:22.829 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 17 20
2010-06-13 14:38:25.076 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 17 27
2010-06-13 14:38:25.757 [mpeg2video @ 0x7f8d0137f380]slice mismatch
2010-06-13 14:38:27.585 [mpeg2video @ 0x7f8d0137f380]invalid mb type in P Frame at 13 26
2010-06-13 14:38:30.637 [mpeg2video @ 0x7f8d0137f380]mb incr damaged
2010-06-13 14:38:32.577 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 1 16
2010-06-13 14:38:37.721 Expiring 0 MBytes for 5170 @ Sun Jun 13 14:30:00 2010 => The Super League Show
2010-06-13 14:38:37.733 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:38:37.842 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:38:39.613 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 24 10
2010-06-13 14:38:40.377 [mpeg2video @ 0x7f8d0137f380]ac-tex damaged at 28 16
2010-06-13 14:38:40.791 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'


mythwelcome.log
2010-06-13 14:35:08.706 RingBuf(/home/user/livetv/5170_20100613143001.mpg): Waited 1.0 seconds for data to become available...
2010-06-13 14:35:08.706 Checking to see if there's a new livetv program to switch to..
2010-06-13 14:35:08.848 NVP(2): prebuffering pause
2010-06-13 14:35:09.709 RingBuf(/home/user/livetv/5170_20100613143001.mpg): Waited 2.0 seconds for data to become available...
2010-06-13 14:35:09.709 Checking to see if there's a new livetv program to switch to..
2010-06-13 14:35:10.558 NVP(2): Prebuffer wait timed out 10 times.
2010-06-13 14:35:11.712 RingBuf(/home/user/livetv/5170_20100613143001.mpg): Waited 4.0 seconds for data to become available...
2010-06-13 14:35:11.712 Checking to see if there's a new livetv program to switch to..
2010-06-13 14:35:12.227 NVP(2): Prebuffer wait timed out 20 times.
2010-06-13 14:35:13.895 NVP(2): Prebuffer wait timed out 30 times.
2010-06-13 14:35:15.564 NVP(2): Prebuffer wait timed out 40 times.
2010-06-13 14:35:15.716 RingBuf(/home/user/livetv/5170_20100613143001.mpg): Waited 8.0 seconds for data to become available...
2010-06-13 14:35:15.716 Checking to see if there's a new livetv program to switch to..
2010-06-13 14:35:17.232 NVP(2): Prebuffer wait timed out 50 times.
2010-06-13 14:35:18.900 NVP(2): Prebuffer wait timed out 60 times.
2010-06-13 14:35:20.569 NVP(2): Prebuffer wait timed out 70 times.
2010-06-13 14:35:22.237 NVP(2): Prebuffer wait timed out 80 times.
2010-06-13 14:35:23.721 RingBuf(/home/user/livetv/5170_20100613143001.mpg) Error: Waited 16 seconds for data, aborting.
2010-06-13 14:35:23.721 [mp2 @ 0x7fa68816f380]incomplete frame
2010-06-13 14:35:23.721 AFD Error: Unknown audio decoding error
2010-06-13 14:35:23.905 NVP(2): Prebuffer wait timed out 90 times.
2010-06-13 14:35:24.145 [mpeg2video @ 0x7fa68816f380]invalid cbp at 19 11
2010-06-13 14:35:25.657 NVP(2): Prebuffer wait timed out 100 times.
2010-06-13 14:35:25.657 NVP(2), Error: Timed out waiting for prebuffering too long. Exiting..
2010-06-13 14:35:25.831 ~OpenGLVideoSync() -- closing opengl vsync
2010-06-13 14:35:25.881 TV: Attempting to change from WatchingLiveTV to None
2010-06-13 14:35:26.881 RingBuf(/home/user/livetv/5170_20100613143001.mpg): Waited too long for ringbuffer pause..
2010-06-13 14:35:27.882 RingBuf(/home/user/livetv/5170_20100613143001.mpg): Waited too long for ringbuffer pause..
2010-06-13 14:35:29.796 TV: Changing from WatchingLiveTV to None
2010-06-13 14:35:29.818 TV: Attempting to change from None to None
2010-06-13 14:35:29.873 TV: Attempting to change from None to WatchingLiveTV
2010-06-13 14:35:29.874 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-13 14:35:29.875 Using protocol version 56
2010-06-13 14:35:30.035 Spawning LiveTV Recorder -- begin
2010-06-13 14:35:30.181 Spawning LiveTV Recorder -- end
2010-06-13 14:35:30.186 ProgramInfo(): Updated pathname '':'' -> '5170_20100613143530.mpg'
2010-06-13 14:35:30.192 We have a playbackURL(/home/user/livetv/5170_20100613143530.mpg) & cardtype(DUMMY)
2010-06-13 14:35:30.193 We have a RingBuffer
2010-06-13 14:35:30.245 playCtx, Error: Attempting to setup a player, but it already exists.
2010-06-13 14:35:30.245 TV Error: LiveTV not successfully started

---

### Post by drivingdynamics on 2010-07-17
> **Techmanm said:**
> I'm watching livetv with mythbuntu 10.04 and have the latest updates installed.

But after a few minutes/seconds live tv stutters.

Here is my mythfrontend log file.



Can someone please help me.


I had the same problems with prebuffer pauses and audio buffer underruns.
In my case, the problem seems to be the wireless network card.
In the syslog i have found the entry :

phy0: unsupported jumbo

at the same time my system crashed.

I tracked the problem by using top, showing the CPU load.

```
top
```phy0 caused high cpu load and my frontend/backend crashed.
I deactivated the network.
I am right now testing for more than 5 hours watching live tv and until now
had no crash.
Maybe you have the same problem or another hardware cause high cpu load.

---

### Post by Hotwheelz79 on 2010-10-07
Hi,

I also see this issue aswell.

I hope it's fixed for 10.10

Thanks.

:-)

---

### Post by LowSky on 2010-10-07
have you tried using the Mythbuntu Autobuilds and ugrading to .23.1?

---

### Post by Hotwheelz79 on 2010-10-08
> **LowSky said:**
> have you tried using the Mythbuntu Autobuilds and ugrading to .23.1?

Yes and the problem still remained.

That's why I thought I'd try moving to 0.24 but nothing changed

apparently there was was a fix that went into 0.24 but I haven't found it.

Thanks.

:-)

---

