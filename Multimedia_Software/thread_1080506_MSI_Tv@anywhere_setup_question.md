---
title: "MSI Tv@anywhere setup question"
date: 2009-02-25
forum: Multimedia Software
---

### Post by jmengle on 2009-02-25
Does anyone have any experience with MSI TvAnywhere card, model # 8876?
It has a CX23881-17 decode chip and a Microtune MT 2032 tuner, which I had to remove and replace the shield above the tuner chip to find out what number it was, it's being used in Intrepid 8.10 ia64, with TvTime as the TV app. At first it would not recognise the TV tuner,all inputs came up as composite 1,2,3,last channel watched in Windows (months ago) is displayed but can't change any channels, but after trying a few card=  numbers, I got it working, now it hangs when scanning channels. I might be barking up the wrong tree here, but I think I just need to put the correct tuner= in /etc/modprobe.d/options. I have card=13 in there now, and now I do have all the inputs correctly seen by TvTime, i.e, Television, Composite,S-Video.

I have been all over the net for the last few days, and I have tried several different card/tuner combos, but cannot figure out what the correct tuner number is.

If anyone can point me to where I can get a list of card= and tuner= numbers used in Ubuntu 8.10 I can probably get this fixed myself.

Maybe someone can verify for me that indeed it is /etc/modprobe.d/options where this card gets configured, or am I doing something wrong. If any outputs from lspci or anything are needed, please let me know.

Thank You in advance
Jim

---

