---
title: "Interesting issue with headphones"
date: 2013-02-07
forum: Multimedia Software
---

### Post by xondak on 2013-02-07
Here's an interesting one for the community...

I've got an HP dv6-6140us laptop with 'BeatsAudio.' This thing has been *nothing but a headache* with audio configuration since I bought it, however I've got all but *one* minor annoyance solved.

When I plug my headphones into the audio-out port I get no audio through the headphones. I noticed while in alsamixer that, when I plug the headphones in, the "Master" volume changes, while the "Speaker" (not to be confused with "Speaker 1") is muted and the volume is lowered to 0. If I unmute "Speaker" and turn the volume up I get sound through the headphones.

If I'm in pavucontrol, the 'Port' is changed from "Speakers" to "Headphones" on the headphone even. If I change the volume here, I get no audio, but if I change the "Port" back to "Speakers," I get audio through the headphones (and not through the actual laptop's speakers.)

Audio returns to normal when I unplug the headphones.

Any idea how to prevent alsamixer from muting the headphones on an event?

---

