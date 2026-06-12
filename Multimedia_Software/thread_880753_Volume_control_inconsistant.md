---
title: "Volume control inconsistant"
date: 2008-08-05
forum: Multimedia Software
---

### Post by plush_cthulhu on 2008-08-05
hello,

I'm having the exact same problem here (with same sound card) as described here:
[http://ubuntuforums.org/showthread.php?t=715381](http://ubuntuforums.org/showthread.php?t=715381)

When trying to adjust the volume, the gnome mixer moves up and down in an erratic way (non-linear and unpredictable, unlocking Left and Right at random)

A friend of mine, who has a completely different (but also USB-connected) sound card has this problem too, leading me to believe this is a problem with all USB sound cards.

However, the command line based alsamixer works fine, so I've made a crappy workaround by putting

amixer --card 1 sset PCM,0 4dB+

and

amixer --card 1 sset PCM,0 4dB-

as 'command lines' in compizconfig and bound it to some keys on my keyboard.

This bug was also present in Gutsy and has been passed to Hardy. Is there anyone else who can reproduce this?

---

