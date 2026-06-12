---
title: "No sound with flash videos"
date: 2008-11-23
forum: Multimedia Software
---

### Post by kanesoban on 2008-11-23
Helo,

altough, i have flashplayer 10 installed via synaptic, i don't have sound in flash videos. I tried looking for a solution in these forums, and i also tried to solve the problem by following this guide
[http://ubuntuforums.org/showthread.php?t=766683&highlight=sound+flash](http://ubuntuforums.org/showthread.php?t=766683&highlight=sound+flash)
but i still have no sound with flash.

---

### Post by ipburbank on 2008-11-23
There are often sound issues, so try closing everyhing, then after half a minute open the web browser again.

---

### Post by psyke83 on 2008-11-23
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kanesoban on 2008-11-23
Ah, i got it. That guide helped me. More precisely, this command:
pkill pulseaudio && sleep 2 && pulseaudio -vv

This showed, that i wasn't in the group of pulse-rt, so i couldn't use puleaudio. As soon as i put myself in the group.. i got sound for everything. 

The one thing i don't get is, why the heck an administrator is by default not able to use the sound system ?

---

### Post by psyke83 on 2008-11-24
> **kanesoban said:**
> Ah, i got it. That guide helped me. More precisely, this command:
pkill pulseaudio && sleep 2 && pulseaudio -vv

This showed, that i wasn't in the group of pulse-rt, so i couldn't use puleaudio. As soon as i put myself in the group.. i got sound for everything. 

The one thing i don't get is, why the heck an administrator is by default not able to use the sound system ?

The pulse-rt group is only for allowing realtime scheduling (and PolicyKit still denies access when you're a member) - that probably didn't solve your problem. Something else in the guide fixed your issue ;).

---

### Post by kanesoban on 2008-11-27
Well, turns out, it didn't really solve it. Most of the time, only totem player has sound. BUT, if i "killall pulseaudio", then everything else (like rhytmbox, and flash videos) has sound too.

---

