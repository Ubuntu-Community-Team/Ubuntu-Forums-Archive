---
title: "yoshimi and qtractor"
date: 2011-05-15
forum: Multimedia Software
---

### Post by gitaarklas on 2011-05-15
As a newbee to Ubuntu, I'm working on an audio-setup. So far recording audio in Ardour works fine, and I also installed qtractor and yoshimi to do some additional midi stuff.

But when I play a midi file in Qtractor, I get no sound from Yoshimi. Playing Yoshimi with virtual kbd works fine.
Both Yoshimi and Qtractor are on midi ch 1. All connections seem to be ok in Jack (maybe they aren't) and playing Yoshimi with virtual kbd works fine.

A little advice is needed an wellcome.

Thanks

---

### Post by cchhrriiss121212 on 2011-05-15
You just need to connect the 2 together, but doing so is no so simple as yoshimi uses jack midi and qtractor uses ALSA midi. First install patchage and a2jmidi which are in the repositories. Patchage is for making jack connections, and a2jmidi is for connecting ALSA and jack midi together.

When jack is running start a2jmidi, now open up patchage, connect as such:
In green boxes: qtractor midi out -- midi through
In red boxes: a2j midi through -- yoshimi

---

