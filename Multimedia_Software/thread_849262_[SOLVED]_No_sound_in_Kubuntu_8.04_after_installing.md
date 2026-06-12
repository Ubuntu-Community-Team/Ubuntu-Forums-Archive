---
title: "[SOLVED] No sound in Kubuntu 8.04 after installing VirtualBox"
date: 2008-07-04
forum: Multimedia Software
---

### Post by AlanR8 on 2008-07-04
Have installed VirtualBox on the wife's Dell Dimension 9100 that dual boots between XP and Kubuntu 8.04.

Prior to installation the sound in 8.04 worked perfectly with full surround sound capabilities. Subsequently, I have no sound in Kubuntu, the Kmix icon has a red X over it and an error "Mixer cannot be found". I tried purging Kmix and re-installing with no luck.

Any ideas?

---

### Post by AlanR8 on 2008-07-05
Bump......

---

### Post by AlanR8 on 2008-07-06
Double BUMP!....Beginning to piss me off!

---

### Post by zgornel on 2008-07-08
Try ```
sudo alsa force-reload
``` and check all mixers afterwards. Try also installing aumix and working the volumes from there (I use it for the microphone).

---

### Post by AlanR8 on 2008-07-09
It was the wife that spotted it! Respect! She uses XP on this dual boot Dell and noticed the Grub menu was longer that it used to be. On inspection, all the options are duplicated!

So, I went down to the 3rd option, technically identical to option 1 and booted the system. 

Bu**er me, I had sound again! Sound also works running in virtual box! 

As I type, Doze in Virtual box is updating to service pack 3, I'm listening to the 2005 Cream reunion at the Albert Hall in Amarok, and typing this in Linux FF3!

---

