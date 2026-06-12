---
title: "Please help me my problem, is very very very importan to me. SOUND PROBLEM"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by the_analyzer on 2008-03-28
I cannot neither youtube videos, nor system log in/out sound.
I had alsa mixer, and my laptop speakers worked fine with that, but when I plugged my headphones, nothing changed (so I did not listen anything on my headphones, and the speakers were no muted)
NOW i removed alsa mixer and I installed another alternative sound card, sry I dont remember the name but you people should know. anyway. NOW
1. I cannot listen from flash, 
2. I cannot listen from some games (for example from Xmoto)
3. When I plug my external speakers (or headphones) the sound is low, and the lap-top speakers arent muted. 
4. Im going crazy from this problems. 

Can anyone help me?

---

### Post by xc3RnbFO8P on 2008-03-28
And your laptop is?

---

### Post by the_analyzer on 2008-03-28
yes right, my laptop is ACER, it reads Extensa 5210

---

### Post by xc3RnbFO8P on 2008-03-28
In terminal:
> cat /proc/asound/card0/codec#* | grep Codec

---

### Post by ubuntu-freak on 2008-03-28
Do you have alsa-oss installed? Also, try installing Flash manually (see part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833)) and have a look at no.7 in my troubleshooting section if you still have problems with YouTube, namely the paragraph concerning Firefox's configuration file. 

Nathan

---

