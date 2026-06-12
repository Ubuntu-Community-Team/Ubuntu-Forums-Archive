---
title: "Microphone works but won't display in sound settings"
date: 2012-11-14
forum: Multimedia Software
---

### Post by mjarret on 2012-11-14
Hi all --

I just got a "new" computer that, to the best of my knowledge, is identical to my old computer. (Apparently laptops don't survive being stepped on.) Anyway, I used to have no problems with audio and now stuff is a bit strange.

I believe the sound card is realtek alc269. 

Anyway, I added the line: 
options snd-hda-intel model=auto (

to alsa-base.conf and cranked up the mic settings in alsamixer and it works perfectly fine with soundrecorder, skype, and anything else. Nonetheless, the damned mic won't display in Ubuntu's Sound Settings. 

Any ideas on what could be going wrong? I'd like to be able to control mic volume without firing up the command line or alsamixergui.

---

