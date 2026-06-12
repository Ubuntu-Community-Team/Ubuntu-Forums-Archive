---
title: "Skype under JACK"
date: 2009-05-04
forum: Multimedia Software
---

### Post by B4RR13N705 on 2009-05-04
Hi, i was needing to use skype under jack, to broadcast some live stuff.
I googled and i found this piece of code:
```

#!/bin/bash



if [ -z "`pidof artsd`" ]; then



       # run with alsa and dmix support        

       #artsd -F 15 -S 128 -r 44100 -b 16 -s 30 -a alsa -d -D asymed &



       #but we use the built in jack support in artsd

       #artsd -F 15 -S 128 -r 44100 -b 16 -s 30 -a jack -d &



       #edit from snappermorgan, the more than 30 second fix!

       artsd -F 15 -S 128 -r 44100 -a jack -d &



       sleep 1

fi



artsdsp -m /usr/bin/skype

```

I run "qjackctl", and then the script. I logged in, but when i try to make call it says "Sound Error."
And it says this in the shell:
```

Error while initializing the sound driver:
unable to select 'jack' style audio I/O

```
Any idea??

---

### Post by B4RR13N705 on 2009-05-17
Hi, i solved that compiling Akode ant Artsd from source.
I executed the script and artsd connects to JACK :p
But :sad: when i make a sound test i get:
```

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave

```

And if i try to make a call, it just give me a sound error.
Can anybody help??

---

