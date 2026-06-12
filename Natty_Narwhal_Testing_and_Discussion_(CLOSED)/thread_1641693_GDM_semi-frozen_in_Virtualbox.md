---
title: "GDM semi-frozen in Virtualbox"
date: 2010-12-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-12-09
I did *sudo apt-get dist-upgrade* as I usually do to upgrade. After reading the "partial upgrade" post, maybe I shouldn't have :)

Anyway, after rebooting (it's been roughly a week since last upgrade, been busy) I can't log in. 

Symptoms...

GDM starts up, but doesn't show username list. I can click the buttons on the lower panel, but none of them do anything (ex. if I press Shut Down, nothing happens).

Any fix?

---

### Post by amauk on 2010-12-09
GDM is broken at the moment
should be fixed soon

in the mean time, you can drop to a VT (ctrl+alt+f1)
login at the terminal, and do "startx" to get to the GUI

---

### Post by wilee-nilee on 2010-12-09
This thread address this, except the fixes don't work so easily in Vbox as you need a cli with a key sequence.
[http://ubuntuforums.org/showthread.php?t=1641092](http://ubuntuforums.org/showthread.php?t=1641092)

---

### Post by kaldor on 2010-12-09
> **amauk said:**
> GDM is broken at the moment
should be fixed soon

in the mean time, you can drop to a VT (ctrl+alt+f1)
login at the terminal, and do "startx" to get to the GUI

It's in a virtual machine, can't do that. Host + F1-5 won't work either ( blank screen)

I might just reinstall when the problem is sorted.

---

### Post by wilee-nilee on 2010-12-09
> **amauk said:**
> GDM is broken at the moment
should be fixed soon

in the mean time, you can drop to a VT **(ctrl+alt+f1)**
login at the terminal, and do "startx" to get to the GUI

Doesn't work in a virtualbox set up.

---

### Post by amauk on 2010-12-09
> **wilee-nilee said:**
> Doesn't work in a virtualbox set up.
oh, ok :P

---

