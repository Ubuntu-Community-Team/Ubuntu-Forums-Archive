---
title: "No sound on Xubuntu"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by MedievalManIII on 2006-10-15
I am using Xubuntu 6.06 on this computer:

CPU: Pentium III 500mhz
VID: Radeon 32MB
SND: Rockwell Riptide
RAM: 192MB

Everything seems to work except for the sound.  My speakers emit no sound at all.  I have followed the comprehensive guide and it failed to fix my problem.  

Here's what happened while I used the guide:

1) no soundcards are detected after "aplay -l"
2) the sound card is listed after "lspci -v"
3) I look around for an alsa driver on the internets.  It exists.
4) I do "sudo modprobe snd-riptide" but nothing happens
5) I tried getting alsa drivers from a fresh kernel but nothing happens
6) I tried compiling the alsa-source but I cannot locate module-assistant and something else
7) I tried using the drivers from the alsa project but it does nothing

Any ideas on what to do next?


Any ideas?

---

