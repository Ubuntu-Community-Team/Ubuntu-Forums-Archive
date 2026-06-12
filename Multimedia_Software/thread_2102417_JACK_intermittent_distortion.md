---
title: "JACK: intermittent distortion"
date: 2013-01-07
forum: Multimedia Software
---

### Post by scyntl on 2013-01-07
Apologies for posting yet-another JACK-related problem! I appreciate any ideas:

I'm running Ubuntu 12.10 , and when I start JACK, everything seems okay.* The sound is fine for a few minutes, but then the INPUT SOUND suddenly gets really crappy (weak and unbearably  distorted) for a few minutes, then fine, then bad. . . If I turn down the frames/period to something like 64, the intervals of good and bad get shorter. If I open Patchage  and change the number of frames, the sound quality is okay for another few minutes.

This symptom occurs with both my external and internal sound-cards.

I also get a lot of xruns*. So I opened up the gnome system monitor, but I'm only using a quarter of my physical resources. (Another problem: I thought I'd try increasing the priority of JACK-related process, but when I try to do this in system monitor, it says, "permission denied." Typing "gksu gnome-system-monitor" or even just "gnome-system-monitor" into the terminal does not open the gnome system monitor.)

*When I say I get lots of x-runs, I mean compared to running at the same settings in Ubuntu 11.10 on my other laptop that is 6 years old.

So I'm thinking about installing 11.10 and seeing if that works. Any better ideas?

---

