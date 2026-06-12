---
title: "FLAC playback in amarok 1.4 with jaunty"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Zaff on 2009-10-07
Hi, I've read about this problem in other forums but I've yet to find a solution. I apologize if this is already on this forum somewhere.

I have ubuntu Jaunty (9.04) at home with amarok 1.4 installed from the bogdanb repository ([http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html)).

Now I have flac files encoded with Sound Juicer. Those files work fine in Rythmbox as well as my amarok 1.4 install at work which is running on Hardy (8.04).

But in my Jaunty Amarok 1.4 install at home, amarok skips a few seconds in the beginning. It doesn't do this when I double click a song, however it does it when automatically starting a new song in a playlist.
It doesn't do it all the time and I've only noticed it a few days ago (it was fine before, maybe some upgrade screwed something up).

Can anyone tell me if there is a fix for this ?
I don't really want to use Amarok 2 yet (although I probably will eventually).
Thanks

---

### Post by s2n6 on 2009-10-08
add the following setting to  ~/.config/kde.org/Phonon-Xine.xine.conf

```
engine.decoder_priorities.flacdec:1
```

After rebooting, this solved the problem for me.

grtz

ref:[http://forum.kde.org/viewtopic.php?f=116&t=72794&start=10]("http://forum.kde.org/viewtopic.php?f=116&t=72794&start=10")

---

### Post by Zaff on 2009-10-08
> add the following setting to ~/.config/kde.org/Phonon-Xine.xine.conf

Code:

engine.decoder_priorities.flacdec:1

After rebooting, this solved the problem for me.

grtz

ref:[http://forum.kde.org/viewtopic.php?f...72794&start=10](http://forum.kde.org/viewtopic.php?f...72794&start=10)
I don't have this file, should I just create it ?
Thanks.

---

### Post by s2n6 on 2009-10-13
> **Zaff said:**
> I don't have this file, should I just create it ?
Thanks.
Sorry, I have no idea? Anyone?

---

### Post by ssri on 2009-11-12
ummm, you can try my guide

[http://ubuntuforums.org/showthread.php?t=1245938](http://ubuntuforums.org/showthread.php?t=1245938)

---

### Post by Zaff on 2009-11-13
Well so far everything seems fine in Karmis (I just upgraded last week), so I'm just gonna leave it like this, but thanks. If the problem reappears I'll try it (unless it's a jaunty only guide).
Thanks

---

