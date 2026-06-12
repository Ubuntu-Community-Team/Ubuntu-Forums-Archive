---
title: "Realtek ALC880 High Def audio driver?"
date: 2006-03-15
forum: Multimedia &amp; Video
---

### Post by Digitallysick on 2006-03-15
do they have one for linux yet?? when i installed ubuntu last, it wouldnt pick it up

---

### Post by AlteredAgain on 2007-07-06
anyone?

---

### Post by GFC2 on 2007-07-06
Driver for an Intel card, correct?  The correct Linux driver can be found through the ALSA website.  To find info on your particular sound card:

aplay -l  (lower case L)  will give you some info and lspci -v will give you more complete info.  Use your results to find the correct driver on the ALSA website.

---

### Post by beap on 2007-09-02
reinstalling my alsa driver made my realtek alc880 not to work.

---

