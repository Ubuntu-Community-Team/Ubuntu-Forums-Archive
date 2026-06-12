---
title: "Program Guide not visible"
date: 2008-11-05
forum: Mythbuntu
---

### Post by RockyMountain on 2008-11-05
Although there are similar posts already, none seem to be exactly the same as my problem, so I'll go ahead and start a new thread.

I've just set up a system with Mythbunu 8.10.  Previously tried 8.04.  I see exactly the same problem with both.

The problem is that if I pull up the program guide while viewing live TV, it flashes only briefly on the screen, and then the live program overwrites it.  It's not on the screen long enough to be able to read it.  Thereafter, it periodically flashes on the screen for a tiny fraction of a second and disappears again.

I'm using a Hauppauge PVR-500 card, Nvidia Gforce 7150/nForce 630 graphics card, and plain vanilla Mythbuntu 8.10 install.

There was a thread on this forum earlier which sounded like the same problem, but the proposed solution to that was (I think?) included in the 0.21.0+fixes package.  I'm using 0.21.0+fixes18722, which I beleive should already have that fix.  Which makes me think I'm seeing an unrelated problem.

I have already tried various permutations of:
  - Video Playback Profile (CPU--, Normal, High Quality, etc.)
  - Guide Shading Method (Solid, Alpha, Blender, etc.)

Is there any way to just have playback temporarily suspend while in the guide, and resume afterwards, so that playback won't keep overwriting the guide?

Thanks,
Derek.

---

### Post by RockyMountain on 2008-11-16
Just in case it helps anyone else out, here's what eventually solved this problem for me...  I downgraded my Nvidia graphics card drivers from 177 to 173.  Problem went away!

There must be multiple different root causes that cause this particular symptom, because others have reported that it goes away when you turn off the PVR-350 MPEG encoder, and other solved it with this patch:  [http://svn.mythtv.org/trac/attachment/ticket/4964/mythtv-pvr350-epg.patch](http://svn.mythtv.org/trac/attachment/ticket/4964/mythtv-pvr350-epg.patch).  Neither of these worked for me, but the Nvidia driver downgrade worked great.


Derek.

---

