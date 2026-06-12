---
title: "i want to remove LAPSDA Multiband EQ on internal..."
date: 2010-09-11
forum: Multimedia Software
---

### Post by shantiq on 2010-09-11
been trying to install pulseaudio-equalizer
and have decided to go back to alsa

now when i start my machine the sound preferences set it on
LAPSDA Multiband EQ on internal audio analog stereo

INSTEAD of lexicon Alpha which is where i want it to be and where it automatically opened with before


[CENTER][IMG]http://img683.imageshack.us/img683/3972/23991089.png[/IMG]
[/CENTER]


how do i correct that?

i actually want the whole LAPSPA plugin multiband thing removed altogether

how can i do that?


thanx   shan

---

### Post by cchhrriiss121212 on 2010-09-11
Try uninstalling it? Also, what do you mean when you say go back to ALSA?

---

### Post by shantiq on 2010-09-11
hi there well it is sorted now   [http://ubuntuforums.org/showthread.php?p=9833992#post9833992](http://ubuntuforums.org/showthread.php?p=9833992#post9833992)



and i do not why it finally left
i had removed and purged pulseaudio-equalizer and yet the wretched LAPSDA Multiband EQ was still about


do not understand it but hey gone is good




a lot of the sound stuff on ubuntu is cryptic to me and i am sure others

are alsa and pulseaudio not separate ?

---

### Post by cchhrriiss121212 on 2010-09-11
LAPSDA and pulse are separate packages, so that is why LAPSDA was left there. 
> a lot of the sound stuff on ubuntu is cryptic to me and i am sure others

are alsa and pulseaudio not separate ?
I was also confused by sound on Ubuntu/Linux when I started but I can understand the basics now. Sound on Ubuntu can be described like this (the arrows mean "talks to"):

Soundcard > ALSA > Pulse > Software

It is possible to have audio without using Pulse, like this:

Soundcard > ALSA > Software

which is what I thought you meant when you said you had "gone back to ALSA". Some of the sound issues in Ubuntu come from the added layer of Pulse between ALSA and software, which is one reason why many people do not like it.

---

### Post by shantiq on 2010-09-11
thanc chris  :KS:KS:KS   proving the point that


> a lot of the sound stuff on ubuntu is cryptic 


God it could be simpler surely


ps   yes and i do not think i am using pulse now but hey i am not sure

---

