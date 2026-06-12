---
title: "Problems with Sound in Flash 10"
date: 2010-06-09
forum: Multimedia Software
---

### Post by mcland on 2010-06-09
I like to listen to music on Pandora at work.  If I leave the window open overnight with the music paused, it won't play the next morning.  In fact, no sound will play from any flash application.  However, I can hear the system sounds.  To recover sounds in flash, I have to restart Firefox.

I have a USB sound card (on board card doesn't work with Ubuntu).  Could that be the problem, or is it a Flash/Firefox problem?  I'm running 9.10 with Flash 10 and Firefox 3.5.9.

---

### Post by Jinger on 2010-06-09
Have you tried using another browser?

---

### Post by lidex on 2010-06-09
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1412153]("http://ubuntuforums.org/showthread.php?t=1412153")

---

### Post by mcland on 2010-06-11
> **Jinger said:**
> Have you tried using another browser?
I tried Chrome last night, but I had the same problem.

---

### Post by mcland on 2010-06-14
I tried the info in that link, but I'm still having the same problem.  Any other ideas?

---

### Post by lovinglinux on 2010-06-28
> **mcland said:**
> I tried the info in that link, but I'm still having the same problem.  Any other ideas?

Try the following commands:

```
rm -fr ~/.pulse ~/.asound*
sudo rm /etc/asound.conf
```

Reboot, then go to "System >> Preferences >> Sound" and configure sound again.

---

