---
title: "HP 520 sound drivers"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by aaryansh87 on 2007-11-01
Can anybody help me get the sound drivers for HP 520. I have been searching for them and didn't find them....

Please help

---

### Post by renzokuken on 2007-11-01
upgrading to the latest alsa-driver may help

---

### Post by aaryansh87 on 2007-11-01
still the problem isn't solved......

---

### Post by Yellow Pasque on 2007-11-01
Does this help?
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by dondong on 2007-11-06
guys,iv  got the same problem with hp520, No sound but the device can be detected as "conexant 20549", really confused. anyone can help me with this? :confused:

---

### Post by dondong on 2007-11-06
bingo!problem solved.
add a line to "/etc/modprobe/alsa-base" as follow:
"options snd-hda-intel index=0 model=3stack"
guys who hav the same problem can try out this.

---

### Post by dondong on 2007-11-06
oops!wrong again,seems to be unstable,no sound again,i dont know why,feeling broken,any1 can help me?:confused:

---

### Post by onta on 2007-11-24
> **dondong said:**
> bingo!problem solved.
add a line to "/etc/modprobe/alsa-base" as follow:
"options snd-hda-intel index=0 model=3stack"
guys who hav the same problem can try out this.


i've already that line to, but i didn't affect to my notebook, right now i've already installed my alsa mixer into version 1.0.14,

you can access using alsamixer on terimal (using root session) and then make sure ITEM IEC958 is not muted, voila.... now i'm running xmms, totem, player and everythin's fine...BUT... if you have dual OS on your notebook, usually after you use your windows and go to your linux, the sound is missing, i dont know what's the cause, but you should shutdown your windows first, and then turn on again and go to your linux session :D voila it works... dunno how that's works :D still figuring how...

thanks
onta:popcorn:

---

