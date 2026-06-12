---
title: "How do I save the sound setting in Kmix?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by khelben1979 on 2009-07-13
I want to know how I can save the sound setting in KMix. I want the bar to be saved at the top after each time I reboot the system. See attached picture.

Any suggestions?

---

### Post by igorzwx on 2009-07-13
You can do something like this with OSS Mixer (OSS4),
with command line, as I remember.

It sould be possible to do this with ALSA too, it is so advanced...

---

### Post by khelben1979 on 2009-07-13
I'm hoping that there is a config file somewhere where I just edit a value and save the file. It shouldn't be difficult. Anyone else?

---

### Post by igorzwx on 2009-07-13
[http://www.google.com/search?hl=en&q=How+do+I+save+the+sound+setting+in+Kmix%3F&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=How+do+I+save+the+sound+setting+in+Kmix%3F&aq=f&oq=&aqi=)

---

### Post by khelben1979 on 2009-07-13
I'll try with ```
alsactl store 0
``` and the next time I'll reboot I'll see what happens. I'm pessimistic of this one. Others in the thread have reported that it don't work, I'll see what happens.

---

### Post by igorzwx on 2009-07-13
I cannot help more, because I have OSS4 on my boxes.

---

### Post by SuperSonic4 on 2009-07-13
kmix is pretty much a frontend to alsa anyway, the alsamixer package can change it via the command line too

```
sudo alsactl store
``` has never failed me

---

