---
title: "Realtek ALC850 and 5.1 surround sound"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by MakLeod on 2006-10-17
One of my speakers just died, so I am looking into buying a new set.  I have onboard sound with the Realtek ALC850 chipset, and I was wondering if I buy 5.1 surround speakers, will I be able to have all 6 channels operational?  I tried bringing up ALSAMIXER and it seemed like it was possible to get surround sound working.  Anyone out there have the ALC850 chipset and 5.1 surround sound working?  Thanks.

---

### Post by MakLeod on 2006-10-17
shameless bump

---

### Post by MakLeod on 2006-10-21
anybody?  =)

---

### Post by squizzar on 2006-10-24
I've got a Realtek ALC650, with a creative 5.1 speaker set. Mine worked in stereo out of the box. In order to get it to use all the speakers I had to create an .asoundrc file, to tell the ALSA sound system to upmix stereo to all the speakers.  The instructions I found are at:
[http://gentoo-wiki.com/HOWTO_Surround_Sound]("http://gentoo-wiki.com/HOWTO_Surround_Sound")

I then had to enable the correct options in the sound mixe - go to the preferences and turn everything relevant looking on.  On the options tab, set channel mode to 6ch and surround jack mode to shared.

check the switches tab,  surround and centre/lfe down mix, duplicate front and swap surround slot should be off.

This is what worked for me anyway, good luck!

---

### Post by MakLeod on 2006-10-24
Thanks, but I ended up just getting a 2.1 speaker system, was a little bit cheaper and I figured I didn't really need a 5.1 system... 8)

---

