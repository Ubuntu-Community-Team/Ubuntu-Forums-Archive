---
title: "Edgy low sound volume (cs46xx)"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by nixendra on 2007-01-21
hello,

I've a (very) low sound volume on my cs46xx sound card (Hercules Digifire 7.1, chipset: Cirrus Logic SoundFusion CS4624) after upgrading to edgy (kernel 2.6.17-10-generic), already looked in the forum but didn't find anything to resolve my problem, here is a list of what i've already tried:

1. checking that alsamixer/gnome-volume sliders are all way up (Master and PCM at 100% - sound distorted and still very low - in fact I'm only able to hear something when they are a 100%, and my speaker volume too)

2. manually compiling alsa 1.0.14rc2 modules (still the same)

3. black listed cs46xx module and loading cs4294 (no luck, exactly the "same low volume")


could this problem be related with the kernel (an option in) instead of alsa ?
any pointer or advice appreciated

thanks

---

### Post by nixendra on 2007-01-21
still trying to get this soundcard to work I may add that the Digifire 7.1 seems to be the same as the Hercules Game Fortissimo II.

also i've found some options to add when loading the modules, mainly external_amp=1 (or 1 to 8) but that didn't change a thing.

anybody with an Digifire/Fortissimo out there would be kind enough to post the content of their /etc/modules.d/sound ?

---

### Post by wesley_of_course on 2007-01-21
Wesley here ; Don't know if this will help or not but <<<<<<<<<<< [http://www.os2usr.org/os2sound.html](http://www.os2usr.org/os2sound.html)

The file # is the same but it may be an updated one , its from hobbes ? , a zip or you can get it from their website .  Hope you find it !

---

### Post by nixendra on 2007-01-22
thanks for the pointer, I've looked at the zip file but since it's for os/2//windows the syntax is not near the same as the alsa modules (and I've not found similar options)


thanks anyway

---

### Post by nixendra on 2007-01-22
problem solved,

i've compiled the alsa 1.0.13 (drivers, libs and utils) and everything is working fine now.


hope this could help the numerous others "low sound" threads...

---

