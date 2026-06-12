---
title: "Files that now have trouble playing with internal player"
date: 2009-08-14
forum: Mythbuntu
---

### Post by bcg30506 on 2009-08-14
I have 2 types of files that used to play perfectly in mythfrontend's internal player but now only play smoothly with mplayer.  The only thing I did was a apt-get upgrade to stay current as I run the svn of mythbuntu 9.04.  Something in the last week of two of mythtv or a supporting library must have changed to "break" playback of these.  When I try now, they play for a couple of seconds, then pause for a second or so, then play for another couple, then pause, etc.

Here is the output of ffmpeg -i for each to show the details of the format and codecs:

File #1:
Input #0, mpegts, from '00068.MTS':
  Duration: 00:01:44.12, start: 0.460433, bitrate: 16080 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s

File #2:
Seems stream 1 codec frame rate differs from container frame rate: 49.97 (6246/125) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'orchestra.mp4':
  Duration: 00:08:29.44, start: 0.000000, bitrate: 474 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 450x360, 25 tbr, 24.98 tbn, 49.97 tbc

The mythfrontend.log shows this while playing them, and again, did not as recent as last week:

2009-08-14 10:01:37.785 TV: Changing from None to WatchingPreRecorded
2009-08-14 10:01:37.786 New DB connection, total: 4
2009-08-14 10:01:37.787 The realtime priority setting is not enabled.
2009-08-14 10:01:37.818 Connected to database 'mythconverg' at host: myth
2009-08-14 10:01:37.887 [h264 @ 0xb718c850]B picture before any references, skipping
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]decode_slice_header error
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]no frame!
2009-08-14 10:01:37.888 AFD Error: Unknown decoding error
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]B picture before any references, skipping
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]decode_slice_header error
2009-08-14 10:01:37.888 Video timing method: USleep with busy wait
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]no frame!
2009-08-14 10:01:37.888 AFD Error: Unknown decoding error
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]B picture before any references, skipping
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]decode_slice_header error
2009-08-14 10:01:37.888 [h264 @ 0xb718c850]no frame!
2009-08-14 10:01:37.888 AFD Error: Unknown decoding error
2009-08-14 10:01:37.889 [h264 @ 0xb718c850]B picture before any references, skipping
2009-08-14 10:01:37.889 [h264 @ 0xb718c850]decode_slice_header error
2009-08-14 10:01:37.889 [h264 @ 0xb718c850]no frame!
2009-08-14 10:01:37.889 AFD Error: Unknown decoding error
2009-08-14 10:01:39.666 NVP: prebuffering pause
2009-08-14 10:01:41.270 NVP: prebuffering pause
2009-08-14 10:01:42.791 NVP: prebuffering pause
2009-08-14 10:01:44.259 WriteAudio: buffer underrun
2009-08-14 10:01:44.324 NVP: prebuffering pause
2009-08-14 10:01:44.326 WriteAudio: buffer underrun
2009-08-14 10:01:45.961 NVP: prebuffering pause
2009-08-14 10:02:25.473 DPMS Reactivated.
2009-08-14 10:02:31.115 TV: Attempting to change from WatchingPreRecorded to None

ffmpeg version:

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

mythtv version: 2:0.21.0+fixes-21228-openglvdpau2-nv180-0ubuntu0

---

### Post by utar on 2009-08-14
I assume from the above that you are using JYA's repository.  I had an issue with BBC-HD after an update with the same messages in my Myth log.

There was a further update on Wednesday though which seems to have fixed the problem.

You may want to check you are up to date.

