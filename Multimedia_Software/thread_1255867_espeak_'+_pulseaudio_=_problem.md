---
title: "espeak '+ pulseaudio = problem"
date: 2009-09-02
forum: Multimedia Software
---

### Post by pallabbasu1234 on 2009-09-02
Espeak is an excellent software. However it has some amount of problems when used with pulseaudio. Sounds get choppy occasionally and some times just a little click is heard other than the actual sound. Have you experienced that?

I guess this is due to reason, each time  a new sound is made it tries to open a new pulse output. Which probably takes some time. It would be better to have a output channel always open.

---

