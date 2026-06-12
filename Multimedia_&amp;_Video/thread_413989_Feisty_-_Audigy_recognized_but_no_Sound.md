---
title: "Feisty - Audigy recognized but no Sound"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by plb on 2007-04-19
My audigy is detected but no sound. Everything worked fine in Edgy. Anyone else have this problem?

---

### Post by jenast on 2007-04-19
Yes, exactly the same.
So far have tried to uninstall & reinstall alsa driver through synaptec, also by manually compiling the alsa driver + librarys+ utils. 

No luck so far. I also noticed that alsaconf is not available anymore. I am just a beginner myself and have not found the solution yet.

Any suggestions?

/Jenast

---

### Post by plb on 2007-04-19
Found Solution: open alsamixer goto "Audigy Analog/Digital Output Jack" and turn it off = hit "M"

---

### Post by Anivair on 2007-05-15
That would be easy if I could open alsamixer. 

rossman@ltsp-2:~$ amixer
*** PULSEAUDIO: Unable to connect: Connection refused
amixer: Mixer attach default error: Connection refused
rossman@ltsp-2:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused
rossman@ltsp-2:~$ 


Yup.  Not good. Pulse is installed. Just in case it matters. It wasn't before and installing it hasn't changed my errors.

---

### Post by slearl on 2007-05-16
> **plb said:**
> Found Solution: open alsamixer goto "Audigy Analog/Digital Output Jack" and turn it off = hit "M"

Thanks for the help ... worked for me too.

---

### Post by nille on 2007-05-19
I thought I've tried everything, apparently not. Thank you, you just saved my day! :guitar:

---

### Post by ButtonMasher on 2007-05-19
> **plb said:**
> Found Solution: open alsamixer goto "Audigy Analog/Digital Output Jack" and turn it off = hit "M"

Fixed mine too.  Thank you!  I love these forums...

---

