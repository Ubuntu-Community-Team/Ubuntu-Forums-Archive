---
title: "How to disable all sound"
date: 2011-09-03
forum: Multimedia Software
---

### Post by fig_wright on 2011-09-03
I'm having problems with sound in Ubuntu. I have old hardware and I think the sound driver is causing crashes. I need to disable all sound completely. How can I so this easily? In Windows this is easy (just go to Device Manager and disable the sound device), but I cant think of a way to do it in Ubuntu.

PS Please dont advise taking out the soundcard - I have no intention of ruining my Windows installation to try to get linux working.

---

### Post by Weirdy on 2011-09-03
try running

sudo apt-get remove pulseaudio

in console. That should remove the pulsaudio system which manages your audio hardware :)

---

