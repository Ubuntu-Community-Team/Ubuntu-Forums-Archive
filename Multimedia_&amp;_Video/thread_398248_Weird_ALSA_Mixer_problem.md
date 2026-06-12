---
title: "Weird ALSA Mixer problem"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by Maxxarcade on 2007-03-31
I have two Sound Blaster Live cards in the same system running 6.10, for MIDI use.  Both work fine, however only one can be affected by ALSA mixer, regardless of which device is selected.

Sometimes I will try to move sliders in the mixer, and they will act funny, snap back to where they were when I move the mouse off of them, etc.  A system reboot usually fixes this, but I can still only control one of the cards.  I need to be able to adjust gain and Bass/Treble for the other card, but it won't let me.  I can change devices, but the sliders stay where they were, and don't affect the other card at all.

Any idea what to check?  I'm fairly new to Linux; this system is for dedicated MIDI use only so I don't play around with it too often.

---

### Post by Maxxarcade on 2007-04-01
Any ideas?  This is the last thing stopping me from having a fully working system :confused:

---

### Post by Maxxarcade on 2007-04-15
Fixed it... Apparently the mixer does not like having two identical sound cards in the system.  Changed one out for an Audigy, and everything works great now.  At first I had so sound from the Audigy, but I discovered that I have to uncheck the Digital/Analog output jack option for this card, and leave it checked for the Live.

---

