---
title: "'SayTime' Heard Over Music, How ?"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Rodney9 on 2008-11-04
I know my sound system can play two sounds at once, as my new email wav sound will play during streaming audio, but not 'SayTime'.

Does anyone know how to get 'SayTime' to be heard at the same time as a game, music, etc is playing ?

I have searched here, Google and man, but can't find how.

Rodney.

---

### Post by Rodney9 on 2008-11-05
Anyone know how ?

---

### Post by kostkon on 2008-11-06
*SayTime* uses *sox*, so try to install the *libsox-fmt-alsa* package, if it is not already installed, and check if that solves your problem.

---

### Post by Rodney9 on 2008-11-07
Well I got Ubuntu 8.10 to tell me the time every half hour even if playing streaming audio, as I like to do.
 
I had to install 'Festival' and 'alsa-oss'
 
Then I used gnome-schedule to set a recurrent task and set for 00,30 with the command -
 
echo "Its `date +\%l\%M\%P` oclock" | aoss festival --tts
 
Rodney

---

