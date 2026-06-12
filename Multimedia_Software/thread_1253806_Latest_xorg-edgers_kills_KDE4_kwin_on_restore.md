---
title: "Latest xorg-edgers kills KDE4 kwin on restore"
date: 2009-08-30
forum: Multimedia Software
---

### Post by tomchiverton on 2009-08-30
I'm using the xorg-edgers repo. to cure my Intel video hardware slowness.

Since the last mass update from it, when I restore from hibernate all the title bars in KDE4 are gone, though otherwise the windows function OK.

On a hunch, I swapped to the text console and tried to kill 'kwin'. It appeared to be hung because it needed '-KILL' to actually die.
Doing 'export DISPLAY=:0.0' then 'kwin' and swapping back to X brought the title bars are back.

Various kernels (including the one from xorg-edgers and the rc7 mainline (as slated for 9.10)) made no difference, so I think this must be a xorg-edgers problem.

Is anyone else seeing this ?

I can't see a mailing list run by xorg-edgers, unfortunately, or I'd be posting there :-)

---

### Post by tomchiverton on 2009-09-19
I've seen a flurry of xorg-edgers updates since this post, and although things haven't settled down, the current version I have works fine now.

Life on the edge, eh :-)

---

