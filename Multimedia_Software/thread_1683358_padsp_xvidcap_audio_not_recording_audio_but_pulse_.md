---
title: "padsp xvidcap audio not recording audio but pulse meter shows activity"
date: 2011-02-07
forum: Multimedia Software
---

### Post by sblandford on 2011-02-07
I can see the audio stream show up on the Pulse volume control and I can see the VE meter on the Pulse applet in full swing. However when I play back the recording that XVIDCap makes there is no sound, just an empty MP3 stream in the AVI container.

The only error message I see at the console is,
"xtoffmpeg.c add_audio_stream(): Can't initialize fifo for audio recording"

Has anyone got XVidCap to work on Maverick? Xvidcap version is 1.1.7-0.2ubuntu10.

This is the last output if I run padsp in debug mode and xvidcap in verbose mode.


> padsp -d xvidcap
utils/padsp.c: stat(/dev/dsp)
[mpeg4 @ 0x120cdd0]removing common factors from framerate
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=10
utils/padsp.c: SNDCTL_DSP_GETFMTS
utils/padsp.c: SNDCTL_DSP_SETFMT: 16
utils/padsp.c: SNDCTL_DSP_STEREO: 1
utils/padsp.c: SNDCTL_DSP_SPEED: 44100
utils/padsp.c: ss: s16le 2ch 44100Hz
utils/padsp.c: sample spec: s16le 2ch 44100Hz
utils/padsp.c: fixated metrics to 12 fragments, 7350 bytes each.
utils/padsp.c: stream established.
utils/padsp.c: SNDCTL_DSP_GETISPACE
utils/padsp.c: sample spec: s16le 2ch 44100Hz
utils/padsp.c: fixated metrics to 12 fragments, 7348 bytes each.
utils/padsp.c: fragsize=7348, fragstotal=12, bytes=7104, fragments=0
[oss @ 0x1279640]Estimating duration from bitrate, this may be inaccurate
xtoffmpeg.c add_audio_stream(): Can't initialize fifo for audio recording
missing -4 milli secs (100 needed per frame), pic no 0

---

### Post by Makosz on 2011-04-28
For me (ubuntu 10.04 32 bit) this worked [HTML]http://dannyman.toldme.com/2009/09/28/howto-ubuntu-xvidcap-audio-support/[/HTML]  with 2011solution stepa when u scroll down

---

