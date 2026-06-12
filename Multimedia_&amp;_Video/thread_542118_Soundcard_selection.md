---
title: "Soundcard selection"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by Stochastic on 2007-09-03
Hi, I've got a laptop with an inbuilt soundcard and an outboard USB Tascam US-122.  I had them both working fine on Ubuntu Studio Feisty.  For some strange reason apps have just recently stopped using the Tascam as the default application despite my best attempts.  In System->Preferences->Sound I have the Tascam selected and when I test it there, it does give me the test tones and when I start Qjackctl it is able to use the device (and therefore any jack-based audio app will use the tascam) but when I start apps like Totem or Amarok they now use the inbuilt soundcard.  How can I get these apps to select the Tascam?  It was working fine yesterday.

---

### Post by ddrichardson on 2007-09-04
These commands let you set the default soundcard:```
sudo asoundconf list
sudo asoundconf set-default-card cardname
```The first command gives the sound cards available and the second sets the default.

---

### Post by dandandan on 2007-09-04
That has no effect for me, can u think of a reason why?

---

### Post by ddrichardson on 2007-09-04
How do you mean that has no effect? Are the commands returning errors or are you not able to get the required sound card?

---

### Post by Stochastic on 2007-09-05
Just as an update: the same way the issue appeared it has now disappeared (mysteriously and with no real tweaking of any settings).  But I'm generally happy now (other than my right alt behaviour).

---

### Post by ddrichardson on 2007-09-05
Sorry what right alt behaviour?

---

### Post by dandandan on 2007-09-05
i have a smiliar problem, my onboard card is the default and my soundblaster live is secondary(allthought its not working atm but thats a didfferent problem)


Names of available sound cards:
Intel
Live

root@sued0r:/home/dan# asoundconf set-default-card Live
root@sued0r:/home/dan# 

cmd works, but still the onboard is used as default soundcard (thats what i ment with no effect)
i simple want the live! as first soundcard(card 0, /dev/dsp) and my onboard as card secondary (card 1, /dev/dsp1)

mfg dan

---

