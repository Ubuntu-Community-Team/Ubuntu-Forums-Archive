---
title: "Sound Issues for Gateway MT3707"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by cyb3rpeace on 2007-07-16
HI all,

I have been working on trying to get the sound working on my gateway mt3707 laptop. I have everything else working great but the sound. The sound icon is there and it looks like the drivers are installed. Does anyone have anything that can be tried.

To solve the wi fi problems i just got an intel wireless g card and replaced the realtek that was in the laptop.

thanks in advance

---

### Post by wolfen69 on 2007-07-16
do:
```
lspci
```
if it is an intel card, go here  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---

### Post by cyb3rpeace on 2007-07-16
Nope it's a
> 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)


---

### Post by splitforthecity on 2007-09-19
i was trying to fix this for several months and just found this which fixed my sound.

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)

---

### Post by Schiz0 on 2008-01-14
Ah ha! After ripping all my hair out over this issue, I find a fix. Thanks!!!

---

