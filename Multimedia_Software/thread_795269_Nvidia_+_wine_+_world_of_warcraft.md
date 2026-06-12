---
title: "Nvidia + wine + world of warcraft"
date: 2008-05-15
forum: Multimedia Software
---

### Post by johnny.westerlund on 2008-05-15
When i run world of warcraft the system crashes. It crashes so bad that my monitor looses sync and i need to hard reset my computer. I tried installing the Beta drivers from NVIDIA and did not see the problem then. Anyone else having any problem?

Running hardy heron 8.04 64 bit
8 gigs ram
nvidia 8800 gt card.

---

### Post by johnny.westerlund on 2008-05-15
Hrm crap. It did crash even with latest beta driver. Anyone have any course of action?

---

### Post by user-unit on 2008-05-15
sometimes leaving it in 3dfx mode causes problems with nvidia cards.

in your wow directory open the WTF folder and edit the Config.wtf file then add 
```
SET gxApi "opengl"
```

if this doesn't help it's still a good idea to have it in there.

---

### Post by johnny.westerlund on 2008-05-16
Allready have that in my Config. Thanks for suggesting though!
Question is if its a wine problem or something with the nvidia drivers. Should probably try and generate some kind of debug output with wine. Any expert on that here??

---

