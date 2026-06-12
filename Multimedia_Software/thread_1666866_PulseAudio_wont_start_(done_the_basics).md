---
title: "PulseAudio wont start (done the basics)"
date: 2011-01-14
forum: Multimedia Software
---

### Post by meekamoo on 2011-01-14
So pulseaudio just decided to stop working suddenly.

Well, I'm not sure if it's pulseaudio or what.

I have cleaned everything up (logged out, removed ~/.pulse* etc, logged back in) and it still doesn't work.

It is in my startup list.

If I run it manually from the command line it executes without errors although I still cannot access it from the sound panel (the volume control has the X and says 'waiting for sound system to respond')

I've gone through the 'fix pulseaudio' tutorials and they have not been helpful.

Anyone know where I can look?

---

### Post by meekamoo on 2011-01-14
Doh.

I had an environment variable in my ~/.profile to point it to a pulse server on another pc which I don't use anymore.

Man what a mission to find.

---

