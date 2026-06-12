---
title: "Problem with PulseAudio and Diablo II"
date: 2009-01-29
forum: Multimedia Software
---

### Post by kentcb on 2009-01-29
Hi there,

I recently started playing Diablo II again, but this time inside WINE in Ubuntu. For the most part it works great (way faster than it ever was on Windows - almost too fast actually) but occasionally PulseAudio just stops working. No sound.

Now I can successfully get sound back by stopping and then continuing the PA process. However, to do this I need to get back to the desktop (I just hit Alt-F2 to bring up the run dialog - the only way I could find to get back).

Once I stop and continue PA my sound is back but Diablo won't go full screen again. I get nasty panels. Even if I set the panels to autohide they don't fully hide and Diablo doesn't take up all available space anyway.

Any tips or ideas on how I can work around this?

Thanks,
Kent

---

### Post by kentcb on 2009-02-02
I managed to work around the PA problems by configuring WINE to use the OSS driver rather than ALSA. Whilst this doesn't fix the actual problem (getting back to full screen seems impossible), it does avoid the need to get back to the Gnome UI in the first place, since audio no longer cuts out.

---

