---
title: "Tote gives error &quot;Failed to connect stream: Too large&quot;"
date: 2009-10-04
forum: Multimedia Software
---

### Post by luisjorge on 2009-10-04
Hello everyone! I just installed Ubuntu 9.10 beta, and I realized I can't play music files or videos. Totem gives the error "Failed to connect stream: Too large", but Banshee and VLC don't play these files either.
Does anyone know a way to solve this?

Thanks in advance!

---

### Post by advocate 21 on 2009-10-04
install gstreamer and whatever else it says it requires.
then maybe vlc/ banshee would work.

---

### Post by nspattak on 2009-10-29
I have the same problem and it still does not work. any ideas ?

---

### Post by migueletorres on 2009-11-13
Same issue here, with last update on Karmic...

Any recommendations?

---

### Post by neviander on 2009-11-20
I have the same problem, apparently it's a new 9.10 bug  [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/362423](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/362423)

Looks like I'll be booting windows to listen to mp3s until they get this fixed.  I don't have the skills to work on bugs like this.

---

### Post by neviander on 2009-12-05
Looks like they fixed it with the latest round of updates, sweet!  :D

---

### Post by cinnabarin on 2010-06-30
I have the same problem, but in mine, I get the same message when i try to listen to a song from within Frostwire. After this, I cannot listen to an mp3 from another program either. This resolves by restarting, but comes back if I try Frostwire again. Can somebody help on this ?

---

### Post by sebasutp on 2010-12-04
> **cinnabarin said:**
> I have the same problem, but in mine, I get the same message when i try to listen to a song from within Frostwire. After this, I cannot listen to an mp3 from another program either. This resolves by restarting, but comes back if I try Frostwire again. Can somebody help on this ?

I had the same problem, it seems that Frostwire has a bug. As a tip, you don't have to restart. If you kill frostwire, MP3 should work again.

---

### Post by m3asmi on 2012-04-23
you must just reload the alsa process
using command 
```
~$sudo alsa force-reload
```

---