[Edit: you may also want to check you haven't accidentally changed any of the audio buffering options]


Utar

---

### Post by bcg30506 on 2009-08-14
I did an update and upgrade this morning and still have the same symptoms.  To my knowledge I did not change audio options, but where and what do I check to be sure?

---

### Post by utar on 2009-08-14
See [http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html) for the recommended audio settings.

Have you tried disabling vdpau (which I assume you are using) and seeing if that makes a difference?


Utar

---

### Post by bcg30506 on 2009-08-14
utar got me pointed in the right direction and now the problem is solved!  Thank you.  All files play perfectly and beautifully.

This is the site that had the "fix", which was a Playback Profile I had to create.  Odd that I didn't need this for VDPAU before the update earlier this week, but glad it took care of it.

[http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html](http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html)

Specifically, here is what I did:

In mythfrontend, go into Setup -> TV Settings -> Playback -> Playback Profiles. Create a new playback profile VDPAU.

If you have a nVidia < 8600GT or < 9500GT, use the following profile:

<      W: 1920 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Advanced 2X

>=    W: 0 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Temporal 2X

I hope this helps someone else out.  The log file proof of it working is below for reference.


Test File #1:

2009-08-14 15:58:19.368 TV: Attempting to change from None to WatchingPreRecorded
2009-08-14 15:58:19.468 DPMS Deactivated 
2009-08-14 15:58:19.695 AFD: Opened codec 0x9b0b480, id(H264_VDPAU) type(Video)
2009-08-14 15:58:19.695 AFD: codec AC3 has 2 channels
2009-08-14 15:58:19.696 AFD: Opened codec 0x8f96490, id(AC3) type(Audio)
2009-08-14 15:58:19.697 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-14 15:58:19.697 Opening ALSA audio device 'default'.
2009-08-14 15:58:19.730 Mixer unable to find control Master 1
2009-08-14 15:58:19.730 mixer unable to find control Master 1
2009-08-14 15:58:20.098 OSD Theme Dimensions W: 1280 H: 720
2009-08-14 15:58:20.114 Unknown altfont: infofont in textarea: callsign
2009-08-14 15:58:20.273 TV: Changing from None to WatchingPreRecorded
2009-08-14 15:58:20.275 The realtime priority setting is not enabled.
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]B picture before any references, skipping
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]decode_slice_header error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]no frame!
2009-08-14 15:58:20.295 AFD Error: Unknown decoding error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]B picture before any references, skipping
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]decode_slice_header error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]no frame!
2009-08-14 15:58:20.295 AFD Error: Unknown decoding error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]B picture before any references, skipping
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]decode_slice_header error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]no frame!
2009-08-14 15:58:20.295 AFD Error: Unknown decoding error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]B picture before any references, skipping
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]decode_slice_header error
2009-08-14 15:58:20.295 [h264_vdpau @ 0xb72a2850]no frame!
2009-08-14 15:58:20.295 AFD Error: Unknown decoding error
2009-08-14 15:58:20.375 Video timing method: USleep with busy wait
2009-08-14 16:00:03.961 TV: Attempting to change from WatchingPreRecorded to None
2009-08-14 16:00:04.070 TV: Changing from WatchingPreRecorded to None
2009-08-14 16:00:04.422 DPMS Reactivated.


Test File #2:

2009-08-14 16:01:36.450 TV: Attempting to change from None to WatchingPreRecorded
2009-08-14 16:01:36.453 DPMS Deactivated 
2009-08-14 16:01:36.470 [h264 @ 0xb72a2850]brainfart cropping not supported, this could look slightly wrong ...
2009-08-14 16:01:36.473 AFD: codec AAC has 2 channels
2009-08-14 16:01:36.474 AFD: Opened codec 0x9b0b480, id(AAC) type(Audio)
2009-08-14 16:01:36.599 AFD: Opened codec 0x99bf4c0, id(H264_VDPAU) type(Video)
2009-08-14 16:01:36.601 Opening audio device 'default'. ch 2(2) sr 44100
2009-08-14 16:01:36.601 Opening ALSA audio device 'default'.
2009-08-14 16:01:36.635 Mixer unable to find control Master 1
2009-08-14 16:01:36.635 mixer unable to find control Master 1
2009-08-14 16:01:36.960 OSD Theme Dimensions W: 1280 H: 720
2009-08-14 16:01:36.975 Unknown altfont: infofont in textarea: callsign
2009-08-14 16:01:37.128 TV: Changing from None to WatchingPreRecorded
2009-08-14 16:01:37.129 The realtime priority setting is not enabled.
2009-08-14 16:01:37.133 [h264_vdpau @ 0xb72a2850]brainfart cropping not supported, this could look slightly wrong ...
2009-08-14 16:01:37.133 VDPAU: Forcing H.264 baseline profile to main - decoding may fail.
2009-08-14 16:01:37.231 Video timing method: USleep with busy wait
2009-08-14 16:02:46.150 DPMS Reactivated.
2009-08-14 16:02:47.287 TV: Attempting to change from WatchingPreRecorded to None
2009-08-14 16:02:47.340 TV: Changing from WatchingPreRecorded to None

---

