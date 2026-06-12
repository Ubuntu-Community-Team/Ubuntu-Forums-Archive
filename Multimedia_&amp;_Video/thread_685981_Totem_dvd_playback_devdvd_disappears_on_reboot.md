---
title: "Totem dvd playback: /dev/dvd disappears on reboot"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by ady.littlefella on 2008-02-02
When trying to play a dvd in Totem I got an error message to the effect that '/dev/dvd' could not be found.  My dvd drive was 'dev/scd0' and so I created a symbolic link to 'dev/scd0' which I named 'dev/dvd'.  This worked fine and Totem played dvd's fine (I am using Totem - Xine by the way).

However, after a reboot the symbolic link I created has disappeared and dvd playback does not work.  Creating the link again fixes the problem.

Any ideas why this is happening and the best permanent fix?

---

