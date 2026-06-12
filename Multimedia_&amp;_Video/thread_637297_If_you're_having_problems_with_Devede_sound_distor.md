---
title: "If you're having problems with Devede sound distortion...."
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by MrKlean on 2007-12-10
On Feisty or Gutsy.....try this.. it worked for me. I had to use an old version of mplayer until I finally found this. I hope it works for you like it did for me !! It's an upgraded mplayer and mencoder that hasn't been mentioned for some reason. This is from a bug report I've been following on this problem.

Go to "System->Administration->Software Sources". It will ask you the password.

Now, in that new tool, go to the tab "Third party software", check the
option "Unsupported updates (gutsy-backports)" and close the window with
the "Close" button (don't use the X in the window bar). It will ask you
to reload the packages list: do it.

Now go to "System->Administration->Synaptic" and install the
Mplayer/Mencoder packages, or you can do all the updates.

When you have finished, you can uncheck the "Unsupported updates
(gusty-backports)" option to avoid the update manager to replace other
packages. Or you can leave it and have your system with the really last
versions of the packages (remember that in Backports are always newer
versions than in the official distribution, but they aren't officially
supported.

---

### Post by jettapup on 2007-12-31
Worked exactly as claimed: 
Had problem in 7.04 and up graded to 7.10 and problem followed.

If there is a problem in Mplayer/memcorder, and the back-ports fixed it, who determines when the packages get up graded??

Still damb new to this Ubuntu thing but actually being able to get something to work is a GREAT moral booster.

Thanks Again to MrKlean

Jettapup

---

