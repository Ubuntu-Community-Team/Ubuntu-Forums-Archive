---
title: "no Sound on Dell Dimension C251 with 10.10 fresh install"
date: 2010-11-19
forum: Multimedia Software
---

### Post by Chris11 on 2010-11-19
[I]Sorry for double posting but I thought it might be better seen in a new post and I should get it fices 'til tomorrow noon :-\"

Original post is 

[http://ubuntuforums.org/showpost.php?p=10137649&postcount=1846]("http://ubuntuforums.org/showpost.php?p=10137649&postcount=1846") 

Here a copy: [/I]


Hello everyone

I just installed 10.10 on a Dell Dimension C521 and can't get sound working...

First I updated the BIOS from 1.0.4. to 1.1.1. (and solved the frozzen mouse problem.) I searched the forum and came across more ore less always the same information, also it looks like this problem is not described any more since 2 years on a Dell Dimension C521..

Here some info:

[B]aplay -l

**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
Subdispositivos: 0/1
Subdispositivo #0: subdevice #0[/B]

the codec is SigmaTel STAC9227

I added the following lines to /etc/modprobe.d/alsa-base.conf

[B]options snd-hda-intel model=dell-3stack
options snd-hda-intel probe_mask=1[/B]

I don't know how to go on now, any help is warmly appreciated

Thanks to all, Chris

---

### Post by Chris11 on 2010-11-20
ok I figured it out...

in a other thread I found the command **alsamixer** I opened the mixer and found the speaker "slider " on zero (second slider from the left)... I dint find the slider in the graphic application so... 

everything is fine now...

---

