---
title: "Live and Recorded TV choppy 11.04"
date: 2011-09-18
forum: Mythbuntu
---

### Post by Chewiesw on 2011-09-18
Hello

I have just upgraded all my hardware and completed a fresh install of Natty 11.04 64bit. Live TV and recorded playback are very choppy although the video playback is fine.

Here is part of the front end log.

```
2011-09-17 18:52:54.154 Found mainmenu.xml for theme 'Mythbuntu'
2011-09-17 18:52:54.313 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-09-17 18:52:54.313 Using protocol version 63
2011-09-17 18:53:00.217 TV: Attempting to change from None to WatchingLiveTV
2011-09-17 18:53:00.217 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-09-17 18:53:00.217 Using protocol version 63
2011-09-17 18:53:00.364 Spawning LiveTV Recorder -- begin
2011-09-17 18:53:00.666 Spawning LiveTV Recorder -- end
2011-09-17 18:53:00.670 We have a playbackURL(/var/lib/mythtv/livetv/1000_20110917185300.mpg) & cardtype(DUMMY)
2011-09-17 18:53:00.670 We have a RingBuffer
2011-09-17 18:53:00.897 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-09-17 18:53:00.916 OSD: Base theme size: 1280x720
2011-09-17 18:53:00.916 OSD: Scaling factors: 0.5625x0.8
2011-09-17 18:53:00.939 OSD: Base theme size: 1280x720
2011-09-17 18:53:00.939 OSD: Scaling factors: 0.5625x0.8
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
2011-09-17 18:53:00.981 Player(0): Video timing method: DRM
2011-09-17 18:53:00.997 TV: Changing from None to WatchingLiveTV
2011-09-17 18:53:00.997 TV: State is LiveTV & mctx == ctx
2011-09-17 18:53:01.000 TV: UpdateOSDInput done
2011-09-17 18:53:01.000 TV: UpdateLCD done
2011-09-17 18:53:01.000 TV: ITVRestart done
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 720 x 576
YadifDeint: Using existing thread.
YadifDeint: size changed from 0 x 0 -> 480 x 480
YadifDeint: Using existing thread.
2011-09-17 18:53:02.579 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-09-17 18:53:02.590 OSD: Base theme size: 1280x720
2011-09-17 18:53:02.590 OSD: Scaling factors: 0.375x0.666667
2011-09-17 18:53:02.608 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-09-17 18:53:02.608 AFD: Opened codec 0x35a1020, id(MPEG2VIDEO) type(Video)
2011-09-17 18:53:02.608 AFD: codec MP2 has 2 channels
2011-09-17 18:53:02.608 AFD: Opened codec 0x666d6f0, id(MP2) type(Audio)
2011-09-17 18:53:02.886 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-09-17 18:53:02.962 ALSA, Error: Setting hardware audio buffer size to 6016
2011-09-17 18:53:03.042 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-09-17 18:53:03.042 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-09-17 18:53:03.042 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-09-17 18:53:03.123 AudioPlayer: Enabling Audio
2011-09-17 18:53:03.194 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-09-17 18:53:03.295 [mpeg2video @ 0x7f0ebdc32580]warning: first frame is no keyframe
2011-09-17 18:53:03.296 [mpeg2video @ 0x7f0ebdc32580]warning: first frame is no keyframe
2011-09-17 18:53:03.369 VideoOutput: Created YV12 OSD.
2011-09-17 18:53:09.668 TV: Attempting to change from WatchingLiveTV to None
2011-09-17 18:53:10.197 TV: Changing from WatchingLiveTV to None
2011-09-17 18:53:22.055 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit 
```

The only errors, that jump out at me are

```
2011-09-17 18:53:02.962 ALSA, Error: Setting hardware audio buffer size to 6016
2011-09-17 18:53:03.042 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-09-17 18:53:03.042 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-09-17 18:53:03.042 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
```

Could this be the cause of the choppy playback? If so how do I fix it?

---

### Post by uteck on 2011-09-18
Did you check your playback options on the frontend?  I seem to recall that when I upgraded to 11.04 some of the defaults like 'real-time priority threads' was enabled and casued choppy playback for me.  And VDPAU was not selected.

---

### Post by Chewiesw on 2011-09-18
Hi Uteck,

I disabled 'real-time priority threads' which had no effect, I am still getting choppy live TV. I don't think I can enable VPDPAU as I am using the onboard INTEL graphics.

---

### Post by Chewiesw on 2011-09-19
Solved my issue, such a dumba$$ mistake, the TV Format Option on the backend was set to NTSC instead of PAL.

---

