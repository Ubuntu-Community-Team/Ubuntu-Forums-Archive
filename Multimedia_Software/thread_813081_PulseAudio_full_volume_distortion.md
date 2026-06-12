---
title: "PulseAudio full volume distortion"
date: 2008-05-30
forum: Multimedia Software
---

### Post by jharkn on 2008-05-30
PulseAudio distorts sound output when the volume reaches maximum as viewed on the PulseAudio output meter.  While this is understandable since the sound above the maximum would be clipped off I would have thought that the default behaviour would automatically avoid this situation?

For example a particular audio track will reach the maximum level and therefore get distorted at that point, this can be worked around by turning down the volume control of the media player and turning up the speaker volume to keep the same actual volume level.

Do I just have some strange settings?  I haven't mentioned any apps by name since I'm pretty sure its independent of that but feel free to ask for more details.

Thanks. :)

---

### Post by jeffus_il on 2008-06-01
What happens if you shut down pulseaudio and use alsa?
```
pulseaudio --kill
```
and then run your mp3 player.

---

