---
title: "Thinliquidfilm"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by ceb0 on 2007-11-04
I've always used thinliquidfilm to encode and upload videos onto my ipod, and it has always worked well.  However, since upgrading to gutsy, the progress bar no longer seems to work.  It does still encode, and transfer no problems, but I would like to get the progress bar back.

This post on the thinliquidfilm site discusses a change to the source code to bring back the progress bar, however it's a bit vague and although I tried, it didn't work for  me.

[http://thinliquidfilm.org/forum/viewtopic.php?t=59](http://thinliquidfilm.org/forum/viewtopic.php?t=59)

Does anyone have a progress bar on their thinliquidfilm?  If so, how did you manage it.  I would post to the thinliquidfilm forum but it seems to be mainly spam these days.  Thanks for any help.

---

### Post by philidox on 2007-11-10
We'll mine was not encoding or showing the bar.  I had to go to the software sources.  System>>Administration>>Software Sources.  Then I went to the "Third-Party Software" Tab and uncheck the medibuntu repositories([http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/)) along with all the fiesty repos, I figured I did not need them anymore.  Maybe unchecking all the fiesty repos was a foolish mistake but removing the medibuntu repos was the right thing.  Everything is back to normal for me.

---

