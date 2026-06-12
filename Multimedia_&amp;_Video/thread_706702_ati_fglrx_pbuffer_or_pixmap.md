---
title: "ati fglrx pbuffer or pixmap"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by warpino on 2008-02-24
HI everyone,

I'm an ubuntu newbie and have no experience of OpenGL at all. I just installed the latest ATI drivers (catalyst 8.02) for my ATI Mobility Radeon 9700. Everything seems to work fine - I don't really care about fancy desktop fx like compiz or beryl. By the way, compiz works fine to me but I hate the "slow scrolling" bug in firefox and pdf documents when desktop effects are activated (if anyone solved that issue please let me know).

THe real matter is... I'm using a piece of software for numerical modelling which, when using fglrx drivers, asks me to reconfigure the system in order to "allow OpenGL rendering to a pixmap or Pbuffer".

Is there any way to fix it?

Thank you very much for any help or suggestions,

w.

---

### Post by Resonance378 on 2008-03-13
Warpino I thought I'd reply about your OpenGL pbuffer issue.

From what I've gathered over the last 2 weeks it sounds like pbuffer support is not functional in the Catalyst 8 series driver and it was in the older drivers although it was very buggy.

I've been all over the net with google search tracking down ATI and Pbuffers, even opened up a bug report with the Wine crew (which is how I eventually found out about pbuffers in the 1st place.)

Long story short - it's a feature that looks like it is not currently supported or support has been removed in the Catalyst 8 series drivers.

---

### Post by warpino on 2008-03-13
thanks very much for your post Resonance...

let's wait for news form the amd-ati staff!

Bye.

---

