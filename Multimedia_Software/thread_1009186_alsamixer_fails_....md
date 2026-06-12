---
title: "alsamixer fails ..."
date: 2008-12-12
forum: Multimedia Software
---

### Post by stephan0h on 2008-12-12
stephan@rechenmonster:~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused


... can somebody please explain?

thanks,
stephan

---

### Post by kiisu on 2008-12-12
Not an expert but maybe you have to start pulseaudio first?

Try typing pulseaudio in the terminal, then check alsamixer

---

### Post by stephan0h on 2008-12-12
cool. 

i had the problem for a long time, that my right speaker was dead.

now i tried to solve it with alsamixer - had seen the hint somewhere on the web - but ... see above.

Starting pulseaudio made alsamixer work. This allowed me to fix the speaker balance. Both speakers working now!!!

Thanks a lot,
Stephan

---

