---
title: "Getting two bt878-based cards to work"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by MistaED on 2007-09-06
Hello, I've got two bt878-based cards in my father's PC with ubuntu feisty, now I've followed some guides and it has been fairly easy to setup the one card but here's the trick: Both cards may be bt878/bttv-based, but one is analog and one is digital and they use different kinds of tuners.

The digital card gets detected automagically, and all I need to do is to modprobe dvb-bt8xx to finish the job, however the analog one can't autodetect the tuner properly so I need to set that one up manually somehow.

Now if I set settings to one card, the other card gets affected too. How can I separate the configuration between the two cards? This is a trick I've never been able to pull off as all the tutorials out there are sort of like a shotgun blast of "modprobe" if you know what I mean ;)

Cheers
-MistaED

---

