---
title: "Xine Problem?"
date: 2008-07-18
forum: Multimedia Software
---

### Post by haelen on 2008-07-18
Suddenly Amarok is crashing when I open it, and when I try to play an mp3 using Movie Player, that crashes too.

When I place my mouse arrow over an mp3 file, it no longer plays.

I suspect the problem might be something to do with xine, as I can play mp3's in Miro - which uses Gstreamer.

Any clues please?

TIA,
Tim

---

### Post by thedaylights on 2008-07-26
Bump.

I'm having similar problems. Amarok didn't work, then did, now doesn't. It spends a lot of time frozen and greyed out, thinking about things. I think it's xine because Mplayer is also unable to play mp3 files.

EDIT:
I found some help [here]("http://ubuntuforums.org/showthread.php?t=792022"). I went to Settings --> Configure Amarok --> Engine and changed "output plugin" dropdown to Alsa. It's working at the moment.

---

### Post by Yellow Pasque on 2008-07-26
If thedaylights' suggestion doesn't work, try starting amarok from the terminal to see what errors it throws.

---

