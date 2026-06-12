---
title: "Help with surround 5.1 and firefox"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by srg84 on 2007-11-01
Hi, i have just added 5.1 surround sound to my card (Aleluya), but now i have a big problem.

Well if i put this in my .asoundrc file:

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

Surround sound works perfectly but I can only have one "sound application" running. If I open firefox, for example, or xmms, an error appears that the sound is blocked.

I have tried a lot of configurations in .asoundrc and nothing, I have tried to set eSound instead of alsa, and sometimes works.  I don't see the solution Anywhere, please help.

I have read that if you want sounds at the same time you must redirect the output to a "sound server" like Esound, or Arts, but works like crap. I'm in Ubuntu Gutsy

---

### Post by srg84 on 2007-11-02
I have solved the problem partially, using eSound (esd) for applications but i don't know how to force the flash player plugin to use esd, ¿any ideas?

---

