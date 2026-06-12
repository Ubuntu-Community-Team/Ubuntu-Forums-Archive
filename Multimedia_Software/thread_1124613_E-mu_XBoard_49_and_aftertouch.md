---
title: "E-mu XBoard 49 and aftertouch"
date: 2009-04-13
forum: Multimedia Software
---

### Post by billstei on 2009-04-13
I have an E-mu XBoard 49 MIDI keyboard that should produce aftertouch, but when I monitor it using kmidimon, I do not see any aftertouch messages.  On the XBoard I hit Edit, then B0, and it shows "on" for the aftertouch setting.  What am I missing here?  Is ALSA filtering it out?

---

### Post by billstei on 2009-04-13
I see now that I Read The Friendly Manual that the XBoard only does Channel Aftertouch, not Key Aftertouch.  Do I need to do anything special with kmidimon (or aseqdump) to see channel messages?

---

