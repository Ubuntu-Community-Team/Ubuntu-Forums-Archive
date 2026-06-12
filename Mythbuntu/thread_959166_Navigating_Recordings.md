---
title: "Navigating Recordings"
date: 2008-10-26
forum: Mythbuntu
---

### Post by chrisblue on 2008-10-26
Hi I have an issue with a relatively new combined frontend/backend install of Mythbuntu 8.04.1

The problem is that I am unable to navigate (ie fast forward, skip forward etc) within a recording. I can fast forward 3x but when I try to stop it exits the recording with the the dialog box to chose to delete. If it try to move faster than 3x then the playback freezes and after a time sometimes drops back to the media library window, sometimes freezes totally and needs a reboot.

This doesn't affect liveTV where I can scroll back and forwards with no issues.

Previous to this the box was working fine though I did have a database issue where one of the tables needed repair which was preventing me getting guide data.

Any ideas of where to start looking?

Thanks Chris.

---

### Post by uopjohnson on 2008-10-27
This can be caused by a corupted recordseek table in your database.  There is a database repair script in mythbuntu-control-center which you can run.  Does that fix the problem?

---

### Post by chrisblue on 2008-10-28
I'll try that and let you know. Might be related to the previous database errors I had with the program guide.

Thanks Jon

Chris

---

### Post by davidMC1982 on 2008-10-29
Hi,

I have exactly the same problem as above. I can't skip forward through a recording and when I skip back the recording stops. This has only happened recently and I've tried the DB repair/optimisation. It only happens with recent recordings. Recordings of the 21st Oct are fine, after that the problems start. The only clue is in the mythfrontend.log:

2008-10-29 20:28:16.002 AFD: Opened codec 0x63f07f0, id(MPEG2VIDEO) type(Video)
2008-10-29 20:28:16.003 AFD: codec MP3 has 2 channels
2008-10-29 20:28:16.003 AFD: Opened codec 0x63f0bd0, id(MP3) type(Audio)
2008-10-29 20:28:16.003 AFD: Opened codec 0x69cb460, id(DVB_SUBTITLE) type(Subtitle)
2008-10-29 20:28:16.003 AFD: codec MP3 has 1 channels
2008-10-29 20:28:16.003 AFD: Opened codec 0x69cb840, id(MP3) type(Audio)
2008-10-29 20:28:16.789 AFD: Opened codec 0x6609a20, id(MPEG2VIDEO) type(Video)
2008-10-29 20:28:16.789 AFD: codec MP3 has 2 channels
2008-10-29 20:28:16.790 AFD: Opened codec 0x63f07f0, id(MP3) type(Audio)
2008-10-29 20:28:16.790 AFD: codec MP3 has 1 channels
2008-10-29 20:28:16.790 AFD: Opened codec 0x63f0bd0, id(MP3) type(Audio)
2008-10-29 20:28:16.790 AFD: Opened codec 0x4381140, id(DVB_SUBTITLE) type(Subtitle)
2008-10-29 20:28:17.775 TV: Attempting to change from None to WatchingPreRecorded
2008-10-29 20:28:17.785 DPMS Deactivated 
2008-10-29 20:28:17.948 AFD: Opened codec 0x39247e0, id(MPEG2VIDEO) type(Video)
2008-10-29 20:28:17.948 AFD: codec MP3 has 2 channels
2008-10-29 20:28:17.948 AFD: Opened codec 0x110bca0, id(MP3) type(Audio)
2008-10-29 20:28:17.948 AFD: codec MP3 has 1 channels
2008-10-29 20:28:17.948 AFD: Opened codec 0x110c320, id(MP3) type(Audio)
2008-10-29 20:28:17.948 AFD: Opened codec 0x42c29c0, id(DVB_SUBTITLE) type(Subtitle)
2008-10-29 20:28:17.951 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-29 20:28:17.951 Opening ALSA audio device 'default'.
2008-10-29 20:28:17.984 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-10-29 20:28:18.032 OSD Theme Dimensions W: 640 H: 480
2008-10-29 20:28:18.254 TV: Changing from None to WatchingPreRecorded
2008-10-29 20:28:18.257 Realtime priority would require SUID as root.
2008-10-29 20:28:18.354 Video timing method: USleep with busy wait
2008-10-29 20:28:23.109 [mpeg2video @ 0x7f2559a8e5b0]warning: first frame is no keyframe
2008-10-29 20:28:23.110 [mpeg2video @ 0x7f2559a8e5b0]ac-tex damaged at 23 19
2008-10-29 20:28:23.111 [mpeg2video @ 0x7f2559a8e5b0]Warning MVs not available
2008-10-29 20:28:23.310 TV: Attempting to change from WatchingPreRecorded to None
2008-10-29 20:28:23.337 TV: Changing from WatchingPreRecorded to None
2008-10-29 20:28:23.441 DPMS Reactivated.
2008-10-29 20:28:23.590 AFD: Opened codec 0x4f29390, id(MPEG2VIDEO) type(Video)
2008-10-29 20:28:23.591 AFD: codec MP3 has 2 channels
2008-10-29 20:28:23.591 AFD: Opened codec 0x4f29770, id(MP3) type(Audio)
2008-10-29 20:28:23.591 AFD: codec MP3 has 1 channels
2008-10-29 20:28:23.591 AFD: Opened codec 0xb547f0, id(MP3) type(Audio)
2008-10-29 20:28:23.591 AFD: Opened codec 0xb54bd0, id(DVB_SUBTITLE) type(Subtitle)
2008-10-29 20:28:24.135 AFD: Opened codec 0x10b5a50, id(MPEG2VIDEO) type(Video)
2008-10-29 20:28:24.135 AFD: codec MP3 has 2 channels
2008-10-29 20:28:24.135 AFD: Opened codec 0x43584d0, id(MP3) type(Audio)
2008-10-29 20:28:24.135 AFD: codec MP3 has 1 channels
2008-10-29 20:28:24.135 AFD: Opened codec 0x69aade0, id(MP3) type(Audio)
2008-10-29 20:28:24.135 AFD: Opened codec 0x4f29390, id(DVB_SUBTITLE) type(Subtitle)
2008-10-29 20:28:24.388 [mpeg2video @ 0x7f2559a8e5b0]ac-tex damaged at 20 10
2008-10-29 20:28:24.388 [mpeg2video @ 0x7f2559a8e5b0]Warning MVs not available

Thanks for any help,

Dave

---

