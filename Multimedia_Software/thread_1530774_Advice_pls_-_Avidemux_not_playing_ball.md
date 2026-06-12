---
title: "Advice pls - Avidemux not playing ball"
date: 2010-07-14
forum: Multimedia Software
---

### Post by yeleek on 2010-07-14
Hi,

Have a VOB, using Avidemux apply video cropping and resizing = no problem.  Set it to use MP3 for audio, and adjust the audio sync to -480ms.  Then use calculator to set a custom size of 2gb.  Test it by selecting output and both video/audio look good.

Save the video, and whilst it does carry out the video filtering.  The output size is nearly always 800mb, and the audio hasn't been sync'd.  I must have tried this whole process 5 or 6 times now.

So is it buggy on Lucid?  Is it a dodgy install?  Are there other options to try?  I normally use DVD:RIP but can't in this case as I've already got the VOB.  So are there better alternatives than Avidemux.

Thanks

---

### Post by yeleek on 2010-07-14
Anyone have any ideas?  Just tried it again with xvid and AC3.  Same thing, video filters applied, audio sync is not.

Its just a case of ticking that box and entering -480ms isn't it?

As I say it works fine in the output window, but the file itself is out of sync.

---

### Post by yeleek on 2010-07-15
Last try - any one? Pls?

---

### Post by amsterdamharu on 2010-07-15
Not sure if ffmpeg can do this, you can try winff, that is a gui for ffmpeg. 
Make sure you got the unstripped or extra libraries.
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Worst case you can extract the audio, remove some with audacity and then encode the audio and video to a new file.

---

