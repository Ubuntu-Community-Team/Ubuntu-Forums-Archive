---
title: "Update nvidia drivers to 1.90.53"
date: 2010-01-03
forum: Mythbuntu
---

### Post by crispen on 2010-01-03
Folks- I just installed a mythbuntu frontend on an IONITX-C-U currently running nvidia version 1.85 . I would like to upgrade my Nvidia video drivers to version 1.90.53 to take advantage of the overscan feature. When I run Update manager or proprietary driver manager the system tells me there aren't updates available. I have a combo frontend/backend running mythbuntu that has version 1.90.53- I must have missed something somewhere. Can anyone point me in the right direction?

Thanks

---

### Post by superm1 on 2010-01-03
Activate auto-builds at [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds).  Those builds are compatible with the 190 drivers, and the 190 drivers are on the auto-builds repo too.

---

### Post by yonkiman on 2010-01-04
> **superm1 said:**
> Activate auto-builds at [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds).  Those builds are compatible with the 190 drivers, and the 190 drivers are on the auto-builds repo too.

It seems like there are several "repo" choices (forgive me if I screw up the terminology):

1) Whatever we get by default when we install Mythbuntu
2) "stable/-fixes" 
3) "trunk"
4) Third-party (Jean-Yves Avenard's, for example)	

My questions are:
[LIST]
[*]Are 1 and 2 the same thing?
[*]To get the 190 driver, do we need to choose 2 or 3?
[*]I will of course back up my disk before I enable the autobuilds, but what are the relative risks that...
[LIST]
[*]...enabling autobuilds alone may break my 9.10/0.22 install immediately?
[*]...recent (not yet widely-tested) code changes may break my install after some update in the future?
[/LIST]
[*]#4 is appealing (let Jean-Yves do all the hard work :-)) - it has all the features I'd like, but I believe it's Myth 0.21-only.  (Not that there's anything wrong with that, I just don't want to go through the hassle of downgrading my database - migrating my database is where I seem to run into the most problems.)
[/LIST]

Any thoughts/comments?

---

### Post by superm1 on 2010-01-05
So some of this should be answered hopefully in the FAQ, but i'll  answer your questions directly and try to update the FAQ to clarify any points that weren't.
> **yonkiman said:**
> It seems like there are several "repo" choices (forgive me if I screw up the terminology):

1) Whatever we get by default when we install Mythbuntu
2) "stable/-fixes" 
3) "trunk"
4) Third-party (Jean-Yves Avenard's, for example)	

My questions are:
[*]Are 1 and 2 the same thing?

By default (1) you get a snapshot of -fixes when Ubuntu/Mythbuntu launched.  (2) are updated builds of these.  Same basic packaging, with any updates.

> 
[*]To get the 190 driver, do we need to choose 2 or 3?

It's on both right now.  I'd stay away from (3) unless you want to do development or testing of that stuff though.

> 
[*]I will of course back up my disk before I enable the autobuilds, but what are the relative risks that...
[*]...enabling autobuilds alone may break my 9.10/0.22 install immediately?

Not too likely to break things.  A lot of us are running this stuff because it's easier to debug bugs upstream with it.
> 
[*]...recent (not yet widely-tested) code changes may break my install after some update in the future?

The changes going onto -fixes are tested and backported from trunk.  Not too likely to break your stuff.
> 
[*]#4 is appealing (let Jean-Yves do all the hard work :-)) - it has all the features I'd like, but I believe it's Myth 0.21-only.  (Not that there's anything wrong with that, I just don't want to go through the hassle of downgrading my database - migrating my database is where I seem to run into the most problems.)

Any thoughts/comments?
(4) is the same basic thing as what we have on (2) right now.  jya might be able to comment on his delta there.  He's actually one of the maintainers now in debian for libvdpau which is used for enabling the -190 drivers on both of our repos.

---

