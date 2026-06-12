---
title: "Hulu playback is choppy"
date: 2012-02-02
forum: Multimedia Software
---

### Post by N00b-un-2 on 2012-02-02
Yes, this is probably yet another hulu post.  Hulu is absolutely unwatchable on 3 out of 4 computers in my house, the one that plays well is my netbook with intel GMA3150 so the issue is definitely a software problem, not a hardware problem.  My HTPC is the one I'm concerned about though.  It is a P4 3.06GHz with 1.5GB ram and an nVidia GT 430 graphics card.
It handles full 1080P blue ray rips with ease, It runs MythTV and XBMC without any issues.  Youtube videos play flawlessly even in full screen, but Hulu absolutely refuses to play well.  What could possibly be the problem?

---

### Post by N00b-un-2 on 2012-03-07
upgraded to a cheap core2duo.  the problem arises from lack of a second CPU thread or separate core.  couldn't even begin to guess why having a hyperthreaded 1.6GHz Atom processor outperforms a 3.06GHz P4 without hyperthreading but the issue with Hulu has been definitively determined to be dependent on the presence of a second CPU core, either real or virtual hyperthread.  I happened across a late model P4 chip with hyperthreading which did in fact address the problem, but the CPU cooler failed and cooked that processor.  It was time for an upgrade anyway...

---

