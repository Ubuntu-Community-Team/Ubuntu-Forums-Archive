---
title: "Audigy1 and no sound through spdif--&gt;nvidia hdmi"
date: 2009-12-14
forum: Multimedia Software
---

### Post by dewon on 2009-12-14
So my setup is audigy1 soud card connected with 2-pin spidf-connector to nvidia 8600gt with hdmi which I was hoping would output both the audio and video to my receiver (Sony dg-910).

I've been battling with sound output for a few nights now without any success. I tried in 9.10 kubuntu and ubuntu, but after learning that spdif-output is somewhat broken on 9.10, I switched to 9.04. Still, nothing.

aplay -l -L gives this
risto@risto-desktop:~$ aplay -l -L
front:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Audigy,DEV=0
    SB Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
**** Luettelo PLAYBACK laitteista ****
kortti 0: Audigy [SB Audigy 1 [SB0090]], laite 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Alalaitteet: 32/32
  Alalaite #0: subdevice #0
  Alalaite #1: subdevice #1
  Alalaite #2: subdevice #2
  Alalaite #3: subdevice #3
  Alalaite #4: subdevice #4
  Alalaite #5: subdevice #5
  Alalaite #6: subdevice #6
  Alalaite #7: subdevice #7
  Alalaite #8: subdevice #8
  Alalaite #9: subdevice #9
  Alalaite #10: subdevice #10
  Alalaite #11: subdevice #11
  Alalaite #12: subdevice #12
  Alalaite #13: subdevice #13
  Alalaite #14: subdevice #14
  Alalaite #15: subdevice #15
  Alalaite #16: subdevice #16
  Alalaite #17: subdevice #17
  Alalaite #18: subdevice #18
  Alalaite #19: subdevice #19
  Alalaite #20: subdevice #20
  Alalaite #21: subdevice #21
  Alalaite #22: subdevice #22
  Alalaite #23: subdevice #23
  Alalaite #24: subdevice #24
  Alalaite #25: subdevice #25
  Alalaite #26: subdevice #26
  Alalaite #27: subdevice #27
  Alalaite #28: subdevice #28
  Alalaite #29: subdevice #29
  Alalaite #30: subdevice #30
  Alalaite #31: subdevice #31
kortti 0: Audigy [SB Audigy 1 [SB0090]], laite 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Alalaitteet: 8/8
  Alalaite #0: subdevice #0
  Alalaite #1: subdevice #1
  Alalaite #2: subdevice #2
  Alalaite #3: subdevice #3
  Alalaite #4: subdevice #4
  Alalaite #5: subdevice #5
  Alalaite #6: subdevice #6
  Alalaite #7: subdevice #7
kortti 0: Audigy [SB Audigy 1 [SB0090]], laite 3: emu10k1 [Multichannel Playback]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0

I also installed the newewst alsa and switched on the following in alsamixer:
master and pcm 100%
iec958 on and 100%
digital/analog switch on (also tried off)
remote amplifier on (also tried off) 

Please someone help me :(

---

### Post by dewon on 2009-12-14
Here's when i try to play through spdif on mplayer. Everything seems okay, but nothing on receiver.

risto@risto-desktop:~$ mplayer -ao alsa:device=spdif -ac hwac3 dvd://
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 24 titles on this DVD.
There are 13 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: fi aid: 128.
audio stream: 1 format: ac3 (5.1) language: fi aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: fi
subtitle ( sid ): 1 language: da
subtitle ( sid ): 2 language: sv
subtitle ( sid ): 3 language: no
number of subtitles on disk: 4
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8888.0 kbps (1111.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12

---

