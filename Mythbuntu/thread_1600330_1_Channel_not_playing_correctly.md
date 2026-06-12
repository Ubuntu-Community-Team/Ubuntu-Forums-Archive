---
title: "1 Channel not playing correctly"
date: 2010-10-18
forum: Mythbuntu
---

### Post by Gobanana on 2010-10-18
I recently installed Mythbuntu 10.04 on a frontend/backend PC for the living room, and a Frontend only system for the bedroom.  After a lot of troubleshooting and trial and error I have everything working except one thing.

I just can't get Channel 5 (ABC on RF channel 35) to play correctly.  When I change to this channel the video seems to play at a fast speed for about 5 seconds then it starts stuttering, i'm guessing because it's used up all the buffer and can't play at that speed anymore.  The audio sounds fine but lags behind the video by a good 5 seconds.  some things I've tried:

It's the same stuttering problem on both the living room machine using CPU++ and the bedroom frontend with VDPAU.

It plays fine with VLC on the mythbuntu machine.  

The channel appears to be broadcast in 720P, other 720P channels play just fine.

I've tried changing to may setting to list in the frontend for both audio and video, some make it worse, but none fix it.

top only shows ~40% CPU usage while watching live TV

here's what i get when playing channel 5


```
2010-10-18 16:29:20.854 OSD Theme Dimensions W: 1280 H: 720
2010-10-18 16:29:20.898 ProgramInfo(): Updated pathname '':'' -> '1052_20101018162920.mpg'
2010-10-18 16:29:20.928 TV: Changing from None to WatchingLiveTV
2010-10-18 16:29:20.928 TV: State is LiveTV & mctx == ctx
2010-10-18 16:29:20.929 Realtime priority would require SUID as root.
2010-10-18 16:29:20.929 TV: UpdateOSDInput done
2010-10-18 16:29:20.929 TV: UpdateLCD done
2010-10-18 16:29:20.930 TV: ITVRestart done
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
yadifdeint: Created 2 threads (2 requested)
2010-10-18 16:29:20.949 OpenGLVideoSync()
2010-10-18 16:29:20.967 Video timing method: SGI OpenGL
2010-10-18 16:29:21.998 ProgramInfo(): Updated pathname '':'' -> '1052_20101018162921.mpg'
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 704 x 480
yadifdeint: Created 2 threads (2 requested)
2010-10-18 16:29:23.215 AFD: Opened codec 0x7f0b8d318000, id(MPEG2VIDEO) type(Video)
2010-10-18 16:29:23.215 AFD: codec AC3 has 2 channels
2010-10-18 16:29:23.216 AFD: Opened codec 0x7f0b8d318660, id(AC3) type(Audio)
2010-10-18 16:29:23.268 Opening audio device 'spdif'. ch 2(2) sr 48000 (reenc 1)
2010-10-18 16:29:23.268 Opening ALSA audio device 'spdif'.
2010-10-18 16:29:23.303 NVP(7): Enabling Audio
2010-10-18 16:29:32.695 ProgramInfo(): Updated pathname '':'' -> '1051_20101018162932.mpg'
2010-10-18 16:29:32.696 ProgramInfo(): Updated pathname '':'' -> '1051_20101018162932.mpg'
2010-10-18 16:29:32.697 ProgramInfo(): Updated pathname '':'' -> '1051_20101018162932.mpg'
2010-10-18 16:29:33.137 ProgramInfo(): Updated pathname '':'' -> '1051_20101018162933.mpg'
2010-10-18 16:29:33.335 WriteAudio: buffer underrun
2010-10-18 16:29:34.816 NVP(7): Prebuffer wait timed out 10 times.
2010-10-18 16:29:36.400 NVP(7): Prebuffer wait timed out 20 times.
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 1280 x 720
yadifdeint: Created 2 threads (2 requested)
2010-10-18 16:29:37.041 AFD: Opened codec 0x7f0b84bc1eb0, id(MPEG2VIDEO) type(Video)
2010-10-18 16:29:37.041 AFD: codec AC3 has 6 channels
2010-10-18 16:29:37.042 AFD: Opened codec 0x7f0b84a328b0, id(AC3) type(Audio)
2010-10-18 16:29:37.042 AFD: codec AC3 has 2 channels
2010-10-18 16:29:37.042 AFD: Opened codec 0x7f0b8484b220, id(AC3) type(Audio)
2010-10-18 16:29:37.071 Opening audio device 'spdif'. ch 2(6) sr 48000 (reenc 0)
2010-10-18 16:29:37.071 Opening ALSA audio device 'spdif'.
2010-10-18 16:29:48.484 NVP(7): prebuffering pause
2010-10-18 16:29:48.735 NVP(7): prebuffering pause
2010-10-18 16:29:49.203 NVP(7): prebuffering pause
2010-10-18 16:29:50.067 NVP(7): prebuffering pause
2010-10-18 16:29:50.350 NVP(7): prebuffering pause
2010-10-18 16:29:51.505 NVP(7): prebuffering pause
2010-10-18 16:29:51.886 NVP(7): prebuffering pause
2010-10-18 16:29:52.136 NVP(7): prebuffering pause
2010-10-18 16:29:52.367 NVP(7): prebuffering pause
2010-10-18 16:29:52.650 NVP(7): prebuffering pause
2010-10-18 16:29:52.884 NVP(7): prebuffering pause
2010-10-18 16:29:53.086 NVP(7): prebuffering pause
2010-10-18 16:29:53.369 NVP(7): prebuffering pause
2010-10-18 16:29:53.750 NVP(7): prebuffering pause
2010-10-18 16:29:53.932 TV: Attempting to change from WatchingLiveTV to None
2010-10-18 16:29:53.950 ~OpenGLVideoSync() -- closing opengl vsync
2010-10-18 16:29:55.082 TV: Changing from WatchingLiveTV to None
```

My setup is as follows:
Front/backend
Quad core Q6600 
4Gb RAM
geforce 8800GTX
HDHomeRun 2 tuner
1.5TB HD as both system and storage drive

Frontend
ZBOXHD-ID11-U
Atom D510
Nex Gen ION
2GB RAM

both are running Mythbuntu 10.04 the Frontend needed some tweaks to get the HDMI audio working.

Does anyone have any ideas?

---

### Post by GaryP2 on 2010-10-18
[FONT=Calibri][SIZE=3]Are you in the Twin Cities area? I'm not, but I noticed this thread which sounds like the issue you are having. KSTP-TV is an ABC affiliate on channel 5 (RF channel 35).[/SIZE][/FONT]

 
[[SIZE=2]http://www.gossamer-threads.com/lists/mythtv/users/455048[/SIZE]]("http://www.gossamer-threads.com/lists/mythtv/users/455048")

---

### Post by Gobanana on 2010-10-19
Wow thanks, I do live in the twin cities area.  I've been banging my head over this issue for over a week, I thought for sure the issue was on my end since I'm new to MythTV.  That explain why no setting changes ever seemed to help :).

---

