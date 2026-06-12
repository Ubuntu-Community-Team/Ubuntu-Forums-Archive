---
title: "No sound for youtube videos?"
date: 2008-12-05
forum: Multimedia Software
---

### Post by Refuge on 2008-12-05
I am having some extreme difficulty watching Youtube videos on Ubutnu 8.10. There is no sound what so ever, I have every volume control turned up full, my speakers are on, and the youtube video sound is all the way up and I have Flash 9.0.113.1 (or something like that) installed.

So why am I not hearing sound?

---

### Post by Northsider on 2008-12-05
Check this out, it worked for me.  I was haveing trouble with all flash related sounds.

[http://www.arsgeek.com/2007/11/27/how-to-fix-no-sound-with-flashfirefox-in-ubuntu-710-gutsy/](http://www.arsgeek.com/2007/11/27/how-to-fix-no-sound-with-flashfirefox-in-ubuntu-710-gutsy/)

---

### Post by Refuge on 2008-12-05
Thank you so much =D

Installed it and sound is now working again xD

---

### Post by psyke83 on 2008-12-05
Northsider & Refuge,

Don't install libflashsupport - I can't emphasize this enough. While it may enable audio for Flash, it's an obsolete method and it causes instability in Firefox.

See [bug #192888]("https://bugs.launchpad.net/bugs/192888") for more information.

The real solution is to configure PulseAudio properly - I recommend you take a look at my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

### Post by iphonegames on 2008-12-05
lol. Check my new [iphone games](http://www.iphonegames3g.com) site for iphone and ipod touch when you have time! :)

---

### Post by Northsider on 2008-12-07
Ok, thank psyke.  I'll try that, thought I haven't had any problems thus far.

---

### Post by L1GTN1NG on 2008-12-08
I have the same problem and I tried what you guys said and it still doesnt work for me. I installed ubuntu on my brother's laptop(same laptop) and he gets sound for  youtube videos, etc. However, I do get sound from non-flash videos.

---

