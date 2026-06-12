---
title: "[SOLVED] Drivers detected, everything unmuted, no sound."
date: 2008-12-16
forum: Multimedia Software
---

### Post by ShadowWraith on 2008-12-16
I have just installed a Sound Blaster Live! card into my system, which I wish to use instead of my integrated VIA8237. Ubuntu and alsa detect it, and I unmuted all channels in alsa mixer, as well as set the card to the top priority in the sound settings, but sound still goes through my VIA and not through the Sound Blaster. Please advise!

---

### Post by ShadowWraith on 2008-12-16
Solved it by disabling integrated audio in BIOS and muting Analog/Digital output Jack in Alsa mixer.

---

