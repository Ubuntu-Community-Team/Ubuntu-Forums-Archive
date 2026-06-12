---
title: "No audio.  Audacious &quot;ALSA error: No suitable mixer element found&quot;"
date: 2019-03-20
forum: Multimedia Software
---

### Post by t0p on 2019-03-20
Running lubuntu 16.04.2... and I have no audio.

If I use audacious I get this error:

```
ALSA error: No suitable mixer element found.

ALSA error: snd_pcm_open failed: No such file or directory.
```

If I try vlc I get:

```
Audio output failed:
The audio device "default" could not be used:
No such file or directory.
```

and no matter what audio option I try in vlc I get no sound...

Any ideas please?  Cheers.

---

### Post by wildmanne39 on 2019-03-20
*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

---

### Post by Dennis N on 2019-03-20
No guarantee, but you might try installing **pulseaudio** and **pavucontrol** packages. Restart.

I recall needing to install those in older Lubuntu - back to at least 14.04 when they didn't include pulse audio and there were sound problems. According to Lubuntu 16.04 manifest, looks like these are also not in the 16.04 release. In audacious, you should then check that output plugin is set correctly.

---

