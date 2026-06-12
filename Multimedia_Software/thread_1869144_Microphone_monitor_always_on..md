---
title: "Microphone monitor always on."
date: 2011-10-25
forum: Multimedia Software
---

### Post by luquino on 2011-10-25
I recently assembled a small pc for my son, using an AsRock MoBo, socket AMD 2+, with an integrated sound card 
Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2).

The mic is plugged into the sound card, and even if I** mute the mic and the input monitors** from Pavucontrol, I always listen my voice from the speakers.
I suppose there is an HW monitor switched on, but I can't understand how to switch it off.
From Alsamixer I only see the "sliders" and no switches to operate.
Any idea?

---

### Post by luquino on 2011-10-26
sorry for the bump... :oops:

---

### Post by luquino on 2011-10-28
OK, problem fixed.
I removed Pulseaudio and everything is working fine.
Even I find that cpu works much less than before: with nothing to do both core stay between 3 and 5 %, before the average was 10 - 14 %.

---

