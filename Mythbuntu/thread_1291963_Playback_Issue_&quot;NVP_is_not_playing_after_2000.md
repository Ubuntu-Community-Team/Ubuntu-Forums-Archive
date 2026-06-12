---
title: "Playback Issue: &quot;NVP is not playing after 20000 msec&quot;"
date: 2009-10-15
forum: Mythbuntu
---

### Post by sgunther on 2009-10-15
I am having an occasional issue with show playback where I press play on a show, the screen goes black and then ~25 seconds later it drops back to the MythFrontend screen.

The mythfrontend.log file shows;
```
2009-10-15 08:10:47.004 AFD: Opened codec 0x8300060, id(MPEG2VIDEO) type(Video)
2009-10-15 08:10:47.004 AFD: codec MP2 has 2 channels
2009-10-15 08:10:47.004 AFD: Opened codec 0x91f6c40, id(MP2) type(Audio)
2009-10-15 08:10:47.012 Opening audio device 'default'. ch 2(2) sr 48000
2009-10-15 08:10:47.012 Opening ALSA audio device 'default'.
2009-10-15 08:11:06.803 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-10-15 08:11:06.804 TV: Changing from None to WatchingPreRecorded
2009-10-15 08:11:06.810 TV: Attempting to change from WatchingPreRecorded to None
2009-10-15 08:11:32.192 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-10-15 08:11:32.354 OSD Theme Dimensions W: 640 H: 480
2009-10-15 08:11:32.972 The realtime priority setting is not enabled.
2009-10-15 08:11:33.082 Video timing method: USleep with busy wait
2009-10-15 08:11:33.143 TV: Changing from WatchingPreRecorded to None
2009-10-15 08:11:34.416 DPMS Reactivated.
```
Watching the logs in real time with the pause the pertinent line appears to be "**TV Error: StartPlayer(): NVP is not playing after 20000 msec**".  I realize that 20 seconds to start a video playback is a long time.  Any ideas on what could be causing this?  My recordedseek database has ~2.1 Million entries, could seeking the database with its large size be causing issues with playback?

-Steve

---

