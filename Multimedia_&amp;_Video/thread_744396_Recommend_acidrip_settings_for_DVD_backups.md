---
title: "Recommend acidrip settings for DVD backups?"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by radioraheem on 2008-04-03
I'm trying to use acidrip to copy my DVD collection and then burn it to cheaper DVD-R's for backup purposes (archive the original copies, basically).

I've tried a few different sets of options, and everytime I get a working AVI file with audio that is correctly in sync with the video.  But when I go to burn it to a dvd (I've been using tovid and the makemenu/makedvd terminal tools)  I end up with a playable DVD but the video is WAY out of sync from the audio.

Can anyone recommend a set of options for acidrip that is known to do a good job when being converted to a dvd burnable format?  Or am I missing a problem somewhere else in the chain of events?

Thanks for any help or insight!

---

### Post by xc3RnbFO8P on 2008-04-03
K9copy is easer to use, rip the dvd and it fits one 4.7 gb dvd.

---

### Post by aeiah on 2008-04-03
acidrip is for ripping and encoding in avi, and tovid is to take avi and encode it to dvd format. what you're doing is degrading the quality far more than is needed, and giving yourself and your cpu more work than is necessary. stuff like k9copy as mentioned takes the avi step out of the equation and is the kind of thing you should be using. just use acidrip to rip dvd files for storage and playback on your computer.

as for the audio sync problem, its something that tovid is probably causing, not acidrip. if you are wanting to convert from avi to dvd make sure you run your avi through the forceidx flag. this should get rid of sync problems:

```

mencoder -forceidx -oac copy -ovc copy input.avi -o output.avi
```

then run output.avi through tovid. if this solves the problem then you should be able to add it to the tovid script or write a small bash / python script that does the forceidx before invoking tovid to do the rest

---

### Post by radioraheem on 2008-04-05
Thanks for the tips  :)

When using k9copy, I seem to be having problems with the Shrink Factor settings.  From the guides I've read I need to get the colored bar into the "green zone" so it will fit on a 4.7GB DVD-R but when I change the slider bar for shrink factor the colored indicator does not change and stays in the red zone.

apt installed k9copy 1.1.3

What am I missing here?

Thanks again for the help.

---

### Post by xc3RnbFO8P on 2008-04-05
Output device > ISO Image @ Default it will fit 4.7gb

---

### Post by radioraheem on 2008-04-05
So just ignore the color bar and make sure it has those settings, that will give me a 4.7GB file, correct?

Many, many thanks!!!

---

