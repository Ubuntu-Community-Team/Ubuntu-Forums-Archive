---
title: "Default audio device and changing devices"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Curlydave on 2007-10-20
I have 2 audio devices, onboard audio and my sound card. I want to use my sound card, but Ubuntu 7.10 only plays through my onboard. I changed the default mixer to my card in the sound preferences and the mixer, but it still plays from the onboard instead. 

I remember in one of the older versions there was a way to change devices. (other than disabling the onboard, which is the quick fix, but I don't want to do it) How do I do it?

---

### Post by SimonTheMime on 2007-10-20
Had the same problem. Fixed it doing the following in terminal:

sudo asoundconf list
(it'll list the two names)

sudo asoundconf set-default-card [name of the card]

---

### Post by emartinez13 on 2007-10-20
I had several sound problems with Ubuntu also... You might want to give this a try [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+guide")
Specifically the sectioned titled "Configuring default soundcards / stopping multiple soundcards from switching"

Good Luck

---

### Post by Curlydave on 2007-10-20
> **SimonTheMime said:**
> Had the same problem. Fixed it doing the following in terminal:

sudo asoundconf list
(it'll list the two names)

sudo asoundconf set-default-card [name of the card]

Excellent, issue resolved. We need a GUI setting for this.

---

