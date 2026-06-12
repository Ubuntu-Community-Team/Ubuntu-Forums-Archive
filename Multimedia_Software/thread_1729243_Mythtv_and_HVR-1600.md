---
title: "Mythtv and HVR-1600"
date: 2011-04-14
forum: Multimedia Software
---

### Post by Derek Karpinski on 2011-04-14
Hi all,

New Ubuntu user here.  I'm trying to get away totally from Windows Vista, but my fiancé loves Windows Media Center and the ability to record shows while we're at work.  So, I installed mythtv.  I've got the video working.  Except for the lower channels show up very snowy, but that's another issue.

The big problem I have is no sound.  I know my card is working because it works in Vista, and if i type in terminal:

```
cat /dev/video1 > ~/Desktop/test.mpg
```I can open it up in vlc and I have video and sound.  But inside myth I get no sound.

Does anybody have any suggestions?  Thanks in advance.):P

-Derek

---

### Post by Derek Karpinski on 2011-04-14
Ok..........update:

I removed some orphaned packages with:

```
sudo apt-get autoremove
```

There were a lot of v4l and ivtv packages because I had installed TV-viewer last night.

Now..........I have sound.  But, everything is slo-mo.  The sound and video are sync'd but everything is slow.  Everything seems to be running at .5X normal speed.

and again, if I run:

[CODE]cat /dev/video1 > ~/Desktop/test.mpg[CODE]

The test video works perfectly.

---

