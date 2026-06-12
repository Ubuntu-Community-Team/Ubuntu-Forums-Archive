---
title: "DVD Problem"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by NewDisciple on 2006-06-14
I followed the instructions from the restricted format to install "libdvdcss2" and had no problem with it.  However, when I try to play a DVD I get an error message about trying to watch an encrypted movie without "libdvdcss2."  I know it is in my files as I am able to follow the install path to it.  Any ideas?   I don't have a clue at this point.

---

### Post by NewDisciple on 2006-06-14
Finally got mplayer to play but I only have sound from my internal card.  Really need to be able to use my headphones.  ???

---

### Post by scxtt on 2006-06-15
check your alsa mixer, there's a "headphone jack sense" tick box - maybe that'll help ...

---

### Post by NewDisciple on 2006-06-15
No such critter on my alsamixer.  After I try a DVD I lose my head phone jack altogether.  If I reboot it returns until I try to play a DVD again.  There isn't much for configuration on the alsamixer GUI so I'm wondering if I am missing a dependency or something.

---

### Post by scxtt on 2006-06-16
don't know - i have built-in sound as well {AC'97} and haven't noticed any issues ...

---

### Post by NewDisciple on 2006-06-16
Was missing one of the alsa parts from synaptic.  I have everything fixed now and it works fine.

---

