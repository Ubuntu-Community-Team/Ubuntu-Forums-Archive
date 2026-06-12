---
title: "Noob question about alsamixer"
date: 2009-04-03
forum: Multimedia Software
---

### Post by BramWillemsen on 2009-04-03
Hello all,

Last week edited some settings in alsamixer. Alsamixer showed something like 15 different control slides. This week I ran alsamixer again, but it **only** shows the **"Master"** and **"capture"** slide. The other ones are gone. Could it be that I forgot to use a certain parameter when starting alsamixer?

---

### Post by ajgreeny on 2009-04-03
Have you changed your sound preferences and chosen pulseaudio, or changed the hardware in the volume control applet?

---

### Post by BramWillemsen on 2009-04-03
When i go to system -> preferences -> sound it says i'm using alsa for everything. when i type alsamixer it shows i use a pulseaudio chip and card though... Strange

When i do this: 
sudo killall pulseaudio
sudo alsa force-reload 

and then type alsamixer again it does show all the ~15 volume slides again. It shows CA0106 for card, and it displays nothing for chip. (using some soundblaster audigy). ** apperantly it still chooses pulseaudio everytime ubuntu boots, even though the sound preferences settings show that i selected alsa for everything. Strange... **

---

### Post by ajgreeny on 2009-04-03
Try to edit your /etc/libao.conf like so which may help.
```
default_driver=alsa
```I found pulse to be nothing more than a pain in the neck with my hardy install

---

### Post by BramWillemsen on 2009-04-03
Thankyou, I'll try it when i log back in on ubuntu :)

---

