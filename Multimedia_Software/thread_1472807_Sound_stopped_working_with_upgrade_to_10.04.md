---
title: "Sound stopped working with upgrade to 10.04"
date: 2010-05-04
forum: Multimedia Software
---

### Post by jamin_melville on 2010-05-04
I've just upgraded to 10.04 from 9.10 and I now have an issue with the sound. 

initially there is sound but when I turn the volume up after it reaches about 50% (or 0db in alsa-mixer), the sound cuts out and won't come back until volume is taken down to 0% and then bought back up to anything less than 50%. A little confusing??

also sometimes the sound just cuts out and wont turn on again, although it does WHILE adjusting volume but that's not a very good solution because I would have to keep changing the volume to get sound..

I've done the standard google thing to see if I can find someone with the same problem but to no success.

lspci shows my card as:

02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

Any suggestions??? thanks

---

### Post by jamin_melville on 2010-05-07
I managed to get it working by editing /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common 

I chucked in the following near the bottom:

[Element Master Front]
switch = mute
volume = off

[Element Headphone]
switch = mute
volume = off

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

then I ran alsamixer and turned the volume on headphones and master front right down then restarted..

---

