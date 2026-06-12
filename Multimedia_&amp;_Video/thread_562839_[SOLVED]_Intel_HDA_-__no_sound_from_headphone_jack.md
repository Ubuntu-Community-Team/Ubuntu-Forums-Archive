---
title: "[SOLVED] Intel HDA -  no sound from headphone jack"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by krajator on 2007-09-29
Hi!

I have Dell Vostro 1500 running Kubuntu 7.04 (I just switched from windows). I have a problem as speciefied in thread title. Just after installing kubuntu I had sound coming out from internal speakers and headphone jack at the same time (pluging headphones into jack didn't mute speakers). To fix this issue I tried compiling the latest ALSA from source following [THIS]("https://help.ubuntu.com/community/HdaIntelSoundHowto") guide. Now I don't have any sound from headphone jack at all.

Output of 
```
cat /proc/asound/card0/codec#* | grep Codec
```

is
```
Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06
```

Any help would be much apprecieted as I'm completely new to linux.

---

### Post by krajator on 2007-09-30
bump

---

### Post by krajator on 2007-09-30
I've managed to solve this myself. Solution is to install alsa-driver-1.0.15rc3, alsa-lib-1.0.15rc3 and alsa-utils-1.0.15rc1 from source.

Step-by-step instructions can be found [HERE]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). Everything from this HowTo applies except filenames (1.0.15rcX instead of 1.0.14) and part about specifying module parameters manually (at least I don't have to do this on my machine, I'm not sure about others though).

---

### Post by blackaardvark on 2007-10-01
Yup, it worked for me! Thanks for that. It got rid of my crackling audio problem too! Sweet!

However.....I've now lost all audio from firefox. Oh dear.

---

### Post by ufalcon on 2008-02-12
Thanks!!

This also fixed my front intel hda jack issues under Gutsy (7.10).  I haven't messed around with the mic to see if it works yet.

Hopefully Hardy whatever-it's-called will include a newer version of ALSA by default!

---

