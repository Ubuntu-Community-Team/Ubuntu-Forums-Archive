---
title: "Crackling in Rosegarden but not Ardour"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by eric71 on 2006-10-30
I've been using Ardour and Rosegarden to record recently in Edgy.  I have mostly been recording audio only but have been playing with midi in Rosegarden and really like the program's interface as a whole.  I've got Jack set up fine.  In Ardour I get great sound quality.  When I record audio with rosegarden i get static or crackling, even though I'm not clipping.  It also occurs for DSSI synth plugins (which also require jack to be running).  Is this a jack problem with Rosegarden, or is Rosegarden just so much more resource heavy than Ardour that it's a CPU or memory issue? Anyone get similar problems? I've got a Fujitsu laptop with 1.6 mhtz Pentium M and 500 megs of memory and an onboard soundcard.

Thanks,

Eric

---

### Post by eric71 on 2006-12-04
Just an update on this.  After playing around for a while the other day, I realized this was all due to having selected to use 16 bit wav files instead of 32 in Rosegarden.  Switching back to 32 bit made all the difference.

Eric

---

