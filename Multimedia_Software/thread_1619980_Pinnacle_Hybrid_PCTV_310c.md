---
title: "Pinnacle Hybrid PCTV 310c"
date: 2010-11-12
forum: Multimedia Software
---

### Post by makowka on 2010-11-12
I have this pcmcia tv card on debian squeeze on a 2.6.32-5 kernel. I can watch tv with tvtime, but I can't hear any sound. What can I do about it? I tried to capture sound with

```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -D front 
```but I can hear only kind of white noise. The card is working with an analogue tv antenna on the pcmcia slot on a laptop. Could someone give me a hint?

---

