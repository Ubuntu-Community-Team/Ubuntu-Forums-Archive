---
title: "Sound not working"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by fourthofjuly on 2007-07-18
**Sound works in Windows XP, but not in Ubuntu 7.04, Fedora 7 and OpenSuSE 10.1. No sound at all.**

[LIST=1]
[*]I have an Intel D845GCL original motherboard with on-board sound, Pentium D 3.0 GHz, 160 GB SATA HDD & 1GB RAM.
[*]In Ubuntu sound preferences, under Default Mixer Tracks, listed device are HDA Intel (ALSA mixer) and SigmaTel STAC9221 A1 (OSS Mixer).
[*]I have tried disabling sound from BIOS, applied the latest updates of Fiesty, but nothing seems to work.
[/LIST]

Could anyone be kind enough to guide me in making sound work on my system?

Thanks & With Warm Regards,

Devang.

---

### Post by linuxwizard on 2007-07-18
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ubanchaos on 2007-07-18
what sounds dont play....is it the mp3's if its that the sound issue get some plug ins

---

### Post by Freezerburn on 2007-07-18
I have this exact same problem. I've tried almost everything, only to fail miserably.

I[This website]("http://www.ryanheise.com/LW60/") was the closest I got. Says that snd-azx would work, which is the old snd-hda-intel driver.

Please, someone help!

---

### Post by jojomac68 on 2007-07-21
had exactly the same problem. sound would work in XP but not in ubuntu. fixed it by doing the following. Right click on Sound icon >Open volume  control>Edit>Preferences> In select  tracks to be visible select >external amplifier.  this becomes visible  under the switches tab deselect the external amp option and the sound should work.  At least it did for me, now if i could only get my CD drawer to open.

---

### Post by wolfen69 on 2007-07-21
for intel integrated sound:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---

