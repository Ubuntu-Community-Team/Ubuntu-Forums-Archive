---
title: "Realtek ALC883 issues"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by nidomedia on 2007-02-15
I'm having a but of a problem with my audio. I have a Intel HDA audio device (a Realtec ALC883). The weird thing is it demonstrates different behaviour in cases in which the hard- and software are supposibly the same. Using the stock audio drivers from ubuntu it seems to be able only to output through the builtin speakers.

When I install the realtec drivers, depending on how it feels, I either have speakers only, or I have the speakers optional headphones (I can mute either both, or the headphones only).

When I have the alsa 1.0.14 drivers installed from the alsa site, I have speakers only.

When I have the alsa 1.0.14 drivers installed from the alsa site with the ALC883 patch ([https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2834](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2834)) I either have the speakers only; or the speakers and headphones as independent outputs (so both can be muted independently).

In order to get the speakers and headphones to work independently; it seems the following sequence of commands must issued.


more informations here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2806](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2806)

---

