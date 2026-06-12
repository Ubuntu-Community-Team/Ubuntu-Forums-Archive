---
title: "Found Fix: Audigy Recording"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by Phasmus on 2006-11-29
I wasn't able to record with my Audigy 4 sound card in edgy.  Tweaking the obvious stuff (master and mic input) in alsa-mixer had no effect.  I found a few posts describing similar problems, either without solutions posted or with solutions to unrelated issues.  It was with nigh overwhelming glee that I finally stumbled upon this: [https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=audigy4capture](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=audigy4capture)

The short version: you need to turn on and turn up the Analog Mix input in alsa mixer to record with this sound card and, presumably, similar models.

Hopefully this is relevant and novel information for this forum.  If not, admins are encouraged to... manipulate... this post as necessary.

As a side note, the sound recorder program has some odd behavior.  It records fine when you turn it on and record once, but if you hit the record button again, input gets shut off for all but one audio source; the one you have selected in the recorder program.  Since recording requires at least master and mic input to be on, this means the sound recorder effectively disables recording if you hit the record button twice.

---

### Post by predaeus on 2006-11-29
I also had the same problem but never got it to work, no matter what mixer setting I used (it worked fine with older versions of Alsa though).

I stumbled over something that helped me to solve it momentarily, but requires manual compilation/installation of the Alsa kernel module, which was easier than expected. And it works for me now, but I've got the same issues as you with the recorder though :-D

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2562](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2562)

---

