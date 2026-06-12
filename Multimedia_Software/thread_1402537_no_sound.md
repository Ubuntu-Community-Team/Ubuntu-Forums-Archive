---
title: "no sound"
date: 2010-02-09
forum: Multimedia Software
---

### Post by filip89 on 2010-02-09
Hi I have a problem. After update to new kernel from 2.6.28-17 to 2.6.28-18 my sound stopped working.

After that i install new alsa 1.0.22.1. it was not helpful
I also tried older kernels 2.6.28-17 and 2.6.28-16 also without sound.

aplay -l shows no sound card, only this line
**** List of PLAYBACK Hardware Devices ****

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0800000 irq 2296

[http://pastebin.com/m27d65173](http://pastebin.com/m27d65173)

Sound did not work also under win xp (after kernel update in linux), and driver reinstallation did not help.
any idea?

---

### Post by krippa on 2010-02-09
Same problem here though I have no XP dual boot to check if sound works there. I will try if it works using a live-cd later on.

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

### Post by filip89 on 2010-02-15
> **kronictokr said:**
> try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

this is for 9.10 I am 9.04, but i tried to install  linux-backports-modules-jaunty-generic and it was no helpful

did someone try live-cd?

---

