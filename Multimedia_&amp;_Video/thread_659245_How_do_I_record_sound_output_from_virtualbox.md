---
title: "How do I record sound output from virtualbox?"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by enigma_0Z on 2008-01-05
I'm trying to record sound from virtualbox into a file. The best solution would be to use vsound--but for some reason, using alsa output from Virtualbox, the sound isn't captured, and using OSS output from virtualbox, there is no sound in virtualbox.

does anyone have any recommendations on how I could go about doing this?

Solved:

Use the rdesktop program and vsound to redirect the remote sound from it.

The sample rate is a bit low but oh well.

---

