---
title: "Flash crashes in fullscreen"
date: 2011-06-28
forum: Multimedia Software
---

### Post by Org1 on 2011-06-28
I have a ATI radeon x1550 video card flash run slow (very low fps) but didn't crash I installed x.org/fglrx-amdcccle flash runs very nice but crashes on full screen.

I've searched and tried flash-aid and reinstalling flash nether worked. I've also removed x.org/fglrx-amdcccle and it stopped the crashing but made the videos unwatchable (low fps).

Any suggestions?



*Useing 11.04 ubuntu
*Does the same thing whit my old ATI 9550

---

### Post by no2498 on 2011-06-28
just seen this it may help



beew 
Chocolate Ubuntu Mocha Blend

  
Join Date: Jun 2010
 Beans: 1,966 	Re: A solution for Flash player... 
Install flash with the flash-aid addon for Firefox, it will configure flash to use hardware decoding (VDPAU) if you have installed the NVIDIA proprietary driver (and optimize flash, clear up conflicting versions etc)

 With chrome it is a bit tricky as it has it own embedded flash apparently.

 If all else fail you can install the flashvideoreplacer addon for Firefox, then you don't need flash for sites like Youtube at all, this will lowers CPU usage quite a bit.

---

