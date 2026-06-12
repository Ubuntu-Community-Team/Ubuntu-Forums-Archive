---
title: "6ch through speakers, 2ch through headphones possible?"
date: 2013-12-26
forum: Multimedia Software
---

### Post by adlin5000 on 2013-12-26
I'd like to have the output through the headphone jack to be 2ch while still having the output through the speakers be 6ch. 

Currently I have to change the audio output in mplayer to 2ch when I want to listen on my headphones and then change it back when using the speakers otherwise I only get the front left/right channels. I can keep changing it back and forth, but its a pain.

Is it possible?

Thanks


Info
Ubuntu 13.04
SBx00 Azalia (Intel HDA)/Realtek ALC889

---

### Post by ajgreeny on 2013-12-26
I'm not certain but I think you can make those changes in the pulseaudio-volume-control application which you can get to from the **volume icon ->Sound-Settings ->Output devices** in your panel.

---

### Post by adlin5000 on 2013-12-26
Thanks, but the sound settings has no settings for headphones that I can see. Am I missing something?

---

### Post by ajgreeny on 2013-12-26
On the "Output Devices" tab of the pulseaudio volume control there should be a "Port" dropdown-box with **Analogue output** or **Headphones** to chose from.

---

