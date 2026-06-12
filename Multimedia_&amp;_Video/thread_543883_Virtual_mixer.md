---
title: "Virtual mixer"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by velocity_88 on 2007-09-05
Hi!
I am using Ubuntu Feisty 7.04.
I have a tv-capture card (pinnacle usb hybrid-card using em28xx-driver).
Whenever I am tuned in to a channel, the capture-card will output sound in the mixer /dev/dsp1. But the sound is in very poor quality. Therefore I need to resample the sound from /dev/dsp1 to a new virtual(?) mixer /dev/dsp2. I get good quality if I resample the sound directly to my soundcard mixer (/dev/dsp), but I choose to use a virtual mixer because I am planning to use MythTV to watch TV. And then I will tell Myth to listen to the virtual mixer. I need to have a solution like this, because Myth supports pause Live-TV and when I pause the picture the sound continues if I just resample the sound directly to my soundcard. How can I make a virtual mixer like this? I got some pointers that I might get to use dmix-plugin for .asoundrc, but I can't find anything relevant about it.
Thanks

---

### Post by wolfen69 on 2007-09-05
i found dbmixer in synaptic. searching in synaptic for "audio mixer" may yield other results too.

---

