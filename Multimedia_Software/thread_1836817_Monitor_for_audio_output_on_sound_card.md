---
title: "Monitor for audio output on sound card"
date: 2011-08-31
forum: Multimedia Software
---

### Post by CorpusWolf on 2011-08-31
Is there a way to monitor for audio output on a sound card?

What I am trying to do is have the computer notify me by email when audio output stops. I can write the script myself for the most part, I just need to know if there is any way to monitor for audio output on the card so that i can run a script when sound output stops.

---

### Post by mronkko on 2011-09-25
You can use inotifywait in a shell script. This will wait until a sound device is closed and then continue executing the script.

The following would monitor the raw sound playback device on card 0, device 0.

#!/bin/bash

inotifywait -e CLOSE /dev/snd/pcmC0D0p 

<command that you want to run when the sound device is closed>


Hope this helps.

---

