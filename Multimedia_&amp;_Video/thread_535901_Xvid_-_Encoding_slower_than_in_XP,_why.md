---
title: "Xvid - Encoding slower than in XP, why?"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by Col-1023 on 2007-08-27
My system is a samprom 3000, 192 mb ram, unichrome pro graphics.

The software I use to encode my DVB TV captures (MPEG2) is avidemux 2.4 (Preview 2) in xp, and in ubuntu 7.04 I use avidemux 2.3.0 which I download with synaptic.

When encoding in xp, my system averages for 1st pass around 25 fps, and for 2nd pass around 6 fps.  In ubuntu 7.04 I average in 1st pass 9 fps, and 2 nd pass 2 fps.

The xvid settings in both cases are exactly the same, and the quality is equally as good, and in both cases avidemux had around 90% cpu usage, so no other compute intensive programs were running.

This is a huge drop in encoding performance, so I'm very interested in what the cause is, since the only obvious difference is that ubuntu has an older avidemux, but I would find it hard to believe that this could make that much difference.

Any help appreciated.

---

### Post by Col-1023 on 2007-08-29
I assume that my system is using VESA drivers for the graphics.

I raised the priority of avidemux from 0 to -6 to see if this would speed things up, but it's had no effect.

Does anyone have any ideas?

---

### Post by Col-1023 on 2007-08-30
After more searching I found this thread,

[http://ubuntuforums.org/showthread.php?t=415167&highlight=xvid+speed](http://ubuntuforums.org/showthread.php?t=415167&highlight=xvid+speed)

I enabled the proposed repositories and installed the new xvid4 package.

My encodes are now back to normal with 1st passes at around 25-30 fps, and 2nd pass at around 5-7 fps.

The new xvid module is supposed to be in universe, but this isn't currently the case, hence having to use the proposed repo.

---

### Post by chrome307 on 2007-08-30
Can you clarify the steps you've taken?

I attempted to follow the thread you mentioned but did not find the DEB package.

---

### Post by Col-1023 on 2007-08-30
I opened synaptic , went to the updates sections and ticked (checked) the Proposed Repositories.

Then synaptic reloaded and told me there were a bunch of updates, I declined all of them except the xvid update, I can't remember the exact filename, but it had xvid in it's title.

I then applied the update, synaptic did the rest and then finally I test avidemux on a short clip to make sure it worked, and it did.

After everything worked, I went back into synaptic and unticked the proposed repositories because except for this single update, I probably won't need that section again.

Hope this helps.

---

