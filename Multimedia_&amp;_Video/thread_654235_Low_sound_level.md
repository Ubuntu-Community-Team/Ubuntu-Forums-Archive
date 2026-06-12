---
title: "Low sound level"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by DavidTurner on 2007-12-30
I Have solved all the problems in my usual way -muck around with it, reboot and it works,but i dunno how i did it.

I have looked at the other thread addressing this issue-I have a toshiba satellite. 
I have tried putting this command into terminal: rmmod snd_hda_intel
and it keeps giving me: ERROR: Module snd_hda_intel is in use,
even though no sound is playing- only terminal is running.
how can i disable sound so i can run the command then enable the sound?
or how can i stop this error?
Please help.

I now have a new error- the sound has been boosted but is very crackly.
Can anyone help with this?

---

### Post by deadgobby on 2007-12-30
Simple. Try in the terminal 

killall esd
 
See if that stops it.

Gobby

---

### Post by DavidTurner on 2007-12-30
It says no process killed. Sorry:(

---

