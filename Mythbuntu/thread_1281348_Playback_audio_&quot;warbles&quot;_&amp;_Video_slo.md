---
title: "Playback audio &quot;warbles&quot; &amp; Video slows a bit...."
date: 2009-10-03
forum: Mythbuntu
---

### Post by sawbuck on 2009-10-03
I've been burning up the posts here on anything related to audio and visual problems, trying every suggestion I can and have gotten to an "almost satisfied" state.  Recently, with some helpful posters describing logs and how to access them I've looked at many of my frontend and other logs in an attempt to understand what is going on.   >>>>  I have learned a bit in the past several weeks but don't understand TOO MUCH  <<<<

To start with here's my system:

Motherboard: ASUS P4B533
CPU: Intel 2.4 Ghz
RAM: 2 Gb
Video Card: EVGA 6200 AGP 8x 512 Mb (NVIDIA GeForce chip)
Sound Card: integrated onboard C-Media Electronics Inc CM8738 (rev 10)
HD: Maxtor 250Gb
Remote: none
Tuners: Haupauge HVR 1600 (using ATSC)
Country: US
TV provider: US Broadcast
TV signal type: Digital (HD & DTV)
Mythbuntu Version: 9.04

My xorg.conf:  (pertaining to XvMC)

Section "Device"
    Identifier    "Configured Video Device"
    Option    "UseEvents"    "true"
    Option    "DPI"    "100x100"
    Driver    "nvidia"
    Option    "NoLogo"    "True"

        Option  "XvmcUsesTextures" "false"
        Option  "NVAGP" "1"
EndSection


Section "Extensions"
        Option "Composite" "Disabled"
EndSection

My playback profile is one I added to "CPU--": (none of preconfigured defaults anywhere worked):

Rez:  >        0,0
DeCoder:    Std XVMC
Vid Rnr:       XVMC-Opengl
OSD Rndr: Opengl 
OSD fade:  On (or off doesn't matter)
DeIntlace:   none
2nd Deint:   none
Filters:  blank

With all the combinations of playback I've tried, this works the best:  My Live TV plays HD with no issues after OSD disappears.  Iv I bring it back - say, to adjust volume - audio warbles/becomes statically until OSD disappears again.

All combinations with playback stutter and chop video/audio while OSD is on then improves to warble/static audio and slight video pauses.

Here is a snippet of my frontend log going into playback:

2009-10-02 22:14:09.057 TV: Attempting to change from None to WatchingPreRecorded
2009-10-02 22:14:09.410 DPMS Deactivated 
2009-10-02 22:14:09.536 AFD: Opened codec 0xad80d40, id(MPEG2VIDEO_XVMC) type(Video)
2009-10-02 22:14:09.536 AFD: codec AC3 has 6 channels
2009-10-02 22:14:09.537 AFD: Opened codec 0xb572030, id(AC3) type(Audio)
2009-10-02 22:14:09.537 AFD: codec AC3 has 2 channels
2009-10-02 22:14:09.538 AFD: Opened codec 0xb5723b0, id(AC3) type(Audio)
2009-10-02 22:14:09.548 AFD: Opened codec 0xb572730, id(MPEG2VIDEO_XVMC) type(Video)
2009-10-02 22:14:09.553 Opening audio device 'default'. ch 2(2) sr 48000
2009-10-02 22:14:09.553 Opening ALSA audio device 'default'.
2009-10-02 22:14:09.641 VideoOutputXv: Desired video renderer 'xvmc-opengl' not available.
            codec 'MPEG2 IDCT' makes 'xvmc-blit,' available, using 'xvmc-blit' instead.
2009-10-02 22:14:09.645 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-10-02 22:14:09.723 VideoOutputXv: Ack! Disabling ChromaKey OSD
            We can't use ChromaKey OSD if chromakeying is not supported!
2009-10-02 22:14:09.732 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-10-02 22:14:09.814 OSD Theme Dimensions W: 640 H: 480
2009-10-02 22:14:10.382 AFD: Opened codec 0xba14430, id(MPEG2VIDEO) type(Video)
2009-10-02 22:14:10.382 AFD: codec AC3 has 6 channels
2009-10-02 22:14:10.383 AFD: Opened codec 0xba14a70, id(AC3) type(Audio)
2009-10-02 22:14:10.383 AFD: codec AC3 has 2 channels
2009-10-02 22:14:10.384 AFD: Opened codec 0xba150b0, id(AC3) type(Audio)
2009-10-02 22:14:10.388 AFD: Opened codec 0xba156f0, id(MPEG1VIDEO) type(Video)
2009-10-02 22:14:10.486 TV: Changing from None to WatchingPreRecorded
2009-10-02 22:14:10.498 Failed to approve 'none' deinterlacer
2009-10-02 22:14:10.498 Couldn't load deinterlace filter 
2009-10-02 22:14:10.512 The realtime priority setting is not enabled.
2009-10-02 22:14:10.600 OpenGLVideoSync()
2009-10-02 22:14:10.677 Video timing method: SGI OpenGL
2009-10-02 22:14:10.723 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.723 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:10.730 VideoOutputXv Error: Child     A        was already marked as available.
2009-10-02 22:14:10.730 VideoOutputXv Error: Child     A        was already marked as available.
2009-10-02 22:14:10.763 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.763 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:10.803 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.803 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:10.843 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.843 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:10.843 VideoOutputXv Error: Child     A        was already marked as available.
2009-10-02 22:14:10.882 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.883 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:10.890 VideoOutputXv Error: Child     A        was already marked as available.
2009-10-02 22:14:10.936 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.936 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:10.975 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:10.976 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:11.029 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2009-10-02 22:14:11.029 VideoOutputXv: ProcessFrameXvMC: Called without frame
2009-10-02 22:14:11.262 WriteAudio: buffer underrun
2009-10-02 22:14:11.363 WriteAudio: buffer underrun
2009-10-02 22:14:11.417 WriteAudio: buffer underrun
2009-10-02 22:14:11.468 WriteAudio: buffer underrun
2009-10-02 22:14:11.551 WriteAudio: buffer underrun
2009-10-02 22:14:11.609 WriteAudio: buffer underrun
2009-10-02 22:14:11.685 WriteAudio: buffer underrun
2009-10-02 22:14:11.760 WriteAudio: buffer underrun
2009-10-02 22:14:11.811 WriteAudio: buffer underrun

I don't really understand much of it and have been plowing through wiki and other.  However, I'm a bit confused by some of the entries in the log pertaining to XvMC and ChromaKey in the following:

2009-10-02 22:14:09.641 VideoOutputXv: Desired video renderer 'xvmc-opengl' not available.
            codec 'MPEG2 IDCT' makes 'xvmc-blit,' available, using 'xvmc-blit' instead.
2009-10-02 22:14:09.645 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2009-10-02 22:14:09.723 VideoOutputXv: Ack! Disabling ChromaKey OSD
            We can't use ChromaKey OSD if chromakeying is not supported!
2009-10-02 22:14:09.732 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'

My EVGA GeForce 6200 seems to say it has OpenGL features so how can I activaate and use "xvmc-opengl"??  

Also, where is Chromakey activated?  How do I find out if it is supported?

Any help is appreciated.

---

### Post by DC^ on 2009-10-03
Try to update your system with:

```
sudo apt-get update
```

Or go to System --> Administration --> Update manager.

---

### Post by sawbuck on 2009-10-03
> **DC^ said:**
> Try to update your system with:

```
sudo apt-get update
```Or go to System --> Administration --> Update manager.

DC^, appreciate the suggestion but I do that routinely and get all updates to keep current.  A check showed system "Up to date".

---

