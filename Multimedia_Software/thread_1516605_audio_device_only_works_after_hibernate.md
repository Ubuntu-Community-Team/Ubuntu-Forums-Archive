---
title: "audio device only works after hibernate"
date: 2010-06-24
forum: Multimedia Software
---

### Post by Azazel on 2010-06-24
when i turn on my computer and log in i get a notification that says "Phonon: KDE's Multimedia Library -- The audio playback device HDA Intel (ALC880 Analog) does not work." and the system falls back to pulse audio.

Also, i noticed that if i wake my computer from hibernation then the HDA Intel device will begin working again.

I read through the comprehensive sound guide with no luck, this behavior seems very strange to me and im not sure what is causing it. I would much rather use the HDA Intel sound device than Pulse Audio.

Any suggestions?

---

### Post by Azazel on 2010-06-28
bump

---

### Post by Azazel on 2010-06-29
Got ALSA working again. i removed everything i could that was related to ALSA and pulseaudio then re-downloaded and re-installed ALSA

```
sudo apt-get remove --purge alsa-utils alsa-oss alsa-base pulseaudio*
```

```
sudo apt-get alsa-base alsa-utils
```

remember to adjust volume levels with alsa mixer after installing

---

