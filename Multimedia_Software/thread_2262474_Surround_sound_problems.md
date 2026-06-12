---
title: "Surround sound problems"
date: 2015-01-25
forum: Multimedia Software
---

### Post by Subbeh on 2015-01-25
Hi, 

Since moving to a new place, my surround sound settings are messed up. I have no idea how, cause nothing really changed. My HTPC is connected to a receiver with 5.1 speaker setup (HDMI). My other devices which are connected to the receiver do have the correct 5.1 sound.

Initially the problem was that the sound was not outputted to the correct speaker, so the sound from the front-right speaker would for instance come from the rear-left speaker. 

I tried to change the order of the mappings in **/usr/share/pulseaudio/alsa-mixer/profile-sets/extra-hdmi.conf**, but this only resulted in a 2.1 setup, even after undoing the changes.

For some reason, I don't hear any sound from my rear speakers any more after some testing. Also running **speaker-test -c6 -twav** does not output any sound. However, when I test the speakers from the Settings -> Sound GUI, I can test all speakers, although the mapping of the speakers is still wrong.

I'm getting really frustrated. Does anyone know what I can do to make it work?

Thanks

---

### Post by tom_rafalovitch on 2015-01-29
I could really use your help, when I connect my PC to the tv with Hdmi sound is great, but when I plug it to my reciver I hear nothing ! Except when I test the speakers in the settings but it gives only 2 speakers to test.
Plz help me ...

---

### Post by SeijiSensei on 2015-01-29
Try installing **pavucontrol** and see what options it offers for the output stream.  That works on both my machine with an ATI adapter and one with an NVIDIA card.  In both cases it  offers "Built-in Audio Digital Surround 5.1 (HDMI)" as an option.  Sending the output to my receiver produces a full surround field if the source material contains it.

---

