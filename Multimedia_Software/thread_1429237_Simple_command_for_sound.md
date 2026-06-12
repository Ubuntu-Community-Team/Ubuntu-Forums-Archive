---
title: "Simple command for sound?"
date: 2010-03-13
forum: Multimedia Software
---

### Post by brandon88tube on 2010-03-13
I wanted to know if there was a simple command for the default sound in ubuntu. An example would be typing volume = 42 into the terminal or something. I'm not looking for alsamixer or anything like that, but maybe thats the only option.

---

### Post by brandon88tube on 2010-03-14
Seems I've found my own answer to this. I can do it by using pacmd. Once pacmd is running, similar to something like mysql, you can type in a command like set-sink-volume device number/name then the volume level. The only thing thats difficult about it, is that 65536 = 100% and values greater than this amplify the audio signal (with clipping). This is all if you have PulseAudio for sound. [http://pulseaudio.org/wiki/CLI](http://pulseaudio.org/wiki/CLI) is a link for better instructions.

---

