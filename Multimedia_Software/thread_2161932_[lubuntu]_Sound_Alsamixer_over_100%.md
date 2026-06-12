---
title: "[lubuntu] Sound Alsamixer over 100%"
date: 2013-07-12
forum: Multimedia Software
---

### Post by Kifferand on 2013-07-12
Hello,
Since the sound of some videos is too low (on youtube, etc.) when the Alsamixer's master is at 100%, I would like to find a way to put the sound over 100%. For example, with vlc we can go until 200%. Is it possible to do the same thing with Alsa ?
I used to have opensuse and the possibility to go until 150% with Pulseaudio.
Thank you in advance.

---

### Post by Kifferand on 2013-07-18
Up !
Nobody has an idea of what could help me ?

---

### Post by eival on 2013-07-18
pulse audio is the main system driver, you have to use that to boost past 100%

any adjustments in Alsa will reset the peak to 100% again

the only thing Alsa can boost is anything plugged into your mic/line ports, i run my TV audio thru my computer for this same reason because the maximum level of the tv is too low

---

### Post by Kifferand on 2013-07-19
Thank you, it worked, I installed Pulseaudio and now that's where I go when I right clic on the sound icon of my toolbar. The only problem is that my package managers informed during the installation that some components of the packages where not checked, but I suppose it is not so bad...

---

