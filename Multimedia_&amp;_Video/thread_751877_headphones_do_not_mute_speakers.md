---
title: "headphones do not mute speakers"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by space-litter on 2008-04-11
havent seen any threads about my specific laptop model. most of them are about a### models

me:
toshiba satellite p205-s6347
hda_intel sound card

so far the only way i can get my headphones to work is if the end of my alsa-base file has the following (however, my laptop speakers do not mute when i plug in my headphones):

options snd_hda_intel model=acer
options snd_hda_intel model=toshiba

(that is, i need both of them in the file for my headphones to work)

ive tried: substituting the above with...

options snd_hda_intel model=auto
options snd-hda-intel model=3stack
options snd-hda-intel model=5stack
options snd-hda-intel model=lenovo
options snd-hda-intel model=toshiba (without the acer entry)
options snd-hda-intel model=acer (without the toshiba entry)
options snd-hda-intel model=laptop

none of the above has fixed it...

---

### Post by space-litter on 2008-04-11
have now also tried (at the end of alsa-base)...

options snd-hda-intel position_fix=1 model=lenovo
options snd-hda-intel position_fix=1 model=3stack
options snd-hda-intel position_fix=1 model=5stack

does anyone else have this laptop model? the a### has plenty of support but i cant find much for p### :(

---

### Post by rushinge on 2008-04-12
Does the headphone jack mute the speakers in windows?  This seems like more of a hardware problem to me, most headphone jacks have the speaker cut-out built into them.

---

### Post by VMan on 2008-04-13
> Does the headphone jack mute the speakers in windows? This seems like more of a hardware problem to me, most headphone jacks have the speaker cut-out built into them.

The Toshiba models seem to have it as a software switch instead of a hardware switch.  I have an A135 model.  It appears that you tried the solution that worked for me

options snd-hda-intel model=lenovo

and it didn't work for you.  Sorry, wish I could be of more help.:confused:

---

