---
title: "AddFrame Deadlock detected in mythtranscode"
date: 2016-02-05
forum: Mythbuntu
---

### Post by danBhentschel on 2016-02-05
**Problem**: Transcode of recorded file fails. Job status in System Status -> Job Queue shows "Unrecoverable error"

**mythtranscode.log**:

```
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: I CoreContext mpeg2fix.cpp:1738 (ConvertToI) Converting frame #10 from B to I Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: I CoreContext mpeg2fix.cpp:1738 (ConvertToI) Converting frame #11 from P to I 
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: N CoreContext mpeg2fix.cpp:2291 (Start) Need to insert 190 frames > max allowed: 20.  Assuming bad PTS
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: N CoreContext mpeg2fix.cpp:2291 (Start) Need to insert 190 frames > max allowed: 20.  Assuming bad PTS
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: E CoreContext mpeg2fix.cpp:705 (AddFrame) Deadlock detected.  One buffer is full when the other is empty!  Aborting
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: E CoreContext main.cpp:724 (main) Transcoding /storage/recordings/1101_20150406005900.mpg failed
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: N CoreContext main.cpp:1090 (CompleteJob) Deleting /storage/recordings/1101_20150406005900.mpg.tmp
Feb  5 14:36:41 mythman mythtranscode: mythtranscode[6099]: N CoreContext main.cpp:749 (transUnlink) Requesting delete for file 'myth://Default@mythman/1101_20150406005900.mpg.tmp'.
Feb  5 14:36:44 mythman mythtranscode: mythtranscode[6099]: I CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.

```

**Goal**: To losslessly remove commercials from a flagged recording, using the built-in "Autodetect" transcoding profile.

**Repeatability**: Happens every time with this episode. I tried another episode of the same show, and the same thing happened. I tried an episode of a different show, and it worked fine.

Any suggestions on where to go from here?

Mythbuntu 14.04, running the latest release of MythTV 0.27. I just updated all packages this morning.

```
$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

```

---

### Post by aelfric55 on 2016-02-29
This is one of the bugs in mythtranscode that have persisted for years without being fixed. Discussed in the wiki: [https://www.mythtv.org/wiki/Mythtranscode](https://www.mythtv.org/wiki/Mythtranscode) 

Of the two workarounds discussed there, I've tried the manual remuxing idea several times without the remuxed file ever making past the deadlock detected error. It seems to be a waste of time. Using a different utility to cut/transcode the recording appears to be the only reliable workaround. The wiki recommends a projectx based script; I find if I'm at the point where I'm dithering directly with an individual recorded file, I prefer cutting the commercials manually and saving the file losslessly with avidemux.

---

### Post by danBhentschel on 2016-02-29
Thanks. The wiki link is appreciated. I will keep this in mind for the future. As for the current couple of recordings, I implemented my own script that is very similar to mythcutprojectx. Not surprisingly, the files were both very damaged for a few seconds in the middle, and needed some significant manual massaging to get them to (sort of) a usable state. I was never able to quite get the closed captioning to work properly again.

Thanks again. I appreciate the response.

---

