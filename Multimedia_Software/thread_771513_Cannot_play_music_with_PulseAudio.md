---
title: "Cannot play music with PulseAudio"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Aikon- on 2008-04-27
I use Music Player Daemon (MPD) for playing my music, and have since early Gutsy days. It ran perfectly smoothly under Gutsy. With Hardy, not so much.

The first issue I had was that MPD would consume ~25% CPU after changing tracks. This appears to have been fixed with advice from [here](http://ubuntuforums.org/showthread.php?p=4816924).

Now, however, I have another issue. It appears that PulseAudio is user-based, which means I need to be logged in with X running? This means that if I need to restart X for some reason, my music cuts out on me. One of the reasons I use MPD is that I can continue listening to music while I restart X, or work in a terminal, or w/e.

Is there any way to get around this so that MPD can play music regardless of the state of my computer? Once the initial boot is finished, if MPD receives a signal to play, it should be able to start immediately, without having to wait for GDM, X, or anything else :(

-Aikon

---

### Post by &#12465;&#12452;&#12488; on 2008-04-27
You can set pulseaudio up to start without/before X server.

---

### Post by Aikon- on 2008-04-27
> **&#12465 said:**
> You can set pulseaudio up to start without/before X server.

How might I go about doing this? Do you happen to have any links to some guides or more information?

---

