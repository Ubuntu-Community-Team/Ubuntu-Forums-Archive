---
title: "Strange recorded DVD playback"
date: 2008-09-28
forum: Mythbuntu
---

### Post by myth01 on 2008-09-28
When playing back recorded DVDs in mythtv, the frontend log keeps showing different errors for different DVDs.

The Hunt For Red October:

```
2008-09-28 11:52:31.187 Opened DVD device at /media/film-1/The Hunt For Red October
2008-09-28 11:52:31.537 There are 1 titles on the disk
2008-09-28 11:52:31.537 Title 0 has 0 parts.
2008-09-28 11:52:31.607 DPMS Deactivated 
2008-09-28 11:52:32.408 AFD: Opened codec 0x8398c60, id(MPEG2VIDEO) type(Video)
2008-09-28 11:52:32.408 NVP: Disabling Audio, params(-1,-1,-1)
2008-09-28 11:52:32.446 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2008-09-28 11:52:32.578 OSD Theme Dimensions W: 1280 H: 720
2008-09-28 11:52:33.247 TV: Changing from None to WatchingPreRecorded
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-09-28 11:52:33.329 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-09-28 11:52:33.332 Video timing method: USleep with busy wait
2008-09-28 11:52:33.701 AFD: Warning, video codec 0x8398c60 id(MPEG2VIDEO) type (Video) already open.
2008-09-28 11:52:33.939 AFD: codec AC3 has 0 channels
2008-09-28 11:52:33.941 AFD: Opened codec 0x9c3aa50, id(AC3) type(Audio)
2008-09-28 11:52:33.951 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-28 11:52:33.951 Opening ALSA audio device 'default'.
2008-09-28 11:52:33.964 NVP: Enabling Audio
2008-09-28 11:52:34.148 GetNextFreeFrame() served a busy frame D. Dropping. AAUUUUUUUUUUUUUUUUUUUUUUUUUUUUL
2008-09-28 11:52:55.273 WriteAudio: buffer underrun
2008-09-28 11:52:55.352 WriteAudio: buffer underrun
2008-09-28 11:52:55.432 WriteAudio: buffer underrun
2008-09-28 11:52:55.513 WriteAudio: buffer underrun
2008-09-28 11:52:55.607 WriteAudio: buffer underrun
2008-09-28 11:52:55.673 WriteAudio: buffer underrun
2008-09-28 11:52:55.753 WriteAudio: buffer underrun
2008-09-28 11:52:55.832 WriteAudio: buffer underrun
2008-09-28 11:52:55.912 WriteAudio: buffer underrun
2008-09-28 11:52:55.992 WriteAudio: buffer underrun
2008-09-28 11:52:56.075 WriteAudio: buffer underrun
2008-09-28 11:52:56.153 WriteAudio: buffer underrun
2008-09-28 11:52:56.233 WriteAudio: buffer underrun
2008-09-28 11:52:56.312 WriteAudio: buffer underrun
2008-09-28 11:52:56.387 NVP: prebuffering pause
2008-09-28 11:52:56.387 WriteAudio: buffer underrun
2008-09-28 11:53:29.063 WriteAudio: buffer underrun
2008-09-28 11:53:29.145 WriteAudio: buffer underrun
2008-09-28 11:53:29.223 WriteAudio: buffer underrun
2008-09-28 11:53:29.303 WriteAudio: buffer underrun
2008-09-28 11:53:29.391 WriteAudio: buffer underrun
2008-09-28 11:53:29.465 WriteAudio: buffer underrun
2008-09-28 11:53:29.543 WriteAudio: buffer underrun
2008-09-28 11:53:29.625 WriteAudio: buffer underrun
2008-09-28 11:53:29.705 WriteAudio: buffer underrun
2008-09-28 11:53:29.783 WriteAudio: buffer underrun
2008-09-28 11:53:29.943 WriteAudio: buffer underrun
2008-09-28 11:53:30.029 WriteAudio: buffer underrun
2008-09-28 11:53:30.103 WriteAudio: buffer underrun
2008-09-28 11:53:30.183 WriteAudio: buffer underrun
2008-09-28 11:53:30.257 NVP: prebuffering pause
2008-09-28 11:53:30.257 WriteAudio: buffer underrun
2008-09-28 11:53:45.039 DPMS Reactivated.
```

Jarhead:

```
2008-09-28 12:18:57.977 Opened DVD device at /media/film-1/Jarhead
2008-09-28 12:18:57.977 There are 1 titles on the disk
2008-09-28 12:18:57.977 Title 0 has 0 parts.
2008-09-28 12:18:58.326 DPMS Deactivated 
2008-09-28 12:18:58.376 AFD: Opened codec 0x8b93c70, id(MPEG2VIDEO) type(Video)
2008-09-28 12:18:58.376 NVP: Disabling Audio, params(-1,-1,-1)
2008-09-28 12:18:58.492 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2008-09-28 12:18:58.611 OSD Theme Dimensions W: 1280 H: 720
2008-09-28 12:18:59.367 TV: Changing from None to WatchingPreRecorded
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-09-28 12:18:59.462 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-09-28 12:18:59.466 Video timing method: USleep with busy wait
2008-09-28 12:18:59.943 AFD: Warning, video codec 0x8b93c70 id(MPEG2VIDEO) type (Video) already open.
2008-09-28 12:19:00.189 AFD: codec AC3 has 0 channels
2008-09-28 12:19:00.191 AFD: Opened codec 0x9192740, id(AC3) type(Audio)
2008-09-28 12:19:00.201 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-28 12:19:00.202 Opening ALSA audio device 'default'.
2008-09-28 12:19:00.228 NVP: Enabling Audio
2008-09-28 12:19:02.492 [mpeg2video @ 0xb7384b88]invalid mb type in P Frame at 44 35
2008-09-28 12:19:02.492 [mpeg2video @ 0xb7384b88]Warning MVs not available
2008-09-28 12:19:02.976 [mpeg2video @ 0xb7384b88]invalid mb type in P Frame at 44 35
2008-09-28 12:19:21.249 DPMS Reactivated.
```

The first dvd was recorded with DVDFab in Wine, and the second in either DVDRip of k9copy, I can't remember which.

Anyone know why these different errors would appear?  The first dvd stutters badly for about 10 seconds every 10 minutes or so.

It's been suggested to increase the size of the audio buffer but I don't know how to do that....

---

