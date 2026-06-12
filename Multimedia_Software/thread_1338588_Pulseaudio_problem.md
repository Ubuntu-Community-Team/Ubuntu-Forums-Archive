---
title: "Pulseaudio problem"
date: 2009-11-26
forum: Multimedia Software
---

### Post by RedSingularity on 2009-11-26
Well my system says that pulseaudio is ready for an update.  Well when i try and update i get this message..........

pulseaudio:
  Depends: udev (>=143) but 141-1.2 is to be installed
 Recommends: pulseaudio-module-x11 but it is not going to be installed
 Recommends: pulseaudio-esound-compat but it is not going to be installed

Looks like pulse depends on UDEV which, may i add, is in fact installed.  Why would it be asking for a dependency that is already installed??????

---

### Post by ssam on 2009-11-26
sometimes these are transient issues if only some of a related group of updates reach the repository when you check for updates. wait for an hour and then try pressing reload (if you are in synaptic) or check (in update-manager).

otherwise. do you have any 3rd party repositories?

---

### Post by RedSingularity on 2009-11-26
Yeah i have a few.

---

### Post by ssam on 2009-11-27
could it be that one of those repositories has given you an incompatible version of pulse or udev? in synaptic it should be possible to see where your packages came from, and what versions are available in different repos.

---

### Post by RedSingularity on 2009-11-27
Well that was the problem.  I switched some repos offline and......problem solved.  Thanks :)

---

