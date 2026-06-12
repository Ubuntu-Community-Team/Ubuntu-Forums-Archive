---
title: "Fresh install, sound quits within minutes, alsa under-run"
date: 2010-06-05
forum: Multimedia Software
---

### Post by HyperHacker on 2010-06-05
Just installed 10.04 x86 and sound is cutting off after no more than about 4 minutes.

Pulseaudio gives a nice detailed error message:> $ pulseaudio
E: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 4294955240 bytes (24347818 ms).
E: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_cmipci'. Please report this issue to the ALSA developers.
E: alsa-util.c: snd_pcm_dump():
E: alsa-util.c: Hardware PCM card 0 'C-Media CMI8738' device 0 subdevice 0
E: alsa-util.c: Its setup is:
E: alsa-util.c:   stream       : PLAYBACK
E: alsa-util.c:   access       : MMAP_INTERLEAVED
E: alsa-util.c:   format       : S16_LE
E: alsa-util.c:   subformat    : STD
E: alsa-util.c:   channels     : 2
E: alsa-util.c:   rate         : 44100
E: alsa-util.c:   exact rate   : 44100 (44100/1)
E: alsa-util.c:   msbits       : 16
E: alsa-util.c:   buffer_size  : 16384
E: alsa-util.c:   period_size  : 8192
E: alsa-util.c:   period_time  : 185759
E: alsa-util.c:   tstamp_mode  : ENABLE
E: alsa-util.c:   period_step  : 1
E: alsa-util.c:   avail_min    : 15503
E: alsa-util.c:   period_event : 0
E: alsa-util.c:   start_threshold  : -1
E: alsa-util.c:   stop_threshold   : 1073741824
E: alsa-util.c:   silence_threshold: 0
E: alsa-util.c:   silence_size : 0
E: alsa-util.c:   boundary     : 1073741824
E: alsa-util.c:   appl_ptr     : 707532
E: alsa-util.c:   hw_ptr       : 688134
E: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: 447852 bytes (2538 ms).
E: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_cmipci'. Please report this issue to the ALSA developers.
E: alsa-util.c: snd_pcm_dump():
E: alsa-util.c: Hardware PCM card 0 'C-Media CMI8738' device 0 subdevice 0
E: alsa-util.c: Its setup is:
E: alsa-util.c:   stream       : PLAYBACK
E: alsa-util.c:   access       : MMAP_INTERLEAVED
E: alsa-util.c:   format       : S16_LE
E: alsa-util.c:   subformat    : STD
E: alsa-util.c:   channels     : 2
E: alsa-util.c:   rate         : 44100
E: alsa-util.c:   exact rate   : 44100 (44100/1)
E: alsa-util.c:   msbits       : 16
E: alsa-util.c:   buffer_size  : 16384
E: alsa-util.c:   period_size  : 8192
E: alsa-util.c:   period_time  : 185759
E: alsa-util.c:   tstamp_mode  : ENABLE
E: alsa-util.c:   period_step  : 1
E: alsa-util.c:   avail_min    : 15503
E: alsa-util.c:   period_event : 0
E: alsa-util.c:   start_threshold  : -1
E: alsa-util.c:   stop_threshold   : 1073741824
E: alsa-util.c:   silence_threshold: 0
E: alsa-util.c:   silence_size : 0
E: alsa-util.c:   boundary     : 1073741824
E: alsa-util.c:   appl_ptr     : 800132
E: alsa-util.c:   hw_ptr       : 688169
KilledALSA doesn't tell me a thing, but mpd just spontaneously pauses and has to be restarted.

SOX gives more detail:> $ play Super\ Mario\ Bros\ -\ Remix.mp3 

Super Mario Bros - Remix.mp3:

 File Size: 3.43M     Bit Rate: 134k
  Encoding: MPEG audio    
  Channels: 2 @ 16-bit   
Samplerate: 44100Hz      
Replaygain: off         
  Duration: 00:03:24.96  

