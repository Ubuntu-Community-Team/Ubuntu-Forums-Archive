---
title: "Audacious no longer plays audio"
date: 2010-03-31
forum: Multimedia Software
---

### Post by g-raf on 2010-03-31
I recently switched my usb external soundcard from an M-Audio Fast Track Pro to an Edirol UA-25EX (i can get 24bit working on it - that's why). 

After making the switch, all audio programs are working just fine except for Audacious. When i try to play audio, i get 00:00 and no playing. The output plugin is ALSA and the audio device is UA-25EX. I don't understand why it's not playing the audio.

---

### Post by cchhrriiss121212 on 2010-03-31
Try opening it from a terminal window. You should be given some error messages.

---

### Post by g-raf on 2010-04-03
> **cchhrriiss121212 said:**
> Try opening it from a terminal window. You should be given some error messages.

This is what i got:

```
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
```

Doesn't look like an error message. Maybe this problem has to do with ALSA configuration? I'm clueless at this point.

---

### Post by g-raf on 2010-04-04
I've tried a few new things. First, i tried to install the latest version of Audacious2 by downloading it and the plugins from the Audacious website. Audacious2 wouldn't open, so I just uninstalled and reinstalled Audacious from synaptic. When i try to open either of them in the terminal, this is what i get:

audacious: unable to launch selected interface skinned

audacious2: unable to launch selected interface skinned

---

### Post by cchhrriiss121212 on 2010-04-04
I've had stability problems with audacious before, did you install the plugins and the plugins-extra packages when you used synaptic? 
Maybe try out another audio player, I'd recommend quod libet.

---

