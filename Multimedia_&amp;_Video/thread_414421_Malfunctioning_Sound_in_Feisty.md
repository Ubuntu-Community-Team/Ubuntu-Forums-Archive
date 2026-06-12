---
title: "Malfunctioning Sound in Feisty"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by IgnacioMiller on 2007-04-19
Hey all,

When I first installed Feisty I had no sound. I went into System>Preferences>Sound, and found the device that played sound for me, CA0106. There were for entries with the exact same name, the one that worked was the fourth one. I installed some packages related to music, and uninstalled some, and then when I went to go listen to a .ogg file I could not hear anything. I went back into the sound configuration applet and tested my CA0106, with no sound. I tested all available devices and all had no sound.

Disclaimer:
My speakers are plugged in
Alsamixer shows nothing muted
Speaker volume is turned up

Thanks for your help, I'm sure this forum is busy today of all days,
Ignacio

P.S. I have a Soundblaster Live! 24 bit soundcard. It worked perfectly in Edgy.

---

### Post by IgnacioMiller on 2007-04-19
Resolved.

---

### Post by jsully1 on 2007-04-20
How did you resolve?

---

### Post by tombug on 2007-04-20
> **jsully1 said:**
> How did you resolve?

ya i second that i have the same problem just wanna know how you solved it

---

### Post by Azakus on 2007-04-20
Solution:
[http://ubuntuforums.org/showthread.php?p=2415537](http://ubuntuforums.org/showthread.php?p=2415537)

---

### Post by fvs on 2007-04-20
Same problem? What's up?

---

### Post by pitbulls20 on 2007-04-20
I am having the same problem and i couldn't figure out what the above link was trying to tell me to do

---

### Post by jsully1 on 2007-04-21
This fixed it for me - all I had to do was follow the very helpful sound troubleshooter found here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

For some reason this also nuked GDM, so you need to do a
sudo apt-get install gdm
as well.

---

