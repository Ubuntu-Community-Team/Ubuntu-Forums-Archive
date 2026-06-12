---
title: "sound card losing channels"
date: 2014-12-05
forum: Mythbuntu
---

### Post by AlecJ on 2014-12-05
I have a annoying problem with the sound card where it losses the 6 channels and so everything is very tinny at boot, the fix is to shh in and run alsamixer then just toggle the 4 6 channel option, this returns the full sound.
I'm at a loss as to why, guess it's not reconfiguring at boot? 
I guess there must be a config file somewhere

The card is a HDA ATI SB using a Realtek ALC887-VD chip on motherboard.

anybody know what file to look for and what to put init?

Alec

---

