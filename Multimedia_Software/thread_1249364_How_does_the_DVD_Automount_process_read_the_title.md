---
title: "How does the DVD Automount process read the title?"
date: 2009-08-25
forum: Multimedia Software
---

### Post by nwfisk on 2009-08-25
Hello all,

I'm currently in the middle of writing a script that backs up DVDs to iso files (run automatically when I insert dvd videos using ivman), and automatic file naming is the last hurdle.

I noticed that when Ubuntu automounts DVDs, it uses the actual title of the movie/DVD, correctly formatted with spaces. My question is: where is that information pulled from, and how might I do the same? Or, where might I begin finding out how that process works?

Currently I'm using dd to pull the volume label (dd if=/dev/sr1 bs=1 skip=32808 count=32 2> /dev/null) and sed to dump the empty space, but I'm left with ugly file names like "RECKLESS_PART_2.iso" rather than the nice "Reckless Part 2" shown at the mount point in /media. Beyond aesthetics, some (cheap) DVDs do not have accurate volume labels.

Any thoughts/guidance would be appreciated!

---

