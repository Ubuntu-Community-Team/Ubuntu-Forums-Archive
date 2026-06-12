---
title: "Installation of Alsa in 10.10"
date: 2011-01-13
forum: Multimedia Software
---

### Post by Robbyx on 2011-01-13
I can not work with pulse. I have removed it but have failed to install ALSA in its place because the instructions I have are out of date. 

**Could someone please point me to alsa installation instructions that work with 10.10.**

---

### Post by cchhrriiss121212 on 2011-01-13
ALSA is already installed with Ubuntu (check synaptic), pulse relies on it in order to work. I assume the problem you have now is that you have no sound?

---

### Post by Robbyx on 2011-01-13
> **cchhrriiss121212 said:**
> ALSA is already installed with Ubuntu (check synaptic), pulse relies on it in order to work. I assume the problem you have now is that you have no sound?


Yes. I have no sound. When I click on the volume control it says "Waiting for sound system to respond"

---

### Post by Yellow Pasque on 2011-01-13
The volume control is pulse-dependent. See [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa) for the old mixer (or just use alsamixer).

---

### Post by Robbyx on 2011-01-13
I seem to have the sound working. Thank you.

---

