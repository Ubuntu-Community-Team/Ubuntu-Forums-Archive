---
title: "black screen with aticonfig powerstate"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by morgengenuss on 2006-06-27
hi everyone.

after i found out that my laptop was boiling because of the ati x1400 powerstate i put "aticonfig --set-powerstate=1" into startup.
since this doesn't seem to be controlled automatically (something like autothrottling for cpu) i created a launcher on my desktop with the command "aticonfig --set-powerstate=3" that i would run before playing games that need some gpu-support.
but actually this launcher is giving me blackscreens in approximately 3 out of 4 times. if i run it from shell there doesn't seem to be a big problem, but i would like to switch powerstates without having to go to the shell first each time...

any ideas why the launcher doesn't work properly (is there any log that could help me except from /var/log/messages?) or how to work around this in some other way?

---

