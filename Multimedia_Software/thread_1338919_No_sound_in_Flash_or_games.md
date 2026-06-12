---
title: "No sound in Flash or games"
date: 2009-11-27
forum: Multimedia Software
---

### Post by maxmingus on 2009-11-27
Just upgraded to 9.10. Originally I had no sound, but was able to fix that in alsa Mixer by unchecking the "Audigy Analog/Digital output jack". Now I have sound from Amarock and Dragon player, but not Flash or Games. All the controls in alsa mixer are enabled and turned on full. There are 2 cards in my PC (an unused onboard sound chip and a soundblaster audigy. Both are recognized using an "aplay -l" command.

Anyone have a clue?

Thanks,
Max

---

### Post by maxmingus on 2009-11-27
FIXED.

Discovered that the problem was with PulseAudio. Went to Synaptic and installed the PulseAudio volume control. That enabled me to disable  the onboard sound chip (configuration tab) which made everything come through the sb audiology sound card.

Hope this helps someone down the road,
Max

---

