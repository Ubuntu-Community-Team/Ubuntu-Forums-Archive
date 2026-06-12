---
title: "An application (Open Arena) is muted and I cannot unmute it"
date: 2010-09-19
forum: Multimedia Software
---

### Post by UeB on 2010-09-19
It is possible to mute specific applications via the audio preference window in gnome (as far as I know this is a feature of pulse audio).

Now Open arena is muted in this way and I cannot unmute it because you only see the muted apps in the audio preference window, wenn they are running. But when Open arena is running I cannot escape from the app with the mouse courser.

What I thourght of but could not find out by searching the internet:

* is a possibility to force an app in the background an returning mouse and keyboard to gnome?

* is there a file where the pulse audio / gnome audio preference changes are stored that I could delete to set everything back to the unmuted default?

thanks in advance!

---

### Post by UeB on 2010-09-21
hmm bumping it... anybody an idea?

the this behaviour survived even the upgrade from Ubuntu 9.10 to 10.04....

---

### Post by UeB on 2010-09-26
ok deleting ~/.pulse/ seems to do the trick now.

I did this and after a reboot all application specific sound options where gone including the mute of open arena.

I am quite sure I already tried this some months ago but there all the app specific options where restored after a reboot... if I remember correctly...

---

