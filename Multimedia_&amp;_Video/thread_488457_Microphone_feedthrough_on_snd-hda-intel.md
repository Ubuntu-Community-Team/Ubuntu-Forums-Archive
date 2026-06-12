---
title: "Microphone feedthrough on snd-hda-intel"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by GlucksRitter on 2007-06-30
Hello,

I have Fujitsu-Siemens Amilo m3438g notebook which seems to have a Realtek ALC880 sound chip. I have tried to install Skype and found that my microphone is not working. I have studied the info available on this subject and ended installing the latest ALSA drivers. I have put model=fujitsu to snd-hda-intel options and currently have a strange effect. The microphone can now be turned on but the input from it goes directly to speakers - however this input is not digitized for use in Skype or any other recording application (I have also tried Ekiga). The effect is very similar to loudspeaker. The input is controllable - I am able to mute/unmute, change gain.

So my question is what can be done to direct the input from the microphone to digitizing input instead of the speakers.

The positive thing in installing new ALSA 1.0.14 was that now the volume wheel is working.

Best,
Alex

---

### Post by GlucksRitter on 2007-06-30
Just some addition - after a little more research I have found that I can hear the microphone input when the first (of three available) input source is set to CD (other options are Mic, Front Mic, Line). The sound is very little resembling the real input, ie. is noisy and broken. This is not looking to be a solution.

---

### Post by chris1952 on 2007-07-24
I apply and for me also it's work but so slowly that I can't ear !!!
do you solve this problem ?

---

