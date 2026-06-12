---
title: "Hauppauge PVR-150 and LiveTV Stop working after about 20 minutes of use."
date: 2008-07-07
forum: Mythbuntu
---

### Post by SavedLinuXgeeK on 2008-07-07
Hi,

  I am running Mythbuntu (Hardy Heron 8.04) with a MythTv release version of 0.21.  I am using a Hauppauge PVR-150 card for recording/watching live tv.  The TV card works for a period of time and then all of a sudden it just stops responding, and watching livetv fails.

My dmesg output for ivtv is as follows:
```

[   29.428901] ivtv:  Start initialization, version 1.1.0
[   29.429035] ivtv0: Initializing card #0
[   29.429038] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   29.484380] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   29.557580] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   29.734695] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   29.737709] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.807324] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   29.963399] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   29.971485] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   29.971499] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   29.971511] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   29.971526] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   29.971540] ivtv0: Registered device radio0 for encoder radio
[   29.971543] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   29.971556] ivtv:  End initialization
[   51.450588] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   51.544216] ivtv0: Encoder revision: 0x02060039

```

I am running the 2.6.24 kernel, and my ivtv version is 1.1.0.  I read elsewhere that earlier versions of ivtv were having issues with DMA timeouts, but I am also getting DMA timeouts on this version.  

My mythbackend.log has this error when trying to access the card:
```

2008-07-06 01:12:10.172 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-07-06 01:12:15.645 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2008-07-06 01:12:16.769 TVRec(1): Changing from WatchingLiveTV to None

```

And the corresponding time in dmesg shows the DMA error:
```

[  555.723879] ivtv0: DMA TIMEOUT 00000001 0
[  558.442471] ivtv0: DMA TIMEOUT 00000001 0
[  561.029642] ivtv0: DMA TIMEOUT 00000001 0
[  563.617233] ivtv0: DMA TIMEOUT 00000001 0
[  566.202458] ivtv0: DMA TIMEOUT 00000001 0
[  568.789828] ivtv0: DMA TIMEOUT 00000001 0
[  571.377197] ivtv0: DMA TIMEOUT 00000001 0
[  573.962672] ivtv0: DMA TIMEOUT 00000001 0
....

```

And the final piece (that I know of) is the messages that appear in the mythfrontend.log:
```

2008-07-06 19:02:24.360 NVP: prebuffering pause
2008-07-06 19:03:00.504 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 35 26
2008-07-06 19:03:00.504 [mpeg2video @ 0x7f08335ea5b0]Warning MVs not available
2008-07-06 19:03:08.091 [mpeg2video @ 0x7f08335ea5b0]mb incr damaged
2008-07-06 19:03:17.093 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 35 25
2008-07-06 19:04:26.384 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 31 26
2008-07-06 19:04:36.733 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 24 5
2008-07-06 19:05:07.651 [mpeg2video @ 0x7f08335ea5b0]slice mismatch
2008-07-06 19:05:07.651 [mpeg2video @ 0x7f08335ea5b0]Warning MVs not available
2008-07-06 19:07:05.804 [mpeg2video @ 0x7f08335ea5b0]skipped MB in I frame at 19 5
2008-07-06 19:07:05.810 [mpeg2video @ 0x7f08335ea5b0]Warning MVs not available
2008-07-06 19:07:09.137 [mpeg2video @ 0x7f08335ea5b0]slice mismatch
2008-07-06 19:07:15.506 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 28 20
2008-07-06 19:08:33.472 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 28 24
2008-07-06 19:08:41.359 [mpeg2video @ 0x7f08335ea5b0]slice mismatch
2008-07-06 19:10:27.542 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 26 17
2008-07-06 19:11:11.864 NVP: prebuffering pause
2008-07-06 19:11:13.084 WriteAudio: buffer underrun
2008-07-06 19:11:13.345 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:14.862 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:16.362 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:17.862 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:19.211 RingBuf(/var/lib/mythtv/recordings/1101_20080706190201.mpg): Waited 8.0 seconds for data to become available...
2008-07-06 19:11:19.239 Checking to see if there's a new livetv program to switch to..
2008-07-06 19:11:19.362 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:20.861 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:22.411 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:23.928 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:25.444 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:26.944 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:27.242 RingBuf(/var/lib/mythtv/recordings/1101_20080706190201.mpg) Error: Waited 16 seconds for data, aborting.
2008-07-06 19:11:27.859 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 39 25
2008-07-06 19:11:27.978 [mpeg2video @ 0x7f08335ea5b0]ac-tex damaged at 36 7
2008-07-06 19:11:28.444 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:29.961 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:31.461 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:32.961 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:34.461 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:35.960 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:37.460 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:38.960 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:40.460 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:41.960 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:43.460 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:44.960 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:46.460 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:47.960 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:49.460 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:50.959 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:52.459 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:53.959 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:55.459 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:56.959 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:58.459 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:11:59.959 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:01.459 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:02.959 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:04.459 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:05.958 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:07.475 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:08.975 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:10.492 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:11.992 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:13.492 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:14.991 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:16.508 NVP: Prebuffer wait timed out 10 times.
2008-07-06 19:12:17.422 TV: Attempting to change from WatchingLiveTV to None
2008-07-06 19:12:17.575 ~OpenGLVideoSync() -- begin
2008-07-06 19:12:17.575 ~OpenGLVideoSync() -- middle
2008-07-06 19:12:17.576 ~OpenGLVideoSync() -- end
2008-07-06 19:12:21.643 TV: Changing from WatchingLiveTV to None
2008-07-06 19:12:21.729 DPMS Reactivated.
2008-07-06 19:14:05.606 TV: Attempting to change from None to WatchingLiveTV
2008-07-06 19:14:05.607 Using protocol version 40
2008-07-06 19:14:13.418 RingBuf(/var/lib/mythtv/recordings/1101_20080706191405.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1101_20080706191405.mpg'.
2008-07-06 19:14:13.450 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/1101_20080706191405.mpg
2008-07-06 19:14:13.450 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-07-06 19:14:13.517 DPMS Deactivated 
2008-07-06 19:14:17.827 TV Error: LiveTV not successfully started
2008-07-06 19:14:17.923 DPMS Reactivated.

```

