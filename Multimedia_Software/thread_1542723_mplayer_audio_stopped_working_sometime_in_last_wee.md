---
title: "mplayer audio stopped working sometime in last week"
date: 2010-07-31
forum: Multimedia Software
---

### Post by BaffledMollusc on 2010-07-31
Hi,

I'm using Ubuntu 10.04 64-bit version.

I've recently lost audio playback using mplayer. It was working maybe a week ago, but when I tried it again last night, no joy. The video is fine, but complete silence on the audio front.

This happens regardless of the codec or container format used by the multimedia file. Other players, e.g. VLC, Movie Player etc work fine, both video and audio.

If I go to System->Preferences->Sound and look at the Applications tab, then fire up any video or audio player *except* mplayer, that application appears in the list. When I'm using mplayer I just get "No application is currently playing or recording audio." I suspect this is the smoking gun, but I don't know what it means.

The device I'm using (hopefully) is a Sound Blaster Audigy 2 ZS. There are other possible sound chips in the system though, like the HDMI one on the graphics card.

I'm using the mplayer version from the PPA ppa.launchpad.net/rvm/mplayer/ubuntu which is described in Synaptic as 2:1.0~rc3+svn20100416-0lucid3.

Using mplayer from the command line gives, for example

```
mplayer 03\ -\ The\ Gothowitz\ Deviation.mkv 

MPlayer SVN-r31042-Ubuntu-RVM (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 03 - The Gothowitz Deviation.mkv.
[mkv] Track ID 1: audio (A_AC3), -aid 0, -alang und
[mkv] Track ID 2: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Will play video track 2.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
A:   4.9 V:   4.9 A-V:  0.000 ct:  0.000   0/  0 28%  0%  0.9% 0 0 
Exiting... (Quit)
```

The output of some other possibly useful diagnostics are

```
uname -a
Linux molluschome 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

If anyone needs more info, please don't hesitate to ask. Any suggestions or advice gratefully accepted!

---

### Post by andrew.46 on 2010-07-31
Hi,

Seems a little odd as the mplayer terminal output seems perfectly normal. Have you tried with a different audio out device? Perhaps either one of these:

```
mplayer -ao pulse 03\ -\ The\ Gothowitz\ Deviation.mkv
mplayer -ao alsa 03\ -\ The\ Gothowitz\ Deviation.mkv
```

Andrew

---

### Post by BaffledMollusc on 2010-07-31
Thank you!

Those both work. Weird - I've no idea which audio driver it was using before, though, or why it was working then stopped.

Anyway, writing ao=pulse into mplayer's config file seems to have fixed everything even when I start it from the menu rather than the command line, so I'm all set.

Thanks for your help!

---

### Post by andrew.46 on 2010-07-31
Hi Baffled,

> **BaffledMollusc said:**
> Thanks for your help!

No problems, I am glad the problem was so easily solved :).

Andrew

---

