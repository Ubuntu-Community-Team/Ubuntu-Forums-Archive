---
title: "Remote Frontend Fails to Play anything  After last apt-get update (1-7-2013)"
date: 2013-01-12
forum: Mythbuntu
---

### Post by ravenium on 2013-01-12
Hello Everyone,

I just moved back to Mythtv after purchasing an HDHomeRun this past fall. Been enjoying mythbuntu so far despite a few glitches (laggy program guide, death of internet streaming plugin, my failed attempts to auto-transcode and export recordings for copying to a tablet, etc).  That's probably for another post and I fully expect a few people to smack me upside the head and point out that there are already 50 posts on said topics.  Anyhow, on to my real issue!

I have 2 computers with mythbuntu 12.04 on them: a retired desktop running the master backend/frontend in the office, and an ex-mac mini running frontend only in the living room. So far everything's worked.  

I've added mythtv-updates to my package update list (via that menu option in the system center), which seems to be an issue because I'm guessing it's grabbing nightly mythtv updates.  Normally this doesn't pose a problem, but from time to time it's broken itself, requiring me to reboot/wait for another build.  Guessing this was my first mistake, eh?

Anyhow, on to the story: I updated both systems the morning of 1/7/2013 and cycled both.  Now when I go to watch either Live TV or any of my recorded programs on the front end, it freezes for 30 seconds, then displays "Please Wait..."....then hangs there in perpetuity.  Occasionally Live TV will show the program guide, then a 1/10 second of audio, then freeze.

What's odd is, the backend/frontend combo system works fine. It records fine and I can watch both live TV and recordings on it without issue.

I also tried accessing the backend via XBMC's new frontend plugin from my laptop and it looked to be the same issue - the video froze, showed 1/2 a second...waited 30 seconds, showed another .5 second.  Always buffering, buffering...

I've tried cycling all systems involved multiple times with no luck.  Is there anything I'm missing?

From the backend:

```
Jan 12 14:35:46 zoidberg mythbackend[1432]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jan 12 14:35:46 zoidberg mythbackend[1432]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: nibbler as a client (events: 0)
Jan 12 14:35:46 zoidberg mythbackend[1432]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jan 12 14:35:46 zoidberg mythbackend[1432]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: nibbler as a remote file transfer
```

Frontend:

```
Jan 12 14:36:55 nibbler mythfrontend[1383]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
Jan 12 14:36:55 nibbler mythfrontend[1383]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingPreRecorded
Jan 12 14:36:55 nibbler mythfrontend[1383]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
Jan 12 14:36:55 nibbler mythfrontend[1383]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
Jan 12 14:36:55 nibbler mythfrontend[1383]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 113ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuULLP
Jan 12 14:36:55 nibbler mythfrontend[1383]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
Jan 12 14:36:55 nibbler mythfrontend[1383]: E Decoder avformatdecoder.cpp:4396 (GetFrame) decoding error#012#011#011#011eno: Input/output error (5)
Jan 12 14:36:56 nibbler mythfrontend[1383]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 117ms for video buffers AAAAAAAAAAAAAAAUAAUUUUUUuUULuAAP
Jan 12 14:36:56 nibbler mythfrontend[1383]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 218ms for video buffers AAAAAAAAAAAAAAAUAAUUUUUUuUULuAAP
Jan 12 14:36:56 nibbler mythfrontend[1383]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 335ms for video buffers AAAAAAAAAAAAAAAUAAUUUUUUuUULuAAP
Jan 12 14:36:56 nibbler mythfrontend[1383]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 452ms for video buffers AAAAAAAAAAAAAAAUAAUUUUUUuUULuAAP
Jan 12 14:36:56 nibbler mythfrontend[1383]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 553ms for video buffers AAAAAAAAAAAAAAAUAAUUUUUUuUULuAAP


and before that a bunch of

Jan 12 14:36:36 nibbler mythfrontend[1383]: I CoreContext ringbuffer.cpp:1086 (WaitForAvail) RingBuf(myth://10.2.2.52:6543/1706_20130111200000.mpg): Waited 12.8 seconds for data #012#011#011#011to become available... 0 < 32768


```

---

### Post by Ubu_Fester on 2013-04-06
I'm getting a similar error in my log -- but not sure if it's my frontend failing or just the commercial flagging process job.   

This is driving my crazy -- after an overnight of recording, I find a number of crashes on my mythbox, or if I'm watching a show and commflagging is processing, my system "sometimes" jumps to a high load (e.g., load=11).

Here is a snippet from my mythcommflag LOG 


> 
Apr  6 08:31:11 HTPC mythcommflag[3739]: E Decoder avformatdecoder.cpp:4233 (ProcessAudioPacket) AFD: [COLOR=#ff0000]**Unknown audio decoding error**[/COLOR]
Apr  6 08:31:33  mythcommflag[3739]: last message repeated 2 times
Apr  6 08:31:33 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 0% Completed @ 97.5419 fps.
Apr  6 08:34:07 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 10% Completed @ 97.4371 fps.
Apr  6 08:36:46 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 20% Completed @ 97.4157 fps.
Apr  6 08:39:20 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 30% Completed @ 97.4052 fps.
Apr  6 08:41:59 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 40% Completed @ 97.3751 fps.
Apr  6 08:44:34 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 50% Completed @ 97.336 fps.
Apr  6 08:47:13 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 60% Completed @ 97.313 fps.
Apr  6 08:49:47 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 70% Completed @ 97.3111 fps.
Apr  6 08:52:27 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 80% Completed @ 97.318 fps.
Apr  6 08:55:01 HTPC mythcommflag[3739]: I CoreContext ClassicCommDetector.cpp:535 (go) 90% Completed @ 97.3236 fps.
[B][COLOR=#ff0000]Apr  6 08:57:37 HTPC mythcommflag[3739]: E Decoder avformatdecoder.cpp:4396 (GetFrame) decoding error#012#011#011#011eno: Input/output error (5)
[/COLOR][/B]Apr  6 08:57:38 HTPC mythcommflag[3739]: N CoreContext main.cpp:939 (FlagCommercials) Finished, 6 break(s) found.
Apr  6 08:57:38 HTPC mythcommflag[3739]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.


Thanks in advance

---

### Post by Ubu_Fester on 2013-04-07
I add a little more detail and moved my question to [h=1]Thread: [MythTV backend setup has closed unexpectedly]("http://ubuntuforums.org/showthread.php?t=2133073")  found at:[COLOR=#222222]  [/COLOR][http://ubuntuforums.org/showthread.php?t=2133073](http://ubuntuforums.org/showthread.php?t=2133073)[COLOR=#222222] [/COLOR][/h]

---

### Post by ravenium on 2013-04-16
Quick update - I found out this was due to a kernel bug introduced with newer mythbuntu kernels vs my r8168 onboard ethernet (Asus P5B mobo).  For some reason it'll vomit under heavy network loads unless you grab the r8168 drivers and build it as a module.  Not sure why, but building the module fixed everything.

---

