---
title: "Audio goes in hardy, and must reload alsa"
date: 2008-08-23
forum: Multimedia Software
---

### Post by djrobthaman on 2008-08-23
Hi,

I've been having a problem with my sound on hardy and thought maybe  someone had already figured it out.  I'm not exactly sure what happens, but after a while something gives and no applications can output any audio.  Once that happens, the only way I can get anything to output sound is to quit any application that can output sound (that includes firefox if I have and pages with flash videos loaded) and reload alsa from the terminal.

Then, when I restart the apps, audio is usually fine.  This happens very often though.  I think I've had to restart alsa at least 5 times today, probably more.

Does anyone know what this problem could be and if there is a permanent fix for it?

Thanks

---

### Post by wolfen69 on 2008-08-23
do you have libflashsupport installed?

---

### Post by djrobthaman on 2008-08-24
No I don't and reading the description in synaptic maybe I should.  But this audio glitch affects every program, not just flash.  Do you think flash could cause something like that?

---

### Post by djrobthaman on 2008-08-25
wolfen69, installed the package and still having the same audio problems (with flash as well as other programs).

Any other suggestions?

---

### Post by djrobthaman on 2008-08-28
I've just made a bit of a realization.  I thiink only one application can use alsa at a time.  And whichever one gets use of alsa first will hog it and alsa needs to be reloaded for something else to.

See anything like that before?

---

