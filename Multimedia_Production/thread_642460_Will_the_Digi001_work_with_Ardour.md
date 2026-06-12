---
title: "Will the Digi001 work with Ardour?"
date: 2007-12-16
forum: Multimedia Production
---

### Post by chri5 on 2007-12-16
I have a digi001 protools sound card and would lke to get it working on a PC with ubuntu & ardour. Has anyone done this?

---

### Post by nalmeth on 2007-12-17
Ardour will support anything supported by JACK, and JACK supports anything supported by ALSA.

Here is their soundcard matrix, maybe you can find your card and its compatibility there:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

Failing that, just try it! Install jackd and qjackctl and ardour, go into the settings in qjackctl, select your device and see what happens

---

