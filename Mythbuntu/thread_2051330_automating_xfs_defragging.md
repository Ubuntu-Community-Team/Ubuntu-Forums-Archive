---
title: "automating xfs defragging"
date: 2012-09-01
forum: Mythbuntu
---

### Post by zapstrap on 2012-09-01
I have a long-standing problem with hd recordings from an hvr-1600 being filled with distortion, tearing, weird artifacts, audible buzzes and clicks. I just ran this:
```
xfs_db -c frag -r /dev/sdc1
```
...on the drive and found something on the order of 450,000 fragments on ~2,800 files. This seems a little much. I modified the way the xfs partition is mounted (it had the default options only) in fstab:
```
# stock options:
UUID=...	/media/archive	xfs	defaults	0	2
# modified options:
UUID=...	/media/archive	xfs	defaults,noatime,logbufs=8,allocsize=512m	0	2
```
... and ran defrag for a while, like so:
```
xfs_fsr -v /dev/sdc1
```
This all seems to have worked nicely, and so far the recordings are not completely trouble free, but so close to flawless as to be off the bug-hunting radar screen.

This mythtv box does not run 24/7 but does write a wake-up time into the bios, waking up to record, and shutting down when idle.

So, how do I automate a periodic clean-up of the media drive? A cron job seems the most obvious, and it's a very simple command, but how do I go about getting the machine to wake-up to defrag? I do not want it defragging while it's recording, which means it may be powered down. Can I add some sort of generic job into the myth backend and have it schedule only when not recording?

---

### Post by klc5555 on 2012-09-01
Since the one time your machine is known to be operating but not recording is when it has completed a recording and is about to shutdown, perhaps a ```
xfs_fsr -v -t 900
``` or something similar at the beginning of your shutdown script could be tried. 

True, 15 minutes per bootup/shutdown won't defrag a lot of files. But the utility only defrags files, not freespace; a file should only need to be completely defragged once. So, after xfs_fsr has by degrees caught up over time, the utility should have no trouble completing its 10 passes and exiting in much less than 15 minutes, whereupon the shutdown would continue.

---

### Post by zapstrap on 2012-09-02
That does seem like a good place to put it, but if the shutdown cycle has an extra 15 minutes in it, it's possible the machine may not shutdown completely before needing to wake back up to make another recording, and therefore miss a recording. This might be too obscure of an event to worry about.

Doesn't the backend support custom jobs? Can I not make one of them the defrag command and specify when I want it to run? It would be much like waking up to record, but instead, waking up to defrag. That way it wouldn't interfere with shutting down, and could be scheduled at a time when there are no conflicts. I'm not sure myth will wake up just to run a custom job, guess I'll just have to give it a try.

---

