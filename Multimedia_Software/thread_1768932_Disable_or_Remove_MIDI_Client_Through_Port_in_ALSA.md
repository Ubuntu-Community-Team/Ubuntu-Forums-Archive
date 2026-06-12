---
title: "Disable or Remove MIDI Client Through Port in ALSA"
date: 2011-05-27
forum: Multimedia Software
---

### Post by magicalplug on 2011-05-27
I'm using SEQ24. It's great, but everytime I create a new MIDI clip in it, it defaults to my first MIDI port.

This is

14:0 Client Through MIDI Port

Is there anyway I can disable this unneeded ALSA MIDI port, so that the only MIDI port available for SEQ24 to use, and thus use by default, is my real hardware one?

Either that or a way to reorder or renumber the ALSA MIDI ports? Any help much appreciated.

---

### Post by magicalplug on 2011-05-27
I've tried using aconnect to connect the MIDI Through Port to itself exclusively, hoping this would stop it appearing to SEQ24 but no such luck. Can anyone help me with this? Cheers.

---

### Post by armarpc on 2011-12-07
Hi, 

This worked for me:

$ sudo rmmod snd_seq_dummy

---

