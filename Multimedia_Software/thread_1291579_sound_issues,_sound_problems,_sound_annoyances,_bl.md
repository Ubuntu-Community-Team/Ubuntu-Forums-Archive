---
title: "sound issues, sound problems, sound annoyances, blah blah blah"
date: 2009-10-14
forum: Multimedia Software
---

### Post by binskipy2u on 2009-10-14
ive been using ubuntu, kubuntu for a few years now.. and it NEVER EVER EVER EVER FAILS.. install vlc, everythign works fine.. install amarok cause you like one feature, NOTHING EVER WORKS AGAIN(talking bout sound), get it working.. then open up banshee, and NO SOUND, then NO SOUND IN AN YTHING AT ALL..
ive read EVERRRRRRRRRRRRRRY thread on this.. is there a be all end all solution.. IM SICK AND TIRED of sound issues in 'buntu , I mean when i reboot, sound 99 per of the time works.. ala' WINDOWS??? if i wanted to use windows I'd use it..
so anyone have any idea why, or what i should do.. I dont want to reinstall THE ENTIRE OS(which I DID Many times) to get ONE SOUND APP WORKING.. cause NOTHING IVE EVER READ works.
so anyone, please help????????????????????????

---

### Post by markbuntu on 2009-10-14
Are you still using Hardy 8.04?
Ubuntu or Kubuntu?
Solutions can vary depending on your answers.

---

### Post by binskipy2u on 2009-10-14
9.04 Kubuntu..

but it happens all the time, I had to reboot, and now everything works..
but why oh WHY???? does it suddenly STOP working after so many songs.. or go silent, and then i try another multimedia player, and it wont even PlaY???

until i reboot, ive seen this problem  for years now.. its getting old and annoying...

---

### Post by markbuntu on 2009-10-15
In Jaunty there is a problem with the snd-hda-intel driver that effects some specific hardware that way. It just sort of dies randomly. You can try updating your ALSA version. There is a thread around here with scripts for doing that. You can also try

sudo alsa force-reload

instead of rebooting.

---

