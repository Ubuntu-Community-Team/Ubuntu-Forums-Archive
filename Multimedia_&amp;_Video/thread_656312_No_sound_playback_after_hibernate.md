---
title: "No sound playback after hibernate?"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by dehughes on 2008-01-02
Hello all,

I came back to the computer this morning and noticed that it had "tried" to hibernate.  I just (re)installed 7.10 late last night, and had left the computer transferring files from my backup drive overnight.  This morning, it had tried to hibernate but failed, but all works as it should except that now I cannot get any sound out of it.  Flash plays, MP3 players churn away, but no sound comes out.  Where should I even start?

Thanks so much!

---

### Post by dehughes on 2008-01-02
Ahhh, figured it out.  "Hibernate" causes things to get screwy with ALSA mixer, so in went into the terminal, ran the mixer (alsamixer at the prompt...), unmuted "headphones" and turned PCM back up.  Bingo.  Sound.

Man, speaking as a new Ubuntu user and a longtime Windows user....Ubuntu is VERY cool, but still has some pretty obvious, common usage fixes that need to take place before people will really accept this. I mean, I've spent three days getting Ubuntu to "work properly", and lots of that was tinkering and re-installing, etc...  Plug and play has its benefits....

---

### Post by dehughes on 2008-01-02
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

That's the page to go to if you're having this same problem with sound after hibernate.... :)

---

