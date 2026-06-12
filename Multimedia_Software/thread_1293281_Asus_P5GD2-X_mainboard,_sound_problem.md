---
title: "Asus P5GD2-X mainboard, sound problem"
date: 2009-10-16
forum: Multimedia Software
---

### Post by cogitordi on 2009-10-16
Using 9.04 Jaunty x86_64.

I have no Gnome theme sounds. I have no sound from Firefox with Flash. I have no sound from VLC. 

I *do* have sound from Movie Player (with codecs installed). 


The command 'cat /proc/asound/cards' shows me:
0 [CA0106] Audigy SE [SB0570]
1 [Intel ] HDA Intel

These are both references to the onboard audio.

I have been searching but I am making no further progress. Anyone have the same mainboard?

---

### Post by Jerry M on 2011-09-30
cogitordi I had the same problem with you since yesterday on Asus P5GD2-X motherbord. My OS is ubuntu 11.04. I tried running the sound troubleshooter that checks for some of the  most common problems. 

Open a Terminal (Program -> Accessories ->  Terminal), then enter this command: 
```
ubuntu-bug audio
```and everything worked fine for me!

---

