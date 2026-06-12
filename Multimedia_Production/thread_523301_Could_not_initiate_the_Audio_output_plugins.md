---
title: "Could not initiate the Audio output plugins"
date: 2007-08-11
forum: Multimedia Production
---

### Post by EMM386 on 2007-08-11
Hi all Im using 7.04  and  install PiTivi and every time I try to start the program I receive a error message 
'** Could not initiate audio output plugins - Make sure you have at least one valid audio output sink available ( alsasink or osssink) ** 
I have alsa install and music plays on VLC and Mplayer but the system sounds are not working.  For a few days I been trying to fix it and searching on the Net and in the Forum for some solutions but so far haven't found anything.

---

### Post by Damper on 2007-10-17
EMM386 - I had this trouble and the solution I found was this;

I had installed an addon PCI sound card some time ago and disabled the onboard AC97 sound chipset in the course of installing the new card. Fiesty Fawn / Pitivi wouldn't work with the new card. So, I went into the system BIOS and re-enabled, set to AUTO, the AC97 and now it works.

---