In:88.7% 00:03:01.77 [00:00:23.19] Out:8.01M [======|======] Hd:0.0 Clip:129  play WARN alsa: under-run
play FAIL sox: `default' Input/output error: Operation not permitted
play WARN sox: `alsa' output clipped 129 samples; decrease volume?
Done.Surprise surprise, the same "alsa under-run" bug I've been seeing since 9.04.

Will I ever have working sound again?

---

### Post by lidex on 2010-06-05
Perhaps this attachment will help. I notice your pulse output shows mmap-interleaved, perhaps you can try rw-interleaved. Is this stereo output or 4-channel?

---

### Post by HyperHacker on 2010-06-05
How would I change that? I'm not using the rear output at all. I played with the switches and all I found was enabling Exchange DAC and disabling Four Channel Mode (normally the reverse) results in full volume at all times, even to the front speakers (while the document says only the rear).

Following [this](http://blog.netflowdevelopments.com/2009/05/10/fixing-alsa-underrun-erorrs-associated-with-pulseaudio-and-typically-skype-in-ubuntu), I tweaked the priority and managed to make it happen less often (~15 minutes in some cases), but that's all.

[This](https://bugzilla.redhat.com/show_bug.cgi?id=524385) seems like the same issue, and a nice workaround - which conveniently doesn't work in Ubuntu because there's no xrun_debug to write to. It describes a hardware bug (and even a [patch](http://archives.free.net.ph/message/20090326.041434.7885fc63.en.html)), which seems related until you consider that this card worked for years without a hiccup under Windows and Ubuntu 8.04 and 8.10 - unless the driver used to work around that bug, and suddenly doesn't anymore?

Another oddity I noticed are that it will crash without even playing anything - and much more often while playing - if pavucontrol is running. In fact it can lock up the entire system. This reminds me of an issue I had with pavucontrol before where it would randomly throw Pulse into a memory-eating loop.

Also strange is that since tweaking the priority, mplayer's audio export function seems to update considerably slower. I was using it in one program to plot a spectrum analyzer, and suddenly the plot is updating much slower, yet the sound is unaffected. Maybe an obscure mplayer bug? This didn't happen with mplayer using ALSA, yet it still crashed.

---

### Post by lidex on 2010-06-05
Have you tried removing pulseaudio and running straight through alsa? Or even OSS4?

---

### Post by HyperHacker on 2010-06-05
Doing that, it doesn't seem to be crashing (yet), but I still get the occasional underrun error accompanied with a skip or two, which is the same problem I had on 9.04/9.10/Debian, but less frequent. Tolerable so far (assuming it doesn't get worse as I've seen before), but does get to be annoying in movies when an important word gets skipped.

Would be nice to have Pulse working though. Really seems odd that it's complaining about an ALSA issue, but Pulse is the one that ends up crashing. I've actually had it report the snd_pcm_delay error and *not* crash a couple times (but the player still freezes). It doesn't seem to be an actual crash, either - it says killed, the same as if I'd hit Ctrl+C - but what kills it?

---

### Post by HyperHacker on 2010-06-06
Hm. Well mplayer only skips on occasion, but mpd is hardly usable. Works fine through OSS, except for only one app being able to use it at a time. :-/

---

### Post by lidex on 2010-06-06
If you're going to use OSS, you'll want to follow this documentation (if you haven't already):
[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")
Pulse needs to be purged or it will cause conflicts.

---

### Post by HyperHacker on 2010-06-06
I don't really want to use OSS (unless I can have more than one program using it at a time), just it's the only engine that works properly in mpd.

---

### Post by HyperHacker on 2010-06-09
...and then there's the times mplayer randomly crashes and plays EXTREMELY LOUD STATIC when I'm trying to quietly watch a movie at night. -.- Nothing appears to have shown up in any logs.

---

### Post by HyperHacker on 2010-06-12
Well, I think I've "fixed" this by switching to the onboard AC'97 sound. The problem does indeed seem to be in the CMI8738 driver. I don't hear any glitches anymore; if it goes another day or two without acting up, I'll try installing PulseAudio again and see how well it works.

I'd definitely like to try to fix the driver, but I have no experience writing drivers or dealing with sound hardware.

---

