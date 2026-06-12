---
title: "Audio Drivers"
date: 2009-10-16
forum: Multimedia Software
---

### Post by C_Bomb on 2009-10-16
**Hi Guys,**

Where can I download audio drivers or something to improve sound.

Cause I sometimes get popping sounds.

And my sound pops the whole time when i play a sound in Hydrogen.

I can hear the sound, but with a pop.

any ideas what to do?

---

### Post by VertexPusher on 2009-10-16
The popping sounds are audio buffer underruns (aka. XRUNs). This means your computer is writing audio buffer contents slower than the sound card is reading them. To get rid of the pops, you should do the following:

1. Make sure that Jack is running in realtime mode.
2. Make sure that Jack is connected to the hardware ("hw") ALSA device, not the default one.
3. Make sure that PulseAudio is not running.

If you still hear pops, proceed as follows:

4. Operate the soundcard in 44.1kHz or 48kHz mode, not 96kHz or higher.
5. Increase the audio buffer size.
6. Some soundcards require increasing the period number from 2 to 3 as well.

---

