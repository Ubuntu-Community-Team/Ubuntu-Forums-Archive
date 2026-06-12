---
title: "[SOLVED] Amarok keeps crashing..."
date: 2008-07-14
forum: Multimedia Software
---

### Post by houbysoft.xf.cz on 2008-07-14
Hi all. I really like amarok, so I'm a little annoyed by this bug (?).
I have left amarok launched, and then I clicked on logout. So I think that maybe amarok was killed, but I'm not sure. But the problem is that now, always when I want to start amarok, it crashes, but crashes ALL THE SYSTEM, causing my computer to reset and restart.

I tried reinstalling amarok, still the same error.

Any suggestions?

---

### Post by Valsodar on 2008-07-14
Do this:
(note the time)
start amarok (wait to crash your system), use this command in termianl amarok > out.log
restart ubuntu
copy and paste logs here(found under system->administration->system log)
also copy and paste out.log (should be under your /home/<username>)

---

### Post by houbysoft.xf.cz on 2008-07-14
thanks for reply, I have done what you said, but unfortunately, my system crashes probably that fast that the out.log isn't flushed to disk or something, because after the system restart, it isn't there...
For the system log, I think that the location that you said to me is in ubuntu, I have xubuntu, there is no "administration" under system..
But I found something that looked like the system log :), /var/log/syslog (?), I've grep'd it for amarok, nothing found.

---

### Post by Valsodar on 2008-07-14
> **houbysoft.xf.cz said:**
> /var/log/syslog
Yes, the syslog could provide some information (and that is what I was looking for), also since your system is crashing probably it wont be an amarok problem (but it might be that amarok triggers it) so that amarok wont be in the log, check the end of the log for suspicious messages before you boot up and post them here.

---

### Post by houbysoft.xf.cz on 2008-07-14
Hi, thanks for your help, but I managed to solve it myself finally :) for those who might be experiencing the same problem, just reinstall amarok, but not with sudo apt-get remove as I have done previously, use sudo apt-get purge instead.

---

### Post by Valsodar on 2008-07-14
So your problem was with the config files. Please mark this thread as solved. And Happy Amaroking to you too. (Also note that installing amarok from source you can get more features, like mysql db, ipod support, other player support)

---

### Post by houbysoft.xf.cz on 2008-07-15
Ok, marked. Thanx :)

---

