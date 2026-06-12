---
title: "No Input Sound On XPsound XP203 USB External Sound Card In Ubuntu 10.04"
date: 2011-01-18
forum: Multimedia Software
---

### Post by muffinman on 2011-01-18
I have a XPsound XP203 USB external sound card (See attached manual for info) which Ubuntu detects (See Sound Pref Hardware.png) & produces a sound output fine. However when connecting a device such as a record player (Which is it's primary use because it has a preamp built in), MP3 player, etc, no input sound is detected. This is currently connected to laptop which has it's own sound input which work fine (See Sound Pref Input Laptop.png. See input level changes) but with XP203 input level remain unchanged (See Sound Pref Input XP203.png). Have tried different profile settings under the hardware tab & input tab but no change. Doesn't matter which computer it's connected to I.E PC or laptop. Have also tried device on Ubuntu 9.10, 10.04 & 10.10 but fault persists. Any help would be fantastic. Thank you in advance :).

---

### Post by muffinman on 2011-03-14
Anyone???

---

### Post by muffinman on 2011-03-31
Fix it :). Ran alsamixer via the terminal & changed the PCM capture source from Mic to Line (See attached screen shot). A bit strange because you can make the same change in Sound Preferences / Input tab & the fault persists.If the default was set to Line in alsamixer it probably would be fine. Cheers.

---

