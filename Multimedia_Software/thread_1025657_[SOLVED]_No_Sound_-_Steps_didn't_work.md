---
title: "[SOLVED] No Sound - Steps didn't work"
date: 2008-12-30
forum: Multimedia Software
---

### Post by luapekralc on 2008-12-30
Hi,

I have no system sounds (and can't play music). Not sure when this occurred since I have not had speakers connected to this computer for a few months, until last week.

Symptom is cannot get test tone, or system sounds, or play captured sounds from Audacity.

When I am recording with Audacity (1.3.4-beta), speakers play the sound being recorded, however if I try playing the recorded sound - nothing. 

I then attempted to test sound with the system/preferences/sound test, but no tone was heard. Likewise for playing system sounds.

Found the "Comprehensive Sound Problem" post, and followed steps 1 & 2 with success. Step 3 seemed to have a bad link, but step 4 did not produce sound. 

Ubuntu identifies the sound card as Ensoniq 1371.

Continuing, I removed and reinstalled the ALSA drivers. Appeared successful. Opened the alsamixer and found speaker and headphone was NOT muted.

I removed and reinstalled the medibuntu components. - No improvement.

I attempted to reinstall mplayer, but several dependencies gave me an error: "Not installable" - so I'm not sure the status of mplayer on my machine.

Not being completely sure that I had ever had sound (I usually have it turned off) I rebooted from the Ubuntu 8.04 LTS CD that I had burned before I upgraded. Sound worded fine! - preferences/sound played a test tone, and system sounds.

This tells me that that Ubuntu recognizes my system sound and can work correctly.

Would appreciate any suggestions to try to restore sound.

---

### Post by luapekralc on 2008-12-30
Followed some steps in another post by psyke83 and reinstalled PulseAudio, with patches for Hardy and it is now working.

Thanks.

---

