---
title: "[SOLVED] Odd sound issue: global configuration?"
date: 2008-11-24
forum: Multimedia Software
---

### Post by GepettoBR on 2008-11-24
Hello, all.

I had some trouble getting my ALC883 onboard sound to work, but eventually managed to fix it by compiling the latest ALSA packages from their website.

Now, both Totem and Rythmbox can play sound, but no other application can. Amarok, Mplayer, VLC, Firefox, all are unable to play back sound of any kind. Rather than each of them having its own unsolvable problem , it's more likely that there's a global setting somewhere that the two "default" players are ignoring for some reason.

Not even the system sound selector in System>Preferences>Sound works, so I really think that Rythmbox and Totem are the exception here, and not the rule.

All help is appreciated, and I apologize if I have omitted any important information. I'm new at this, so I don't really know what information qualifies as "important".

---

### Post by psyke83 on 2008-11-24
Your audio mixing problems are a result of a suboptimal PulseAudio setup. See here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by GepettoBR on 2008-11-25
Thank you. Thread marked as solved.

---

