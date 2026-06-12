---
title: "[SOLVED] Sound glitch"
date: 2008-09-25
forum: Multimedia Software
---

### Post by Truman Davis on 2008-09-25
I've had a problem whenever I use linux, a long time ago when I first used Ubuntu I found that once a youtube video had finished playing, the sound from the last second would loop uncontrollably, closing firefox did not help. I then started to experience it when watching videos or listening to music, logging out would also fail to fix it. After a while I got sick of it and assumed it was an ubuntu bug and switched to fedora, but I also encountered this problem there with increased frequency.

I've now switched back to ubuntu and i'm running it with wubi (alongside my windows installation) and I once again encountered this terror bug. Ending the process called PulseAudio will stop the sound but the looping will continue as soon as it's started again.

I've searched the net but can't find anyone else with this problem. Any ideas on how to fix this?

---

### Post by Mattlock on 2008-09-25
Everything up to date? Firefox, the media players etc? I had the same issue for a while but it went away once I did so.

---

### Post by Truman Davis on 2008-09-25
Yep, all up to date. But this glitch can occur wherever sound is played, I was once changing my login sound and it happened.

---

### Post by Bakon Jarser on 2008-09-25
Sounds like it is probably a pulseaudio bug.  You could try upgrading to the new version of pulseaudio.  Also Ubuntu 8.10 will be shipping with a newer version of pulseaudio in late October.

You could also try this.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Truman Davis on 2008-09-25
This seems to have fixed it. Thanks for the speedy response!

---

