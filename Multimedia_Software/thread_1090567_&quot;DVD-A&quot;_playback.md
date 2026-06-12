---
title: "&quot;DVD-A&quot; playback"
date: 2009-03-08
forum: Multimedia Software
---

### Post by lotharamious on 2009-03-08
Hey all, does anyone know how to play DVD-Audio disks in linux?

Just to make sure we're all on the same page as to what DVD-A is... it's a DVD disk with **files in the audio_ts folder**.  Please don't give answers for how to play a DVD video.

Ok.  So I can play DVD-A disks in Windows with powerdvd just fine.  Does anyone know how to do this in Ubuntu?

Initial attempts with mplayer fail with things like...

```
$ mplayer ats_01_1.aob

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team           
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)                                                                         
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                      
Compiled with runtime CPU detection.                                             
mplayer: could not connect to socket                                             
mplayer: No such file or directory                                               
Failed to open LIRC support. You will not be able to use your remote control.    

Playing ats_01_1.aob.

Too many audio packets in the buffer: (4096 in 8224747 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.   
MPEG: Missing video stream!? Contact the author, it may be a bug :(     

Too many audio packets in the buffer: (4096 in 8224768 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.   
MPEG: Missing video stream!? Contact the author, it may be a bug :(     
libavformat file format detected.                                       
[lavf] Audio stream found, -aid 0                                       
==========================================================================
Forced audio codec: mad                                                   
Opening audio decoder: [pcm] Uncompressed PCM audio decoder               
AUDIO: 32000 Hz, 4 ch, s16be, 256.0 kbit/12.50% (ratio: 32000->256000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_hw.c:1321:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] Playback open error: Device or resource busy
mcop warning: user defined signal handler found for SIG_PIPE, overriding
[AO ARTS] Connected to sound server.
[AO ARTS] Stream opened.
[AO ARTS] buffer size: 20480
[AO ARTS] buffer size: 2048
AO: [arts] 32000Hz 4ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  -0.0 (unknown) of 1664.1 (27:44.1) ??,?%

```

If it's any consolation this particular disk is a 4.0 channel 24-bit/96kHz recording.  (Possibly 24-bit/192kHz)

Any help would be sweet, as 4 hours of Googling has gotten me nowhere.

Thanks.

---

### Post by alquery on 2011-08-10
I know that I'm **extremely** late, sorry.

But if you were like me and googling for something to do this on Linux and couldn't find it, VLC now plays DVD-A's if you insert a disc and manually go to Media -> Play Disc -> select DVD.
For some reason, Ubuntu doesn't play right with them and balks when you insert a DVD-A.

---

