---
title: "VidCutter low disk space warning, then no audio saved"
date: 2019-05-08
forum: Multimedia Software
---

### Post by ra7411 on 2019-05-08
I have a 4.7 gig vid I'm trying to edit w/ VidCutter.

When I save the edited version, I get a low disk space warning (pic attached). I click on "ignore", it continues saving, but the edited version has no audio track when I test play it.

I've edited smaller vids, and the audio is saved so it's no some setting that needs clicking. In other words, I think I need to  re-set  where VidCutter sends temp files to avoid low disk space. I only have about 12 gigs available in "/" , so I would like to send temps to /Home which has ample space, but I can't figure out how to re-set it in VidCutter.

Any ideas?

Thanks

---

### Post by ra7411 on 2019-05-12
This is a reply to my own post - I found a vid editor that works with large files - LosslessCut.

There's a page [ [https://github.com/mifi/lossless-cut/releases](https://github.com/mifi/lossless-cut/releases) ] where you can download a zip file, unzip it, LosslessCut will be in the directory and can be run (at least it can be in Ub 18.04).

---

### Post by aeronutt on 2019-05-20
I'm also having problems with VidCutter, and no audio in the saved/edited files.

I tried losslesscut...but running "./LosslessCut" gives and error 
"libgconf-2.so.4: cannot open shared object file: No such file or directory"

Bummed.

---

### Post by aeronutt on 2019-05-20
UPDATE:
losslesscut runs fine in 18.04 for me, so it's obviously not compiled to run in 19.04.

But, the bigger issue...I found out the audio problem with vidcutter. IF, I leave vidcutter open, and view the edited file in a player (eg VLC), audio doesn't work. But if I close vidcutter, then play the edited vid in VLC, it's all fine. It appears vidcutter is 'locking' the audio output and not allowing other programs access to audio. Close Vidcutter, all is ok.

---

