---
title: "swfdec install knocks out audio (ALSA)"
date: 2009-10-22
forum: Multimedia Software
---

### Post by polarberg on 2009-10-22
Edit: Solved, disregard, swfdec had nothing to do with the problem. I forgot I installed gnome-alsamixer, which apparently had the Master channel muted by default.

Just tried to install swfdec as a remedy to YouTube acting funny (it seemed like I could view the first video I retrieved but nothing after that, different story). Well, in the middle of the install I go back to Movie Player and suddenly sound isn't happening. I checked in the Sound preferences, ALSA is still the only thing that works, but there's no sound playing when I test it. It must have had something to do with the prereqs I was installing to make swfdec configure properly, but I have no idea what could've done it. The only thing I specifically remember installing is libglib2.0-dev.

I'm very new to this and I don't even know what output I could paste that would be helpful in diagnosing the problem. And, almost as an aside, I still don't even have swfdec installed yet.

---

