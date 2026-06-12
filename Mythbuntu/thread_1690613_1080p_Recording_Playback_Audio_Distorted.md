---
title: "1080p Recording Playback Audio Distorted"
date: 2011-02-18
forum: Mythbuntu
---

### Post by Dragonflyoh on 2011-02-18
The audio on my 1080p recordings is distorted. Video is fine, and audio and video on 720 recordings is fine. I have an intel i3 processor with 4 GB DDR3 memory. I am using the built in audio on an Intel DH55TC motherboard. I am using Myhthbuntu 10.10. I have tried all sorts of changes to the audio setup and am using SPDIF Stereo. The recordings have dolby surround sound. Any ideas would be appreciated.

---

### Post by nickrout on 2011-02-19
> **Dragonflyoh said:**
> The audio on my 1080p recordings is distorted. Video is fine, and audio and video on 720 recordings is fine. I have an intel i3 processor with 4 GB DDR3 memory. I am using the built in audio on an Intel DH55TC motherboard. I am using Myhthbuntu 10.10. I have tried all sorts of changes to the audio setup and am using SPDIF Stereo. The recordings have dolby surround sound. Any ideas would be appreciated.

for one thing i don't know of any boradcasters using 1080p anywhere in the world, so I suspect it is 1080i.

Secondly do you have logs? perhaps with -v audio on your commandline for the mythfrontend.

Also mediainfo will tell you exactly what codecs are being used in your recording.

---

### Post by Dragonflyoh on 2011-02-21
Thanks!

My mistake on the 1080. Mythtv indicates its 1080.

I have run into a motherboard problem and am waiting for a replacement. As soon as its installed I will check the log file as you suggested and post the results.

---

### Post by floh-511 on 2011-02-22
Downmixing to stereo can be a problem by itself in my experience (not with Ubuntu but Windows).
Does it go away when you output 5.1 AC3 as passthrough?

---

### Post by Dragonflyoh on 2011-02-24
I have tried changing the output to every choice and the only changes are either no audio or the distorted sound.

I looked for logs and from what I read there should be a frontend log in var/log/mythtv. I do not have a mythtv folder or a frontend.log file anywhere. I looked at the syslog and found:
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 64.
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.

The syslog also has these lines about pulse audio:
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: snd_pcm_dump():
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: Soft volume PCM
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: Control: PCM Playback Volume
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: min_dB: -51
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: max_dB: 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: resolution: 256
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: Its setup is:
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   stream       : CAPTURE
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   format       : S16_LE
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   subformat    : STD
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   channels     : 2
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   rate         : 44100
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   msbits       : 16
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   buffer_size  : 88192
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_size  : 44096
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_time  : 999909
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_step  : 1
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   avail_min    : 87310
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_event : 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   start_threshold  : -1
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   stop_threshold   : 1444937728
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   silence_threshold: 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   silence_size : 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   boundary     : 1444937728
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c: Its setup is:
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   stream       : CAPTURE
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   format       : S16_LE
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   subformat    : STD
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   channels     : 2
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   rate         : 44100
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   msbits       : 16
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   buffer_size  : 88192
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_size  : 44096
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_time  : 999909
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_step  : 1
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   avail_min    : 87310
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   period_event : 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   start_threshold  : -1
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   stop_threshold   : 1444937728
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   silence_threshold: 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   silence_size : 0
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   boundary     : 1444937728
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   appl_ptr     : 87384
Feb 24 14:48:55 Mythtv pulseaudio[1539]: alsa-util.c:   hw_ptr       : 87384

I found a test for sound that was:
aplay -vv /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

I did that and got:

Playing raw data '/usr/share/sounds/ubuntu/stereo/desktop-login.ogg' : Unsigned 8 bit, Rate 8000 Hz, Mono
ALSA <-> PulseAudio PCM I/O Plugin
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 8
  buffer_size  : 4000
  period_size  : 1000
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1000
  period_event : 0
  start_threshold  : 4000
  stop_threshold   : 4000
  silence_threshold: 0
  silence_size : 0
  boundary     : 2097152000
##################################################+| MAX

The sound file did not play, but the speakers did put out a stream of steady noise. Any other ideas would be appreciated.

---

### Post by Dragonflyoh on 2011-02-26
After trying all sorts of changes I changed the video player from Internal to gxine and everything works very well. I tried vlc and that did not solve the problem. I am now going to get my remote working.

---

### Post by Dragonflyoh on 2011-02-27
Went back to trying the Internal Player and after reading the information here:
[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)
I changed my profile from High Quality to  Normal and everything is working great.

---

