---
title: "No sound on my T60"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by phinn on 2006-12-22
I have Ubuntu 6.10 on my Lenovo T60 laptop and I cannot get the audio working at all. I have tried several apps and other websites and nothing seems to work.

Any suggestions?

Thanks

---

### Post by phinn on 2006-12-22
Okay I have since got it working with ASLA but the sound is extremely quiet.

So any suggestions with that?

I added the line:
options snd-hda-intel model=ref

to /etc/modules.d/alsa-base

as per some forum.  But who knows if that did anything.

The audio is just very quiet.

---

### Post by kevinshields on 2007-01-07
Yep - had the same prob (cranked the volume to max but stil there
was virtually no sound) - if you haven't done it already, grabbing the
latest ALSA driver, building it like

 # ./configure --with-cards=hda-intel --with-sequencer=yes;make;make install

and then downloading the alsa-lib and alsa-utils, just building them
like

# ./configure;make;make install

worked swell for me.

---

### Post by Paul_K on 2007-11-29
This thread fixed it for me:

[http://ubuntuforums.org/showthread.php?p=3861060#post3861060](http://ubuntuforums.org/showthread.php?p=3861060#post3861060)

install gnome-alsamixer and unmuted it worked!!!

-PaulK

---

