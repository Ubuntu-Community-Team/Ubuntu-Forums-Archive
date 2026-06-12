---
title: "No sound: Pulseaudio connecting to HDA digital, not analogue"
date: 2011-03-04
forum: Multimedia Software
---

### Post by halfbeing on 2011-03-04
Recently a problem started occurring intermittently. Now it is occurring all the time.

I have a Conexant HDA sound card. When PulseAudio starts it connects automatically to the digital sound, not the analogue. Analogue is what I want.

What used to work was that I would simply stop kdm and then do an "rmmod snd-hda-intel" followed by a "modprobe snd-hda-intel" and it would fix itself. Now I get digital all the time, which means I have no sound.

Does anyone know what is going on here?

Thanks.

---

