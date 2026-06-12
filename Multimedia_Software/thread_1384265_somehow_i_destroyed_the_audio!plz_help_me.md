---
title: "somehow i destroyed the audio!plz help me"
date: 2010-01-18
forum: Multimedia Software
---

### Post by aintour on 2010-01-18
i had pulse audio i change it to esound, but i don't have audio no more
and i want to put back pulse audio working with skype and amsn...


i follow some tips from forums but nothing is working right now!
please can you help me? with a good step to step solution to install again pulse audio and working with amsn and skype?

Thank you a lot guys! i really need your help.

---

### Post by Icarus315 on 2010-01-19
Open a terminal, Applications -> Accessories -> Terminal.  Then in that terminal type: gstreamer-properties and press Enter.  This will let you choose the sound system used by Gnome.  Try the ones available until you find one that works.  If changing the desktop-wide sound system doesn't work then you need to go into each application itself and see if you can change the sound system used per-application.

---

