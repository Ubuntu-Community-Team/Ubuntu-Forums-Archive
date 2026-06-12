---
title: "Not working 5.1, audigy 2 ZS, Hardy"
date: 2008-12-07
forum: Multimedia Software
---

### Post by CrustyDOD on 2008-12-07
Hello!

I really need help you guys. Since the time i installed hardy i don't have 5.1 sound and now i have enough of it :)

First off, I changed in daemon file for pulseaudio to 6 channels.

```
speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.15

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 16 to 16384
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left <---- WORKING
 4 - Center
 1 - Front Right <---- WORKING
 3 - Rear Right
 2 - Rear Left <---- WORKING
 5 - LFE
Time per period = 8.365417
```

Only 3 speakers are working!

Yes, i've unmuted everything i could try in volume control. Nothing helps.

Logs show this:
```
pulseaudio[5987]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
```
That's the only thing in logs about sound!

Under "Sound Preferences", i've got everything autodetect.
Default Mixer Tracks: Audigy 2 ZS (alsa mixer)

I've read lots of threads about sound and audio and they are all getting me confused! That or the solution doesn't work.

Now i'm at the dead end.. What to do? Anyone can help?

---

### Post by CrustyDOD on 2009-01-20
Nobody?
It's still not working..

---

