---
title: "Sound card audio problem"
date: 2009-06-26
forum: Multimedia Software
---

### Post by gordoha on 2009-06-26
I have a Dell XPS.  The sound card is, per dell order form, "High Definition 2.0".  I have latest ubuntu version.

It works ago, but the volume just doesn't get very loud.

When the computer came with Vista on it, it was loud.  Now that I have gone to linux, it works, but like i said it is just not very loud.

Any ideas?

Thanks

Bear in mind, I am not all that great with linux, so the more detailed explanation/suggestions the better.

---

### Post by gordoha on 2009-06-26
pretty please?

---

### Post by raboofje on 2009-06-26
> **gordoha said:**
> The sound card is, per dell order form, "High Definition 2.0".

Could you be a bit more specific with 'lspci'?

I'm guessing this is an Intel HDA card, in which case check out [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by kixome on 2009-06-26
On my HP with intel HD audio I always have to double click the mixer(volume icon) go to the top edit>preferences, then enable Master,Headphone,PCM,FRONT,FRONT MIC, Surround,Center,LFE, SIDe, and CD. Turn all of them up except the mic. LFE has some times made my whole sound experience be muted. Try that, if it doesn't work, well sorry I couldnt be of greater help.

---

