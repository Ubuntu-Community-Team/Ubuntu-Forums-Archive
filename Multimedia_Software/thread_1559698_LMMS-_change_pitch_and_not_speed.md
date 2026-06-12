---
title: "LMMS- change pitch and not speed?"
date: 2010-08-23
forum: Multimedia Software
---

### Post by higashi on 2010-08-23
I noticed that, when choosing different notes, LMMS not only changes the pitch of the instrument, but also the speed. So, if an instrument makes a sound that lasts about 5 seconds, a really low note can make it last about 10 seconds, and a really high note can last about 1 second.

Is there a way to configure how LMMS handles sounds so that it changes their pitch, without changing their speed?

---

### Post by higashi on 2010-08-27
Bump!

---

### Post by tgalati4 on 2010-08-27
LMMS supports VST plug-ins.  You might search for a pitch/tempo plug-in.  I know audacity has a plug-in for pitch change while maintaining tempo.  It works OK, but is limited in range, stretch it too far and it sounds bad.

sox can also change pitch and preserve tempo:

sudo apt-get install sox
man sox

---

