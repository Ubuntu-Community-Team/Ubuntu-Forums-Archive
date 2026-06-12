---
title: "enabled X-Fi driver, lost sound in flash/youtube"
date: 2009-05-19
forum: Multimedia Software
---

### Post by zapporius on 2009-05-19
I have lost sound when watching youtube videos, and here is what I did in chronological order:

- I installed Kubuntu 9.04, and at first used my on-board sound chip (HDA Intel).
- I tried to install flash support for Konqueror, following different guides, but never got Konqueror to play videos on Youtube.
- then I installed Firefox, which worked with youtube quite nicely.
- after that I figure why not try to get my X-Fi working, installed the tarball from Creative support site and it worked perfectly, KDE recognized that I have loaded new driver and switched to it automagically. Amarok, movie playback, notifications, it all worked.

- However, when I watch youtube videos in firefox, I don't have sound anymore, my guess is that firefox/flash/XYZ is still using the HDA Intel. How do I make it use X-Fi instead? What backend (?) is flash using, gstreamer, xine? I'm at loss with all the buzzwords and I don't really have a clue whats doing what on my system anymore.

Pulseaudio? Phonon? Gstreamer? Xine? Help.


EDIT: Solved! "asoundconf set-default-card XFi" did the trick.

---

### Post by oldrocker99 on 2009-05-19
I think you have to go into your BIOS and disable the onboard sound chip. That should fix you right up.

:guitar:

---

