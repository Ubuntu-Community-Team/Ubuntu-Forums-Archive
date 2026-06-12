---
title: "Xubuntu 18.04 On Dell 7204 Rugged Extreme Realtek ALC3226: Alsa wrong audio mapping"
date: 2018-07-23
forum: Multimedia Software
---

### Post by flori123321 on 2018-07-23
Hi,

so I experienced a strange behaviour with Alsa and my Realtek ALC3226:

1) My internal internal speakers don't work (Alsa: headphones muted, speakers at 100%). 

2) If I am plugging my headphones, they are working (Alsa: headphones at 100%, speakers muted).

3) When opening Alsa with no headphones plugged, I see headphones muted, speakers at 100%. 

4) Now, when I increase headphones to 100% in this setup, my speakers are working.

So obviously there is some mappign issue going on. I checked hdajackretask. The problem is: It seems like both headphone jack and speakers are mapped on the same pin. Anyone ever faced such behaviour?

Best,

Florian

---

### Post by slickymaster on 2018-07-23
*Thread moved to **Multimedia Software**.*

---

