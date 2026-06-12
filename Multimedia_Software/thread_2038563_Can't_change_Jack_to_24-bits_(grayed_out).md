---
title: "Can't change Jack to 24-bits (grayed out)"
date: 2012-08-06
forum: Multimedia Software
---

### Post by jsedwards on 2012-08-06
I bought a ESI-Juli@ card ( [http://www.esi-audio.com/products/julia/](http://www.esi-audio.com/products/julia/) ) specifically to record 24bits/192Khz and it was Linux compatible.  It records at 192KHz just fine, but only 16-bits.  When I get in the Jack Setup the "Word length" is set to 16 and is grayed out and cannot be changed.

I also booted it with AV Linux and does the same thing.  The 16 word length is grayed out in the Jack setup.

Is there something somewhere I need to configure or is it because ALSA cannot use the 24-bit capability of the ESI-Julia card?

---

### Post by jsedwards on 2012-08-08
I've determined the problem is not with ALSA, I can record 24-bits with arecord with no problem.

So I don't really need to get Jack working with 24-bits, because I can record what I need with arecord.

It would be nice to know what the problem is with Jack, just in case I ever need to use it, but I can live with this for now.

---

