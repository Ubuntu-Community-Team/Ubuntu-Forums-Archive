---
title: "Check if microphone is working"
date: 2020-08-27
forum: Multimedia Software
---

### Post by kromak on 2020-08-27
Hello. I want to do a test to know if my microphone is working. Perhaps some software that record sound? What do you recommend ? I can test it on Mate 18.04

---

### Post by TheFu on 2020-08-27
**arecord** to record, then **aplay** to play.

I usually just scream "Czech, Czech, Czech" into the mic. ;)

You can check the levels using something like **pavucontrol**, but if the settings are or get screwed up, the levels aren't necessarily tied to what is output to any specific "sink" or program.

---

### Post by kromak on 2020-08-30
> **TheFu said:**
> **arecord** to record, then **aplay** to play.

I usually just scream "Czech, Czech, Czech" into the mic. ;)

You can check the levels using something like **pavucontrol**, but if the settings are or get screwed up, the levels aren't necessarily tied to what is output to any specific "sink" or program.

Nothing happened. Where the file is supposed to be stored? I can't find anything....

---

