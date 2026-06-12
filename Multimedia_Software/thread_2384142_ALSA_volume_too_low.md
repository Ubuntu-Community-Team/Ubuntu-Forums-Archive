---
title: "ALSA volume too low"
date: 2018-02-02
forum: Multimedia Software
---

### Post by carl-leach-public-b on 2018-02-02
I have Google assistant running on a headless system. The sound output is via a USB sound card but the volume is too low, even with volume set to max on alsamixer. I've been trying to figure out how to enable pre-amp, but have been unsuccessful. The current asoundrc is:

```
pcm.!default {
 type asym
 capture.pcm "mic"
 playback.pcm "speaker"
}
pcm.mic {
 type plug
 slave {
 pcm "hw:0,0"
 format S16_LE
 }
}
pcm.speaker {
 type plug
 slave {
 pcm "hw:2,0"
 }
}
```

Any ideas on how I can enable pre-amp or otherwise increase the volume?

---

### Post by carl-leach-public-b on 2018-02-03
I've figured it out. It's nothing to do wit Alsa, rather Google Assistant has the ability to control volume, i.e. "OK Google, turn it to 10"

---

