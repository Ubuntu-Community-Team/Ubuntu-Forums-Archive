---
title: "nVidia screen resolution problem."
date: 2008-10-11
forum: Multimedia Software
---

### Post by chris_andrew on 2008-10-11
Hi, all.

I'm unfortunate enough to have an on-board nVidia graphics chip.  Using Open Source drivers, I got an absolutely unusable resolution.  Having been a GNU/Linux user for 10 years, I was very reluctant to install the suggested nVidia driver, but as my screen was unusable, I couldn't see any other option (literally!).

Using the nVidia stuff, my screen is now great.  Unfortunately, whenever I first log on, I have to reset the resolution, because it keeps defaulting back to one that is really high (tiny text).

Is it at all possible to use a free driver, or if not, to have the nVidia (177.80) settings remembered after I have logged-off?

Any help appreciated.

Cheers,

Chris.

---

### Post by overdrank on 2008-10-11
> **chris_andrew said:**
> Hi, all.

I'm unfortunate enough to have an on-board nVidia graphics chip.  Using Open Source drivers, I got an absolutely unusable resolution.  Having been a GNU/Linux user for 10 years, I was very reluctant to install the suggested nVidia driver, but as my screen was unusable, I couldn't see any other option (literally!).

Using the nVidia stuff, my screen is now great.  Unfortunately, whenever I first log on, I have to reset the resolution, because it keeps defaulting back to one that is really high (tiny text).

Is it at all possible to use a free driver, or if not, to have the nVidia (177.80) settings remembered after I have logged-off?

Any help appreciated.

Cheers,

Chris.

Hi and you can install the nvidia settings then use the command ```
gksu nvidia-settings
``` this will hopefully save the setttings

---

### Post by chris_andrew on 2008-10-11
Overdrank,

Many thanks for this.  I assumed that because I am a sudo'er, that the settings should have been saved properly.  This was a mistake.  As root, everything seemed to go fine, without any negative dialogue boxes. 

I'm pretty confident that the settings will now survive a reboot.  I'm in the middle of a load of stuff at the moment, so it's not a good time to reboot or restart X.

I will report back if this didn't work, but I'm sure it will.

---

