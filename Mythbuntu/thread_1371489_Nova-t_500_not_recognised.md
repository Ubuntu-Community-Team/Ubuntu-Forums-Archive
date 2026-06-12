---
title: "Nova-t 500 not recognised"
date: 2010-01-03
forum: Mythbuntu
---

### Post by timbim on 2010-01-03
I've just built and installed mythbuntu 9.10, with a win-tv nova-t 500 card.  The mythtv wiki article on it suggests that it should be recognised automatically, but it doesn't seem to show up anywhere.

What should I do?

---

### Post by SiHa on 2010-01-03
Have you run the backend setup?```
$ mythtv-setup
```
In the capture cards section you add a new card, of the type DVB (V3.x) MPEG capture card. Select frontend 0 for the first tuner.
Do the same for the second tuner (frontend 1).

---

### Post by timbim on 2010-01-03
There's no field against the frontend heading!  I can't do anything in the DVB device number field.

---

### Post by SiHa on 2010-01-03
Ah, OK, thought I'd check, as you hadn't mentioned quite that much.

Is there anything else on the PCI bus? I've got a -500, and I have found it a bit picky sometimes if there's another PCI card in there.

---

### Post by timbim on 2010-01-03
Nvidia graphics card...

---

### Post by SiHa on 2010-01-03
Clutching at straws now. Tried changing slots?

---

### Post by utar on 2010-01-04
Type "dmesg | grep dvb" into a terminal and post the output here.

---

