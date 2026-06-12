---
title: "programs show sound playing, but no sound is outputted"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by forumguy on 2006-06-17
I am using an hp dv8000 laptop that uses hda-intel audio; sound was originally playing, but I couldn't get the volume very high (I could increase PCM, but at max, it makes the sound crackle)

I decided to download the latest alsa drivers (1.0.11) and compile/install them myself; i also compiled/installed the alsa-lib 1.0.11 and alsa-plugins 1.0.11; after restarting, all programs say that sound is being played, but I can no longer hear anything (i've tried with amarok, with KDE itself, and even mplayer on the command line). And all sound settings are maxed out (from KDE sound control and from alsamixer)

i'm thinking I might have accidentally overwritten or conflicted with an ubuntu package... what might be wrong and what packages must i reinstall in order to revert these changes?

Thanks in advance!

---

### Post by forumguy on 2006-06-17
awesome, i think i got it

my manual alsa-lib install conflicted with the ubuntu libasound package; i uninstalled alsa-lib and alsa-plugins with make uninstall, then reinstalled the libasound package from synaptic

sound works, but it's still very soft... has anyone been able to get volume very high with intel hda audio?

---

