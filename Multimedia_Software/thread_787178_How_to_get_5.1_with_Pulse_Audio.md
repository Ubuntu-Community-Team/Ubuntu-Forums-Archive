---
title: "How to get 5.1 with Pulse Audio?"
date: 2008-05-08
forum: Multimedia Software
---

### Post by pogoyoyo on 2008-05-08
hey i just did, " The (almost) Perfect Pulse Audio Setup "  located, [http://ubuntuforums.org/showthread.php?t=776739&highlight=5.1+surround](http://ubuntuforums.org/showthread.php?t=776739&highlight=5.1+surround)
and i now have pulse audio set up as my main sound thing, but the only reason i got it is cuz i thought it would help me solve my surround sound problem ( using amarok, i dont get any sound to center and rear speakers )
anyone know how to get other speakers working using pulse audio?

---

### Post by AFarris01 on 2008-05-19
have you tried editing the "default-sample-channels" entry with this: 

sudo gedit /etc/pulse/daemon.conf

its down near the bottom.  i believe it defaults to 2...just uncomment it, change it to 6 and restart and you should be all set.

---

### Post by wolfen69 on 2008-05-19
i believe that you will have to change the value to 5 not 6, since the subwoofer is really not a seperate channel, and just for low frequency sound.

---

