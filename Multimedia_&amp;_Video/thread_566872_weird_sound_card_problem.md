---
title: "weird sound card problem"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by molsen on 2007-10-04
Ubuntu 7.04
Sound Blaster Extigy

I get sound from rhythm box, but I get nothing from websites/youtube/system sounds.  the soundcard is detected and all.  What's the dealio?

also, possibly related: my sound randomly works in windows xp pro.  same deal...it's detected, good drivers, but i get nothing most of the time

---

### Post by molsen on 2007-10-04
any ideas?

---

### Post by molsen on 2007-10-05
lol so i turned ON my onboard sound just to see what would happen.  and music still plays through my external soundcard but the system sounds and webpage sounds come through the onboard soundcard!  what is going on?

---

### Post by exhume on 2007-10-05
I was having weird sound card problems at first as well. Try the following to fix it.
in a terminal type
```

$ asoundconf list
```

the output should look something like the following:

```
Names of available sound cards:
Audigy2
NVidia
```

next type:

```
asoundconf set-default-card CARD
```
Using the one of the soundcard names you got from the list comand to replace CARD.

---

### Post by molsen on 2007-10-05
cool, got it.  do i need to restart for this to take effect?

---

### Post by molsen on 2007-10-06
ok, i did it and now music and system sounds come through my external sound card, but sounds from firefox still go through my onboard sound when rhythm box is paused.  i have to completely exit it for sound to come through the external card.

---

### Post by exhume on 2007-10-06
Hm have you tried looking at the settings for firefox itself?

---

