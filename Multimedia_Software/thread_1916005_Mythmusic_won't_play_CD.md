---
title: "Mythmusic won't play CD"
date: 2012-01-27
forum: Multimedia Software
---

### Post by rafe101 on 2012-01-27
I had trouble with underrun buffers earlier which made the CDs stutter. I never did figure that out. I have since upgraded Mythbuntu to 11.10. MP3s play but not CDs. The track names load into the player, but no time info. So, I get neither playtime ticking down or sound.

Here are some excerpts from my frontend log. It looks like the buffer error is still there, but I'm not that far yet. So that doesn't bother me.

```
2012-01-27 13:12:56.103 CD status has changed.
2012-01-27 13:12:56.123 Track, Error: putYourselfOnTheListView() called when my_widget already exists.
2012-01-27 13:12:56.123 Track, Error: putYourselfOnTheListView() called when my_widget already exists.
2012-01-27 13:12:56.123 Track, Error: putYourselfOnTheListView() called when my_widget already exists.
2012-01-27 13:12:56.123 Track, Error: putYourselfOnTheListView() called when my_widget already exists
...
...[literally hundreds of these]
...
...
...
2012-01-27 13:14:22.594 The cddecoder said it had audio tracks, but it won't tell me about them
2012-01-27 13:14:22.738 CD status has changed.
2012-01-27 13:14:23.932 Pulse: PulseAudio resume OK
2012-01-27 13:14:24.032 Pulse: PulseAudio suspend OK
2012-01-27 13:14:24.046 AO: Resampling from 44 kHz to 48 kHz with quality medium
2012-01-27 13:14:24.046 AO: Opening audio device 'surround51:CARD=CMI8768,DEV=0' ch 6(2) sr 48000 sf signed 16 bit reenc 0
2012-01-27 13:14:24.047 ALSA, Error: Setting hardware audio buffer size to 128
2012-01-27 13:14:24.047 ALSA, Error: Error opening /proc/asound/card0/pcm1p/sub0/prealloc: Permission denied. 
2012-01-27 13:14:24.047 ALSA, Error: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm1p/sub0/prealloc
2012-01-27 13:14:24.047 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
[mp3 @ 0x9f686d20] max_analyze_duration reached
[mp3 @ 0x9f686d20] Estimating duration from bitrate, this may be inaccurate
[mp3 @ 0x9bcc6a10] max_analyze_duration reached
[mp3 @ 0x9c061100] Header missing
2012-01-27 13:18:33.307 Read frame failed
```

---

