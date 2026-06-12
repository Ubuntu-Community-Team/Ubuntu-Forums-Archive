---
title: "GeForce 2 Go drivers"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by AdventHorizon on 2007-03-26
I'm a linux newbie, and on top of that I'm dumb enough to have upgraded to feisty already.

This morning there was a round of updates. I read through the changelogs and as I recall the nvidia driver update only said it was a minor update to match the new kernel. Since I'm skeptical of anything nvidia related anymore (they have not once in 5 years, on windows or linux, provided me with decent drivers) I always read the changelogs.

Well, it seemed minor enough, so I updated. BIG mistake. Turns out that nvidia removed support for my video card from the latest drivers. Problem is, the legacy drivers don't work either. At least, they didn't two weeks ago when they last tried them (I've tried them twice now; once when I first installed Edgy and that last time was when I upgraded to Feisty). Both times they didn't work and I had to swap back to the standard drivers from the command line.

They haven't updated the legacy drivers in the last two weeks (their forums say they came out in December) so I'm not too hopeful those will work. What can I do? Is there a way to go back to the last drivers that worked, even though they were for the -12 kernel?

Like I said, I'm a newbie, and I'm still learning my way around the command line. Otherwise I'm sure I'd be exploring all over there for an answer. Help!

---

### Post by AdventHorizon on 2007-03-26
Did I say I was a newbie? Because I meant it.

Reconfiguring xserver did the trick. No idea if I have 3d acceleration though. How do you tell?

---

