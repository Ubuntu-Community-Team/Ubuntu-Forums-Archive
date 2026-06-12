---
title: "Vid quality better in MPC (Windows), than MPlayer (Linux)..."
date: 2010-05-04
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-05-04
I think it's only a configuration setting (cache maybe?), and I'm not knowing which one or how - need to know what the RANGES are first...

But the problem is that all my videos look better in 32bit XP playing in Media Player Classic, than playing in MPlayer Movie Player, with x64 Hardy. CPU is 3x core, 2G memsticks, so hardware isn't the problem I don't think.

What configuration setting should I start with?

---

### Post by Judo on 2010-05-04
The "better" quality is most likely due to FFDShow's filters.  FFDShow has some fantastic filters in it that can seemingly increase quality.  Although, I don't like them due to their side effects.  Sure, they can removes artifacts, but they also remove detail and sometimes cause artifacts of their own.

That said, mplayer has its own filters.  They can be enabled with command line options or in whatever options menu you have, if you're using an MPlayer frontend like SMPlayer.

(I should mention that I'm making a lot of assumptions, but this is very likely to be the reason.)

---

