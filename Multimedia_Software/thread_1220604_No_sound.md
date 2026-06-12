---
title: "No sound"
date: 2009-07-23
forum: Multimedia Software
---

### Post by RedSingularity on 2009-07-23
I have just ran the upgrade to 9.04 and i lost my sound.  I have tried for a few hours now but cannot get it working.  Any ideas would be great.  Thanks.

---

### Post by scotty2 on 2009-07-23
Do you have (or can you load) Alsa Mixer?  After an upgrade to 9.04, I found several of the speaker and microphone volume sliders were set to minimum.  This is easy to see and change in Alsa Mixer.

---

### Post by RedSingularity on 2009-07-23
I just checked; Everything is fine with volume and mic.

---

### Post by RedSingularity on 2009-07-23
I have found that OSS works but it will nlot play sounds in firefox when this is enabled.  When sound preferences are set to auto detect or ALSA i get nothing at all.

---

### Post by RedSingularity on 2009-07-23
Oh nevermind, i got it.  There was a conflict with pulseaudio.  All i had to do was remove it from the system through "autoremove".

---

