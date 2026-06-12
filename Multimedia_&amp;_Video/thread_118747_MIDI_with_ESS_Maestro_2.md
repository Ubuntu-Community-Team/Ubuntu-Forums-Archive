---
title: "MIDI with ESS Maestro 2"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by christhemonkey on 2006-01-17
Is there anyway to load a soundfont onto my soundcard?
Its an ESSmaestro2 and it says it supports wavetable synthesis?
But when i use sfxload it says no AWE devices detected!
Any help appreciated.

---

### Post by FarEast on 2006-01-17
Hi christhemonkey,

I think sfxload supports soundblaster only...
To play MIDI files with soundfonts, I recommend you to install **timidity**(I am not sure if you are already using it, though).

[http://ubuntuforums.org/showthread.php?t=111061&highlight=timidity](http://ubuntuforums.org/showthread.php?t=111061&highlight=timidity)

---

### Post by christhemonkey on 2006-01-18
it also said it was soundblaster compatible?

---

### Post by FarEast on 2006-01-18
> it also said it was soundblaster compatible?

I am not sure, but I do not think that the internal architecture
of your card is 'compatible' with soundblaster.  If it were compatible,
you would be able to load soundfonts with the utility from Creative
Labs(on Windows).

On the other hand, I wish you could load soundfonts with sfxload.
We may well expect cards with capability of handling soundfonts
to have such compatibility...

---

