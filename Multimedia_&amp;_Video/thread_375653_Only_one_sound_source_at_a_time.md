---
title: "Only one sound source at a time?"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by bward1 on 2007-03-04
My computer only plays one sound source at a time.  In other words, if I have amarok running and then open up mythtv then mythtv doesn't have any sound.  If I stop amarok and restart the mythfrontend then I get myth sound.  Myth and amarok aren't the only two applications that fight for the sound, but they are the two most common.  Is there a way to allow multiple sound sources to play simultaneously?

---

### Post by superm1 on 2007-03-04
Make sure you configure myth to use ALSA, not OSS.

Change the sound device and mixer to both ALSA:default.

Same goes for amarok.  Whatever backend you choose, make sure it uses ALSA.

---

