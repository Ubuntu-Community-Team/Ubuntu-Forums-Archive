---
title: "Mplayer - no video"
date: 2008-06-02
forum: Mythbuntu
---

### Post by Trollslayer on 2008-06-02
OK, I had things working using Mplayer to play back .mkvs and it was fine.
Now, without changing anything I'm aware of, there is no video.
Mplayer on it's own works perfectly, Mplayer from within MythTV you get sound and if you pause or stop it responds normally. The only problem is the MythTV screen stays there, no video.
Hardy Heron 8.04, MythTV 0.21, ATI graphics with restricted driver.
As I say, running Mplayer from the desktop is fine.

Found it - from the desktop it selected X11 video, the -vo xv had worked before but now it reported no video device found.
Chaned the [COLOR="Blue"]-vo xv[/COLOR] to [COLOR="blue"]-xv x11[/COLOR] and it's fine.
The ATI restricted driver is X11 BTW.

---

### Post by superm1 on 2008-06-02
> **Trollslayer said:**
> OK, I had things working using Mplayer to play back .mkvs and it was fine.
Now, without changing anything I'm aware of, there is no video.
Mplayer on it's own works perfectly, Mplayer from within MythTV you get sound and if you pause or stop it responds normally. The only problem is the MythTV screen stays there, no video.
Hardy Heron 8.04, MythTV 0.21, ATI graphics with restricted driver.
As I say, running Mplayer from the desktop is fine.

Found it - from the desktop it selected X11 video, the -vo xv had worked before but now it reported no video device found.
Chaned the [COLOR=Blue]-vo xv[/COLOR] to [COLOR=blue]-xv x11[/COLOR] and it's fine.
The ATI restricted driver is X11 BTW.
Turn on the VideoOverlay in your ATI driver.

aticonfig --help

should show you how to.  i don't know off hand.

---

