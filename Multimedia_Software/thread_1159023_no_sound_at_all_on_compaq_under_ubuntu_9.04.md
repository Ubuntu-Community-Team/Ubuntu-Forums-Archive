---
title: "no sound at all on compaq under ubuntu 9.04"
date: 2009-05-14
forum: Multimedia Software
---

### Post by willywonky on 2009-05-14
I installed ubuntu 9.04 on new compaq presario laptop
works great but no sound!
When i try to play a test (alsa) sound i get the following:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

the soundcard is:
hda intel stac92xx analog

help!
thanks in advance

---

### Post by willywonky on 2009-05-14
OK, apparently it is possible to install a driver for this soundcard though not necessarily free of bugs, see
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

however i'm a beginner and need someone's help with this, to follow the instructions at

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

(It says these instructions work for an Intel 82801AA, mine is 82801ICH9, i'm guessing this is still the right one to try?)

I've checked that i have soundcore.  but i am stuck when i get to the unzipping bit of the abouve alsa-project page.  i have a 14k alsa-driver text file, whcih doesn't unzip... clearly i'm a beginner so can someone give me some clues?  Thanks

i might be doing completely the wrong thing in which case please say so!

---

### Post by willywonky on 2009-05-14
ok i'm going to reply to myself again

i have unzipped the package but when i type the line
./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install

it starts working but at the end i get a lot of "permission denied".  (when it tries to write files) what do i do?

---

### Post by xc3RnbFO8P on 2009-05-14
Try **sudo make install**

---

