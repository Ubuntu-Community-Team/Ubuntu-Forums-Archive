---
title: "[SOLVED] Setting default soundcard"
date: 2008-07-27
forum: Multimedia Software
---

### Post by billesboelle on 2008-07-27
Hey, i've tried setting up my sounds :-)

Got an onboard sound thats broken in the plug, and a pci card that works good.

I can't get Ubuntu to default select the pci card, after trying the settings from complete soundprob guide as below:
It seems the index=0 function doesnt want to help me.
Maybe its due to the fact that my machine registres 2 sound drivers with same name ?
cat /proc/asound/modules gives this responce
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_cmipci

Any ideas,or something you wanna see before being able to help me.
Btw, forgot to mention.
If i try the index option, my pci can is removed from aplay -l and cat /proc/asound/modules.
Regards Alex.



Configuring default soundcards / stopping multiple soundcards from switching

Note: This section assumes that you have installed each soundcard properly.

    *
      In a shell, type
      Code:

      cat /proc/asound/modules

    *
      This will give the the name and index of each soundcard you have currently. Make a note of the names, and decide which one you want to be the default card.

    *
      Now type
      Code:

      sudo nano /etc/modprobe.d/alsa-base

    *
      At the very end of the file, add the following (assuming you have 3 cards with module names A, B and C and you want to have them in the order CAB)

Code:

options snd-C index=0
options snd-A index=1
options snd-B index=2





Found it :asoundconf, and set deafault with it.

---

