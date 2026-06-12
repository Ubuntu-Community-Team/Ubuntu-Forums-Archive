---
title: "voice digitize software"
date: 2018-11-19
forum: Multimedia Software
---

### Post by jason.jackal on 2018-11-19
Is there any software that I can modulate and digitize my voice making it sound like a computer or something from Kraftwerk or the Cylons from Battlestar Galactica 1978?

---

### Post by ajgreeny on 2018-11-19
Not sure about doing this "live" but you can certainly record your voice using audacity and then add effects to the recording to change it in almost any manner you want if you add the various ladspa plugin packages that are available.

I have used it many times to create sound effects for stage performances.

PS:
I add tap-plugins and swh-plugins to give many possible effects.

---

### Post by Dennis N on 2018-11-19
Several online sites will do text to speech. Here's one that is robotic. You can download a wav file of your creation.
[https://lingojam.com/RobotVoiceGenerator](https://lingojam.com/RobotVoiceGenerator)

---

### Post by Holger_Gehrke on 2018-11-21
No need to use an online service for that. The packages speech-dispatcher and speech-dispatcher-espeak-ng are part of most Ubuntu flavours and can be installed on the ones which don't have them by default. The default voice(s) have often been criticized for sounding too mechanical, so they should be great for your use case. Try 'spd-say "Some text to check speech synthesis"' in a terminal to check whether it's installed and whether it sounds like what you want. To generate audio files you would call espeak directly with the option '-w' and a name for a .wav file. See the various man-pages for details.

Holger

---

