---
title: "Low quality on mp3 playback"
date: 2008-06-16
forum: Multimedia Software
---

### Post by eloydark on 2008-06-16
Hello everyone,
I have a small problem that I cannot find the solution. My mp3 playback quality is very low, in low frequencies I get pops as if it was recorded from a very low quality turntable. I have not noticed this problem with other formats but it might exist also, most of my collection is mp3s so I cannot tell for sure! These songs are 320kbps and sound great on Windows and on my mp3 player, so it must be something wrong with my linux box! I tried switching from alsa to oss but there was no difference. My player of choise is Amarok but I have the same problem with other players as well!
What could possibly be wrong with my settings? My soundcard is an onboard Realtec 850.
Thank you in advance.

---

### Post by honus100 on 2009-06-13
I had that problem using VLC and Rhythmbox, found the following solutions (note my machine is connected to an external amp using S/PDIF out, this may or may not work for other setups):

Rhythmbox seems to have a volume control independent of the system volume. Cranking it down, turned the volume up on my speakers, solved the problem. CTRL + down, or look in the Control menu.

In VLC I clicked on the equalizer button and turned the preamp down to zero, cranked the speaker volume up.

---

