---
title: "Anybody with a M-audio Delta 1010?"
date: 2008-04-13
forum: Multimedia Production
---

### Post by K.Morgan on 2008-04-13
Hi,

I am having serious trouble trying to get my delta 1010 card to work.  I have installed all the latest ALSA drivers, Ubuntu recognises that a Delta 1010 card exists, i have the settings in everything pointing to use the ALSA drivers for the delta 1010 but nothing, no sound at all from any programs, whether it's Amarok or VLC.

I played around so much with the drivers yesterday that it completely messed my system up andi ended up having to do a clean install of Ubuntu today and really don't want to have to go down that road again, so if there's anybody that has managed to get sound from you card, help would be much appreciated.

Kristian

---

### Post by Prefader on 2008-04-13
Assuming your system has another sound card, you might not have alsa set up to use the 1010 as your default card.

Try this:```
asoundconf list
```
and make sure that you see "M1010" in the output.  If it's not there, the card isn't being found.  If it is . . .
```
asoundconf set-default-card M1010
``` should set it up as your default.

---

### Post by K.Morgan on 2008-04-13
Thanks for the reply, it was to do with the default sound card.  Ubuntu was using the sound card attached to my motherboard as the default sound card, so i went into the BIOS and disabled the on-board sound and now everything works perfectrly with the Delta 1010 being default.

thanks


Kristian

---

