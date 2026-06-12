---
title: "Need Sound driver for Acer 5573"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by xpax on 2007-04-26
hi,

I can't find Acer 5573 sound driver? can anybody help me with this.. thanks.

---

### Post by deadgobby on 2007-04-26
what version of Ubie are you running? Any ways please open up the terminal and copy and past the following command.
aplay -l 

and please post the results.

Thanks

---

### Post by xpax on 2007-04-26
currently running ubuntu 7.04. i already run command aplay -l

*** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by deadgobby on 2007-04-27
Your sound is from a intel chip set. Ubie should pick it up right away and you should hear sound. Is your speaker icon have a no sound red circle around it?  Did you up grade? Have you double click on the speaker icon and check all volume levels? Have you installed ALSA mixer? Is the volume control on the laptop all the way up? I
 Just trying to help.
Gobby

---

### Post by xpax on 2007-04-30
Your sound is from a intel chip set. Ubie should pick it up right away and you should hear sound. Is your speaker icon have a no sound red circle around it? Did you up grade? Have you double click on the speaker icon and check all volume levels? Have you installed ALSA mixer? Is the volume control on the laptop all the way up? I
Just trying to help.
Gobby



speaker sound is ok, yes , i ugrade from 6.04 to 7.04. speaker icon check already. alsa mixer all straight up to red light (full).

i post some the problem in this site : [http://forum.lowyat.net/topic/448494](http://forum.lowyat.net/topic/448494)

---

### Post by xpax on 2007-04-30
Your sound is from a intel chip set. Ubie should pick it up right away and you should hear sound. Is your speaker icon have a no sound red circle around it? Did you up grade? Have you double click on the speaker icon and check all volume levels? Have you installed ALSA mixer? Is the volume control on the laptop all the way up? I
Just trying to help.
Gobby



speaker sound is ok, yes , i ugrade from 6.04 to 7.04. speaker icon check already. alsa mixer all straight up to red light (full).

i post some the problem in this site : [http://forum.lowyat.net/topic/448494](http://forum.lowyat.net/topic/448494)

---

### Post by masteryurez on 2007-04-30
> **xpax said:**
> hi,

I can't find Acer 5573 sound driver? can anybody help me with this.. thanks.


You can find your sound-driver inside the original CD that you got when you bought the Acer.. take a look inside that cd.. I find the sound-driver myself because I also have an Acer... good luck

---

