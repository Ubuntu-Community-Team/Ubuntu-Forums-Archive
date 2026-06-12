---
title: "Can't record video on Cheese"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Fibonacci on 2009-02-05
I've got a Logitech QuickCam Communicate MP which otherwise worked out of the box on GNU/Linux. I've tested it on aMSN, Skype, xawtv, and even Cheese - although only for static pictures in this later case.
However, it appears that it doesn't work for video on Cheese. Whenever I try to record video one of the following happens:
· Either the video freezes after a few frames. Even if I leave it recording for ten minutes, the actual video written to disk is frozen for ten minutes. (best case)
· Or Cheese displays the first few captured frames, afterwards freezing the video as in the previous case, but the file actually written to HD is **empty**. (worst case)
All during this problems, Cheese outputs **nothing** to the console.
Even more strangely, the problem *might* not manifest itself on low-res videos, i.e. 320×240 or lower. But if I have recorded video at a higher resolution (which has invariably failed), and then try to record again at 320×240, then the problem will most likely appear again.

How can I fix that?

Thanks.

---

### Post by KeeperOfDreams on 2009-06-07
Wanted to add my information as well.
Just discovered this.
Runnning Ubuntu 9.04 post upgrade from 8.04 -> 8.10 -> 9.04
Under 8.04 running video fine after upgrade to 9.04, video works for most applications (skype etc.) But not cheese.
Cheese is locking, window responds to x button, but then must force quit application.
File is started, but no data in file is created.
Machine is a HP DV5Z with built in webcam (will need to investigate model).
Will add more information as I discover it.

---

### Post by no2498 on 2009-09-05
get( wxcam )

---

### Post by Fibonacci on 2009-09-06
Excuse me?

---

### Post by no2498 on 2009-09-14
[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)


you can get it in a deb file

---

