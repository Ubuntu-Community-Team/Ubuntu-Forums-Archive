---
title: "No Sound- Intel ICH8 onboard soundcard"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by DMCrimson on 2007-10-18
Earlier today i decided to try out the new Ubuntu release.  After installation, the sound doesn't work on my machine.  Video works, flash works, but audio does not.  I have checked out a couple guides( including this forum's Comprehensive Sound Guide.  I installed codecs and plug-ins, and it seems to be a driver issue.  I am using an Intel Corporation 82801H (ICH8 Family) HD Audio Controller.  It's an onboard soundcard that worked on Vista but it may as well be dead on Ubuntu. Can anyone help?

---

### Post by wolfen69 on 2007-10-18
this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards) is for feisty, but may be worth a try.

---

### Post by mbeedee on 2007-10-19
I'm having the same issues with the Intel 82801G (ICH7 Family). It worked perfectly on Feisty.

---

### Post by mbeedee on 2007-10-19
Wait never mind. It turns out running the generic kernel as opposed to the 386 kernel is a good idea.

---

### Post by DMCrimson on 2007-10-19
> **wolfen69 said:**
> this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards) is for feisty, but may be worth a try.

I tired it, but it didn't work.

mbeedee, what do you mean by running the general kernel instead of the 386 kernel?  Im still new to linux in general.

---

