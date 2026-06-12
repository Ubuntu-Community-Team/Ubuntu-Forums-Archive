---
title: "Input source combining and priority"
date: 2008-11-24
forum: Mythbuntu
---

### Post by uMuppet on 2008-11-24
I have multiple input sources Analogue and Satellite, the 2 sources have some similar channels and some are unique to each source.  

Question 1:
'Triangle' is identical on both sources, can I make channel 3 go to Triangle on the satellite and if it is busy go to Triangle on the analogue tuner?

Question 2:
'Prime' is unique only to Analogue tuner and 'Sun' is unique only to Satellite tuner.  Can I set it up so that I can use ch+ and ch- to flick between them without changing the input source each time?


Thanks

---

### Post by ian dobson on 2008-11-25
Hi,

If you make sure that both channels have the same EPG you can set the priority for one tuner higher that the other so that myth will chose the best available source.

MythTV doesn't support channel "zapping" over different input sources at the moment. I've seen a patch on the dev channel that supports this but I think it'll take awhile for it to make it into the fixes/trunk.

Regards
Ian Dobson

---

### Post by uMuppet on 2008-12-10
> **ian dobson said:**
> Hi,

If you make sure that both channels have the same EPG you can set the priority for one tuner higher that the other so that myth will chose the best available source.



I can't seem to get this to work.  Where do I change the tuner priority?

---

