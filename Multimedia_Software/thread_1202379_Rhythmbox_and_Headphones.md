---
title: "Rhythmbox and Headphones"
date: 2009-07-02
forum: Multimedia Software
---

### Post by RussellEngland on 2009-07-02
Hi, I'm new to Ubuntu.

I've been using Rhythmbox which I prefer over Amarok. But whenever I plug in the earphones, the sound is "different" from the speakers. The same tracks work fine in Amarok with headphones.

The difference seems like the voice has been lowered in volume, parts of the music has been increased in volume and while some parts of the music I can't hear at all.

Any ideas?

Many thanks

Should of added, I'm using Ubuntu 9.04 and Rhythmbox 0.12.0

---

### Post by HavocXphere on 2009-07-02
To what do the two apps output? ALSA/OSS/Phonon etc.

Chances are that the one is being equalized and the other is not. Or normalized for that matter.

It's also possible that the one is applying replay gain:
[http://en.wikipedia.org/wiki/Replay_Gain](http://en.wikipedia.org/wiki/Replay_Gain)

---

### Post by RussellEngland on 2009-07-02
Thank you for the quick reply but I have no idea, how do I find that out?

---

### Post by RussellEngland on 2009-07-02
Just tried the headphones with Last.FM and the sound is quite bad on most of the tunes - although perfectly fine with the speakers.

---

