---
title: "two programs using one sound card?!"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Gizmo89 on 2007-11-04
hi, can anyone tell me how i can get my sound card to be able to work on more than one program? like on kubuntu (so i've heard) and windows...

---

### Post by bingoUV on 2007-11-04
If they try open same sound card directly, they will never work together. This is because sound cards  are opened in exclusive mode. If one program has opened it, the other will be denied access. Old linux programs sometimes have this problem.

But, not to worry. Nowadays most programs have an option to open a sound library (artsd, esd, alsa etc) instead of the sound card directly. You just have to ask the program to use  one of these libraries. If you post which programs you are having trouble with, someone here will guide you to your solution.

---

