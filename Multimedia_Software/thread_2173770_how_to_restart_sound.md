---
title: "how to restart sound ?"
date: 2013-09-11
forum: Multimedia Software
---

### Post by Coder88 on 2013-09-11
My soundcard works fine, just that sometimes something is hijacking it and then i have no sound playing a video/mp3. Is there an easy command to restart the sound driver/daemon? I have pulled up gnome-alsamixer to check and nothing is muted to be causing this. I can get sound back by restarting (logging out then in did not fix this) but that is rather inconvenient.

---

### Post by Yellow Pasque on 2013-09-11
This command may help:
```
sudo alsa force-reload
```

> just that sometimes something is hijacking it
The only thing that should be using the audio device directly is pulseaudio. To see what's using the sound device:
```
lsof /dev/snd/*
```

---

