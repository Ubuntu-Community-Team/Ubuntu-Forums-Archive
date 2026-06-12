---
title: "Sound stopped working after update on Thinkpad A31 in 8.04"
date: 2008-06-10
forum: Multimedia Software
---

### Post by jimdon77 on 2008-06-10
I just installed the various updates that came up.  After rebooting my computer, the sound stopped working.  I'm hazarding a guess that one of the updates had something to do with that.  How might I be able to reinstall the previous driver (and which one is it), so that I get my sound back?

I have a Thinkpad A31, running Ubuntu 8.04.

---

### Post by fnord23 on 2008-06-11
I have an a31 as well.  I tried a variety of complicated methods..  I enabled the thinkpads volume control and mute buttons with 'tpb', checked and unchecked a million Alsa options, then in desperation I tried:

/etc/init.d/alsa-utils reset

And it all started working.

Hope it works for you.

---