The main issue I see in the front end is not being able to open the live stream which I assume is due to the DMA timeouts listed in the dmesg output.

I have searched many a forum and tutorial to try to make some heads of these errors, but as I understand it, this should have been resolved in ivtv 1.1.0 so I am not sure what the issue really is.  If any one has any ideas or is able to help at all, that would be greatly appreciated.

Also, there is some noise in the frontend log about ac-tex being damaged, I'm not sure what that means either.  Again, any help would be awesome.

---

### Post by ian dobson on 2008-07-08
Hi,

What are your temperatures like?

Try creating a file /etc/modprobe.d/ivtv.conf with the text:-

options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2

In it, this will increase the size of the mpeg buffers, which might solve your problem.

Regards
Ian Dobson

---

### Post by SavedLinuXgeeK on 2008-07-09
Thanks for the reply Ian, I should be able to test this out tnite, and get back.  Thanks again.

---

### Post by SavedLinuXgeeK on 2008-07-13
Hey Ian.  I've tried the suggested activities and it changing the modprobe settings didn't seem to make a difference.  Any additional suggestions would be great.

---

### Post by ian dobson on 2008-07-13
Hi,

What do you get when you try :-

grep ivtv  /var/log/messages

I'm mainly interested in lines like:-
```

Jul 13 18:45:22 alpha2 kernel: [   47.216223] ivtv0: Registered device video1 for encoder MPG (9216 kB)
Jul 13 18:45:22 alpha2 kernel: [   47.216243] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Jul 13 18:45:22 alpha2 kernel: [   47.216258] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Jul 13 18:45:22 alpha2 kernel: [   47.216270] ivtv0: Registered device video24 for encoder PCM (320 kB)
Jul 13 18:45:22 alpha2 kernel: [   47.216272] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150

```

and 
```

Jul 13 18:45:54 alpha2 kernel: [   84.877112] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Jul 13 18:45:54 alpha2 kernel: [   85.077237] ivtv0: Encoder revision: 0x02060039

```

Can you also try a different PCI slot for your PVR card.

Regards
Ian Dobson

---

### Post by linnix on 2008-09-06
I am having a similar issue with a PVR 500

Mythfrontend reports:

```
2008-09-06 07:18:59.845 Connecting to backend server: 192.168.0.103:6543 (try 1 of 5)
2008-09-06 07:18:59.846 Using protocol version 40
2008-09-06 07:18:59.853 TV: Attempting to change from None to WatchingLiveTV
2008-09-06 07:18:59.854 Using protocol version 40
2008-09-06 07:19:07.527 RingBuf(/var/lib/mythtv/recordings/1023_20080906071859.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1023_20080906071859.mpg'.
2008-09-06 07:19:07.548 New DB connection, total: 3
2008-09-06 07:19:07.549 Connected to database 'mythconverg' at host: 192.168.0.103
2008-09-06 07:19:07.606 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/1023_20080906071859.mpg
2008-09-06 07:19:07.609 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-09-06 07:19:07.623 DPMS Deactivated 
2008-09-06 07:19:12.089 TV Error: LiveTV not successfully started
2008-09-06 07:19:12.129 DPMS Reactivated.

```

and:
grep ivtv /var/log/messages
gives the following

```

Sep  6 06:46:54 mythbuntu-livingroom kernel: [   25.848117] ivtv:  Start initialization, version 1.1.0
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.105005] ivtv0: Initializing card #0
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.105010] ivtv0: Autodetected Hauppauge card (cx23416 based)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.197465] ivtv0: Autodetected WinTV PVR 500 (unit #1)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.387449] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.387722] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.539082] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.562812] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571619] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571638] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571656] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571685] ivtv0: Registered device video24 for encoder PCM (320 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571703] ivtv0: Registered device radio0 for encoder radio
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571705] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571806] ivtv1: Initializing card #1
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.571810] ivtv1: Autodetected Hauppauge card (cx23416 based)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.580763] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.595983] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.666733] ivtv1: Correcting tveeprom data: no radio present on second unit
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.666735] ivtv1: Autodetected WinTV PVR 500 (unit #2)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.713253] ivtv1: Registered device video1 for encoder MPG (4096 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.713284] ivtv1: Registered device video33 for encoder YUV (2048 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.713315] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.713345] ivtv1: Registered device video25 for encoder PCM (320 kB)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.713348] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
Sep  6 06:46:54 mythbuntu-livingroom kernel: [   26.721071] ivtv:  End initialization
Sep  6 06:47:02 mythbuntu-livingroom kernel: [   41.774521] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Sep  6 06:47:03 mythbuntu-livingroom kernel: [   41.971087] ivtv1: Encoder revision: 0x02060039
Sep  6 06:47:03 mythbuntu-livingroom kernel: [   42.656168] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Sep  6 06:47:03 mythbuntu-livingroom kernel: [   42.854541] ivtv0: Encoder revision: 0x02060039

```

Not sure if this has been cleared up at all. but any help would be appreciated

---

