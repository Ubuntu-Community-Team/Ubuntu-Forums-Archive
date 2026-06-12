---
title: "absolute newb to sound creation.  can I get some help"
date: 2007-11-04
forum: Multimedia Production
---

### Post by Bubs on 2007-11-04
Installed the ubuntu studio and was checking out the apps.  lots. nice.

but How do I "hook up" zynAddSubFX" to rosegarden or ardour so that the sound from zyn gets added to the workspace in rosegarden or ardour.  I've no clue.  been trying for a while.

Like I said totally amateur.  I just want to get into making a few electronic sounds for some animation I'm doing. 

any advice?

---

### Post by Stochastic on 2007-11-05
I assume you have qjackctl running?  if so, just route the output of zynAddSubFX to the input of ardour or rosegarden within the connections window

---

### Post by Bubs on 2007-11-05
I tried that from another post somewhere here. 

but is there something I need to do in zyn and ardour to make sure that they pick up the jack routing?

---

### Post by Stochastic on 2007-11-05
quite often you'll need to open ardour's mixer and adjust the track's input source if the routing isn't already being picked up

---

