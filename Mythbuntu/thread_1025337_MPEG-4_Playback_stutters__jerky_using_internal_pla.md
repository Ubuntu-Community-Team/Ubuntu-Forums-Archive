---
title: "MPEG-4 Playback stutters / jerky using internal player"
date: 2008-12-30
forum: Mythbuntu
---

### Post by Geurrilla on 2008-12-30
Hey guys,

I'm trying to get the Internal player to work nicely for mythvideo (I hate the lack integration with mplayer / vlc / xine) -- however for some reason when playing MPEG-4 files it is either jerky or seems to be playing at 1/2x!

Getting very frustrated with it, and no matter what Playback profile I change it to or create it's still the same. 

Mythfrontend.log reports the following:

```
2008-12-30 14:24:23.925 XMLParse::LoadTheme using /usr/share/mythtv/themes/neon-wide/video-ui.xml
2008-12-30 14:24:24.734 TV: Attempting to change from None to WatchingPreRecorded
2008-12-30 14:24:24.736 DPMS Deactivated 
2008-12-30 14:24:24.986 AFD: Opened codec 0xae7c80, id(MPEG4) type(Video)
2008-12-30 14:24:24.986 AFD: codec MP3 has 2 channels
2008-12-30 14:24:24.986 AFD: Opened codec 0xae7680, id(MP3) type(Audio)
2008-12-30 14:24:24.987 Opening audio device 'default'. ch 2(2) sr 48000
2008-12-30 14:24:24.987 Opening ALSA audio device 'default'.
2008-12-30 14:24:25.035 Mixer unable to find control Master
2008-12-30 14:24:25.035 Mixer unable to find control Master
2008-12-30 14:24:25.045 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-30 14:24:25.065 OSD Theme Dimensions W: 640 H: 480
2008-12-30 14:24:25.231 TV: Changing from None to WatchingPreRecorded
2008-12-30 14:24:25.233 Realtime priority would require SUID as root.
2008-12-30 14:24:25.253 mdb:34, lastbuf:0 skipping granule 0
2008-12-30 14:24:25.337 Video timing method: USleep with busy wait
2008-12-30 14:24:26.108 WriteAudio: buffer underrun
2008-12-30 14:24:26.357 WriteAudio: buffer underrun
2008-12-30 14:24:26.692 WriteAudio: buffer underrun
2008-12-30 14:24:26.859 WriteAudio: buffer underrun
2008-12-30 14:24:27.025 WriteAudio: buffer underrun
2008-12-30 14:24:27.110 WriteAudio: buffer underrun
2008-12-30 14:24:27.360 WriteAudio: buffer underrun
2008-12-30 14:24:27.526 WriteAudio: buffer underrun
2008-12-30 14:24:27.611 WriteAudio: buffer underrun
2008-12-30 14:24:27.863 WriteAudio: buffer underrun
2008-12-30 14:24:27.944 WriteAudio: buffer underrun
2008-12-30 14:24:28.027 WriteAudio: buffer underrun
2008-12-30 14:24:28.277 WriteAudio: buffer underrun
2008-12-30 14:24:28.364 WriteAudio: buffer underrun
2008-12-30 14:24:28.445 WriteAudio: buffer underrun
2008-12-30 14:24:28.695 WriteAudio: buffer underrun
2008-12-30 14:24:28.778 WriteAudio: buffer underrun
2008-12-30 14:24:28.863 WriteAudio: buffer underrun
2008-12-30 14:24:29.029 WriteAudio: buffer underrun
2008-12-30 14:24:29.196 WriteAudio: buffer underrun
2008-12-30 14:24:29.364 WriteAudio: buffer underrun
2008-12-30 14:24:29.615 WriteAudio: buffer underrun
2008-12-30 14:24:29.698 WriteAudio: buffer underrun
2008-12-30 14:24:29.865 WriteAudio: buffer underrun
2008-12-30 14:24:30.115 WriteAudio: buffer underrun
2008-12-30 14:24:30.366 WriteAudio: buffer underrun
2008-12-30 14:24:30.781 WriteAudio: buffer underrun
2008-12-30 14:24:30.867 WriteAudio: buffer underrun
2008-12-30 14:24:31.032 WriteAudio: buffer underrun
2008-12-30 14:24:31.117 WriteAudio: buffer underrun
2008-12-30 14:24:31.367 WriteAudio: buffer underrun
2008-12-30 14:24:31.533 WriteAudio: buffer underrun
2008-12-30 14:24:31.618 WriteAudio: buffer underrun
2008-12-30 14:24:31.871 WriteAudio: buffer underrun
2008-12-30 14:24:31.951 WriteAudio: buffer underrun
2008-12-30 14:24:32.034 WriteAudio: buffer underrun
2008-12-30 14:24:32.285 WriteAudio: buffer underrun
2008-12-30 14:24:32.370 WriteAudio: buffer underrun
2008-12-30 14:24:32.452 WriteAudio: buffer underrun
2008-12-30 14:24:32.703 WriteAudio: buffer underrun
2008-12-30 14:24:32.748 TV: Attempting to change from WatchingPreRecorded to None
2008-12-30 14:24:32.804 TV: Changing from WatchingPreRecorded to None
2008-12-30 14:24:33.847 DPMS Reactivated.

```

Has anyone encountered this before? 

PS. the videos in question work perfectly in Mplayer / Xine / VLC.

---

### Post by Geurrilla on 2008-12-30
[I]For some reason (unbeknownst to me) I fixed this issue by setting the Audio output device to "ALSA:analog."

No more stuttering or buffer underruns.
[/I]

Actually all that did was kill the sound (I didn't notice because my speakers weren't plugged in)

So obviously the problem is with the sound rather than the video. Gah.

---

