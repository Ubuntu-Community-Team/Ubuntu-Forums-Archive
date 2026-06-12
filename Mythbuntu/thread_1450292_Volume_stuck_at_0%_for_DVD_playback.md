---
title: "Volume stuck at 0% for DVD playback"
date: 2010-04-08
forum: Mythbuntu
---

### Post by bb_145 on 2010-04-08
Hi,

I recently upgraded to 10.04.  Now when I playback some DVDs, the volume ends up stuck at 0%, so there is no sound.  It appears to be limited to DVDs that contain both AC3 and MP2 audio tracks.  The same DVDs worked in 8.10.  I can occasionally get the audio to return by switching between the audio tracks.

Mythfrontend.log:

```
2010-04-08 20:00:17.264 Opened DVD device at /dev/sr1
2010-04-08 20:00:17.265 There are 1 titles on the disk
2010-04-08 20:00:17.265 Title 0 has 0 parts.
2010-04-08 20:00:17.406 AFD: Opened codec 0xad0af00, id(MPEG2VIDEO) type(Video)
2010-04-08 20:00:17.407 NVP(6): Disabling Audio, params(-1,-1,-1)
2010-04-08 20:00:17.429 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2010-04-08 20:00:17.492 OSD Theme Dimensions W: 640 H: 480
2010-04-08 20:00:17.624 TV: Changing from None to WatchingDVD
2010-04-08 20:00:17.628 AFD Error: Bad stream (NULL)
2010-04-08 20:00:17.764 AFD: Warning, video codec 0xad0af00 id(MPEG2VIDEO) type (Video) already open.
2010-04-08 20:00:17.810 AFD: codec AC3 has 0 channels
2010-04-08 20:00:17.813 AFD: Opened codec 0xb6cfbf0, id(AC3) type(Audio)
2010-04-08 20:00:17.823 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-04-08 20:00:17.824 Opening ALSA audio device 'default'.
2010-04-08 20:00:17.827 NVP(6): Enabling Audio
2010-04-08 20:00:17.877 AFD: Warning, audio codec 0xb6cfbf0 id(AC3) type (Audio) already open, leaving it alone.
2010-04-08 20:00:17.877 AFD: codec AC3 has 2 channels
2010-04-08 20:00:20.075 NVP(6): Timed out waiting for free video buffers.
2010-04-08 20:00:20.634 Video timing method: USleep with busy wait
2010-04-08 20:00:20.688 WriteAudio: buffer underrun
2010-04-08 20:00:22.048 WriteAudio: buffer underrun
2010-04-08 20:00:26.477 AFD: Warning, video codec 0xad0af00 id(MPEG2VIDEO) type (Video) already open.
2010-04-08 20:00:26.613 AFD: Opened codec 0xbe3b020, id(DVD_SUBTITLE) type(Subtitle)
2010-04-08 20:00:26.615 NVP(6): Disabling Audio, params(-1,-1,-1)


2010-04-08 20:00:26.680 AFD: Warning, video codec 0xad0af00 id(MPEG2VIDEO) type (Video) already open.
2010-04-08 20:00:26.682 AFD: codec AC3 has 0 channels
2010-04-08 20:00:26.683 AFD: Opened codec 0xbe29e70, id(AC3) type(Audio)
2010-04-08 20:00:26.713 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-04-08 20:00:26.714 Opening ALSA audio device 'default'.
2010-04-08 20:00:26.725 NVP(6): Enabling Audio
2010-04-08 20:00:27.088 WriteAudio: buffer underrun
2010-04-08 20:00:27.582 WriteAudio: buffer underrun
2010-04-08 20:00:27.994 WriteAudio: buffer underrun
2010-04-08 20:01:36.417 AFD: Warning, video codec 0xad0af00 id(MPEG2VIDEO) type (Video) already open.
2010-04-08 20:01:36.480 NVP(6): Disabling Audio, params(-1,-1,-1)
2010-04-08 20:01:36.493 AFD: Warning, video codec 0xad0af00 id(MPEG2VIDEO) type (Video) already open.
2010-04-08 20:01:36.493 AFD: codec MP2 has 0 channels

**2010-04-08 20:01:36.493 AFD: Opened codec 0xbc6b510, id(MP2) type(Audio)**
2010-04-08 20:01:36.493 AFD: Setting channels to 2
2010-04-08 20:01:36.494 [mp2 @ 0x60c780]Header missing
2010-04-08 20:01:36.494 NVP(6): Disabling Audio, params(16,2,0)
2010-04-08 20:01:36.494 AFD: Warning, audio codec 0xbc6b510 id(MP2) type (Audio) already open, leaving it alone.
2010-04-08 20:01:36.494 AFD: codec MP2 has 2 channels
2010-04-08 20:01:36.639 [mpeg2video @ 0x60c780]warning: first frame is no keyframe
2010-04-08 20:01:36.644 [mpeg2video @ 0x60c780]warning: first frame is no keyframe
2010-04-08 20:01:36.649 [mpeg2video @ 0x60c780]00 motion_type at 39 12
2010-04-08 20:01:36.649 [mpeg2video @ 0x60c780]Warning MVs not available
2010-04-08 20:01:37.325 GetNextFreeFrame() served a busy frame c. Dropping. UUUUUUULUUUUUUUUUUUUUUUUUUUUUUU
2010-04-08 20:06:47.718 TV: Attempting to change from WatchingDVD to None
2010-04-08 20:06:47.718 TV: Changing from WatchingDVD to None

```

It appears to be getting ready to play the audio in the line that is in bold.  As a possible clue, in cases where the audio works, the log reports "NVP(6): Enabling Audio" 

Any suggestions would be appreciated.  Thanks.

---

