---
title: "Garbled sound with multiple applications"
date: 2011-11-04
forum: Multimedia Software
---

### Post by Michael_3545 on 2011-11-04
I'm having an unusual issue with my sound, and I haven't been able to find anything similar with my trusty friend Google.  When two applications output sound, all sound becomes distorted and garbled.  One application works fine, such as VLC alone, but if more than one application outputs sound, everything becomes garbled.  The only thing I have done to the sound (to my knowledge) is installed linux-backports-modules-alsa-lucid-generic.  I doubt this is the problem as I installed it about a month ago with no issues.

I'm running Ubuntu 10.04 with kernel 2.6.32-34-generic, and whatever the default sound setup is.  (I think it is PulseAudio).

Thanks in advance for your help!

EDIT:  I just realized that this issue is only on my account.  Is there some way of reseting the sound preferences that won't wipe all my other settings?

EDIT 2: On IRC someone suggested that I should delete ~/.pulse, and that worked for a while, but then the problem returned.  Then, thinking it may have been a bad idea to delete PulseAudio's files while it was running, I logged out and deleted it again from a TTY.  The problem has not returned since then.

---

