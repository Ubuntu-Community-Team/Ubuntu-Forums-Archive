---
title: "MythTV Multiple Frontends, Won't allow different settings"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-04-18
I have a MythTV system consisting of a frontend/backend system and also two remote frontend machines.  Remote frontend1 needs to use dsp0 for sound, and frontend2 needs to use dsp1 for sound.  For some reason, though, when I change the sound device on one machine, it also changes it on the other.  Is anyone else having this problem?

---

### Post by superm1 on 2007-04-19
It sounds like you might have the same hostnames assigned to these two machines.  Is this the case?  If so, use the unique-identifier option on the second (non backend/frontend machine).

---

### Post by josesanders on 2007-04-20
That did it, thanks!

---

