---
title: "No Sound on 9.10 Clean Install"
date: 2009-11-04
forum: Multimedia Software
---

### Post by user1397 on 2009-11-04
So I had a windows vista/ubutnu 9.04 dual boot setup, and i decided to do an upgrade to windows 7 from vista, and a clean install of karmic to get its full benefits (like the ext4 filesystem!)

Anyways, I have a sound blaster audigy basic sound card, and it works in windows 7, but not in ubuntu.

am i missing something here?

---

### Post by user1397 on 2009-11-04
hmm wow I've even tried what was suggested somewhere in this forum to install some karmic alsa backport package of some sort and reboot, still no go.

any ideas anyone?

---

### Post by ColJep on 2009-11-05
Have you tried running Alsamixer in a terminal and setting levels there. It seems to start with muted master.

---

### Post by user1397 on 2009-11-05
yea i tried that, everything looked good.

i guess it has to do with pulse audio...but i know next to nothing about that :(

---

### Post by Ulysses361 on 2009-11-06
Please send us the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by user1397 on 2009-11-06
Thanks a bunch man, your post solved my problem.  I did steps 1-4 roughly, and now it works, though it seems as if everything is a little too loud now haha, guess I'll have to mess with the alsamixer settings.

---

