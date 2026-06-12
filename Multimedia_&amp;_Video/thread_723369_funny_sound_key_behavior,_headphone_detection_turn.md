---
title: "funny sound key behavior, headphone detection turned off."
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by zoexii on 2008-03-13
Hello, I am experiencing the following problem:
Whenever I use the sound keys at the top of my keyboard (sound up, sound down, mute), headphone detection is turned off.  I can see this happen in alsamixer if I have it open in a terminal.  This makes it imposssible to use the sound keys to adjust volume while I'm trying to be quiet with headphones (a must while at the workplace).

I am runing Dapper on a PowerBook pismo (PPC), and am using fluxbox.  I have already checked ~/.fluxbox/keys and commented out the following: 
F3: Exec aumix -v +5
F4: Exec aumix -v -5

After restarting fluxbox, the keys still change the volume and still disable the headphone detection.  What other process(es) respond respond to the volume keys, and how do I disable them or change their behavior?

thanks, Zoe

---

