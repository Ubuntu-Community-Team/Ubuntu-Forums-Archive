---
title: "Crackly audio in ZSNES on Mythbuntu 8.04 with SPDIF out"
date: 2008-05-09
forum: Mythbuntu
---

### Post by aseriesoftubes on 2008-05-09
I have configured my .asoundrc to send all audio over SPDIF like so:
```

pcm.!default {
   type plug
   slave {
     rate 48000
     pcm "spdif"
   }
}

```
I have installed the libsdl1.2debian-all package as suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=733387"). When launching ZSNES, I have tried all of the audio output options using the "-ad" option, but I only get sound using "-ad sdl". The sound, however, is very tinny and crackly. I have changed all the options within ZSNES (sampling rate, interpolation, disable SPC emulation, disable stereo sound, etc.) but nothing helps. 

I am using an older SB Live! card with a coax SPDIF output. Sound is perfect in MythTV and in VLC, Firefox, etc. Also, sound in ZSNES was fine in Mythbuntu 7.10, so I suspect this problem might have something to do with Pulse.

Anybody else having similar troubles?

---

