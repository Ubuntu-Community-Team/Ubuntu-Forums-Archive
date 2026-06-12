---
title: "SPDIF working but only in stereo!!!"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by fugazi41 on 2007-06-17
There seems to be a lot of problem with SPDIF sound under ubuntu 7.04. I've try to figure out how to fix it but no luck! I need help!

I have a P5B motherboard with a on board sound card:

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
 lspci 
...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
...

```

```
 lsmod | grep snd
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  13 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

```

```
 more /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

```

I'm connected to a Onkyo 7.1 amplifier via optical fiber. 

My problem is that sound only works in stereo! IEC958 is unmuted in alsamixer. 

I have try with speaker-test -c[678] but only the Front Left/Right output sound. 
I have also tried with different device surround[567]1, iec958 or spdif but I get 

surround[567]1 return no error but I get no sound from any speaker. 

But with the other two I get error. 

```
speaker-test -c6 -Dspdif

speaker-test 1.0.13

Playback device is spdif
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```

```
speaker-test -c6 -Diec958

speaker-test 1.0.13

Playback device is iec958
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument

```

I have no .asoundrc (since I have read that it was not necessary with alsa driver 1.0.14)

With vlc, when I set sound to a/52 over SPDIF,  I get: 
```
bp8839@marillion:~/Movies$ vlc movie.avi 
VLC media player 0.8.6 Janus
[00000335] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
No accelerated IMDCT transform found
[00000336] alsa audio output error: write failed (Broken pipe)
[00000336] alsa audio output error: write failed (Broken pipe)

```

Does this chipset sound really supported? Anyone can help or point me in the right direction?

thanks for your time reading me,

Regards,
fugazi41

---

### Post by xzero1 on 2007-06-23
Try mplayer with a 5.1 dvd and use the command line:
mplayer dvd://1 -afm hwac3. This tells mplayer to use to use ac3/dts passthrough which will test your setup. I can't get vlc to work with passthrough either.

---

### Post by fugazi41 on 2007-06-25
I have try with mplayer but it switch to stereo as well!!! My Onkyo only receive stereo via optical spdif! The DVD is Ice Age in AC3 english sound track. On my dvd player with the same receiver, everything work fine!

I have switch to fedora 7 and still get the same problem. On the alsa website. They are talking about ICH6/7 for the HDA intel. They never mention ICH8! Is it really supported yet?

Thanks for your reply.


```
[bp8839@marillion ~]$ mplayer dvd://1 -afm hwac3 -dvd-device /dev/dvd-sr1 -alang en
MPlayer SVN-r23545 rpm.livna.org (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 12 titles on this DVD.
There are 21 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: ac3 (stereo) language: es aid: 130.
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
number of audio channels on disk: 4.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: es
subtitle ( sid ): 2 language: fr
subtitle ( sid ): 3 language: es
number of subtitles on disk: 4
Selected DVD audio channel: 128 language: en
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
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
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:   0.7 V:   0.7 A-V:  0.035 ct:  0.043  17/ 14  4%  2%  0.4% 0 0              
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

```

---

### Post by xzero1 on 2007-06-28
You are doing everything correctly so it does appear that the current driver for your chipset does not support spdif passthrough. I would email the chipset manufacturer to be sure. Too bad our legal system doesn't understand monopolysoft.

---

### Post by lank23 on 2007-07-04
I too have a P5b mother board, but my spdif "optical" port works correct.  

I use gxine 0.5.11 and set the audio output to pass through and I get perfect sound.  Other players VLC, MPlayer.. don't work for me.  But with MPlayer I did get the same stereo effect.

lank23

---

### Post by paradoxni on 2007-07-05
i seem to be having this issue as well, everything is set to passthrough and my stereo mp3's etc play fine on my amp/speakers, but if i play a 5.1 DVD I get no sound passed to the amp via the spdif.

---

### Post by SBFC on 2007-07-06
My speakers were working fine with an optical hookup. Only problem I had, and it was minor, was that I couldn't control my volume with the master volume. I had to use the actual receiver knob.

I normally used alsamixergui to mess with stuff, but just for the heck of it I opened up the XFCE Mixer. I kid you not, I merely _opened_ it, and BAM! My sound no longer works. I've been tinkering with it for the last hour and can't figure out what happened. Even shut down my system and powered back up in hopes that would fix it...but no.

Sad.

---

### Post by SBFC on 2007-07-09
Finally figured out what happened. Previous to my post I hadn't ever used the XFCE Mixer. When I opened it, it apparently hijacked the settings for my soundcard, and it set it to 2ch instead of 6ch. Even changing it to 6ch in alsamixer wouldn't hold. 

I also couldn't get it to stick in XFCE mixer until I was messing around and discovered I could save a profile. So, I set it to 6ch and named a profile and saved it. I then proceeded to wet myself as my speakers finally started pouring music at full volume (had it turned all the way up since it was set to 2ch it was very faint). :P

---

### Post by lank23 on 2007-07-10
How are you guys sure that you are getting or not getting 5.1 "6 chanel" sound. 

I know for sure that what I am getting due that my Sony receiver displays the input type IE "PCM 48Mhz = stereo"  or 5.1 Dolby Digital" or "5.1 DTS" and so on.

Also when I send 5.1 DD / DTS to the receiver a blue light on the front of it comes on, and I just smile...

lank23

---

### Post by Trollslayer on 2008-06-07
In SPDIF there is a control channel with various flags and configuration data.
I suspect ALSA isn't setting these correctly.

---

