---
title: "[SOLVED] Sound coming from internal speaker instead of external speakers"
date: 2008-12-01
forum: Multimedia Software
---

### Post by pinkunicorn on 2008-12-01
I've installed Intrepid on a desktop machine and it generally works, but I'm having problems with the sound. The sound does play, but it comes from a speaker built into the desktop machine and thus sound rather bad. Since I have external speakers connected to the machine, I'd like the sound to be played there instead.

I haven't been able to find anywhere suitable to configure this, though. In the System->Administration->Sound control panel I have a few select boxes for where to play sound for various types of events.

Originally, these were set to "Detect automatically" (or something similar; I'm reverse-translating all menu items from Swedish). I've also tried "PulseAudio Sound Server" and "ALSA - Advanced Linux Sound Architecture" with the same result (i.e. sound from the internal speaker).

If I select "Intel ICH5 with AD1981 Intel ICH5 (ALSA)", the sound test thingy gives me an error message that says "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Couldn't open sound device for playing."

If I select "Intel ICH5 with AD1981 Intel ICH5 - IEC958 (ALSA)", the sound test thingy doesn't give any error message, but not any sound either.

My external speakers are connected with the green plug to the green socket on the sound card. If I connect my mp3 player to the speaker plug I hear sound, so the speakers as such are OK.

How can I get sound playing via my external speakers instead of the internal one?

---

### Post by ajgreeny on 2008-12-01
Double click on your volume icon in the panel and make sure firstly that all the sliders you want are showing by using edit in 8.04, or Preferences at the bottom of the window in 8.10 (I think, I'm on 8.04 atm).  Mute the system/case speaker if you want and make sure other levels are all OK.  If that doesn't work I'm not sure what else to try.

---

### Post by pinkunicorn on 2008-12-01
Ah, that does it. Thanks!

---

### Post by marcoahernandez on 2009-01-14
> **pinkunicorn said:**
> Ah, that does it. Thanks!

I tried what your have advised and works perfectly...aaahhh!!! al last a real solution, I have spent many horus figuring out what going on, but now I know...Thanks a lot for your post !!!

Best Regards.

---

### Post by OMIGHTY1 on 2009-02-11
Well, this certainly fixed my problem! Thanks a lot!!:mrgreen:

---

