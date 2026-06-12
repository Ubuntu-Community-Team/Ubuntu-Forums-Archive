---
title: "MythTV no video (black screen)"
date: 2009-12-17
forum: Multimedia Software
---

### Post by squaregoldfish on 2009-12-17
For the past few days, I've been unable to watch any programmes, recorded or live, in MythTV. I get perfect audio, but I just have a black screen - no video is shown, and neither is the OSD.

If I run mythfronted from the command line, I get the following error repeated constantly:

```
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x2a00001

```A google search hasn't turned up anything for this error, and now I'm stumped.

I think this happened following an update to xorg:

xserver-xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10

Does anyone have any clues? I could try downgrading xorg, but I'd like to think of that as a last resort.

Steve.

---

### Post by RedSingularity on 2009-12-17
Have you tried viewing the video with compiz disabled?

---

### Post by squaregoldfish on 2009-12-17
I'm not using compiz at all.

Also, I've confirmed that the videos are OK - mplayer can play the recordings quite happily.

Steve.

---

### Post by squaregoldfish on 2009-12-23
Hmm. Mysteriously started working again.

Just one of those things, I suppose.

---

### Post by smallJockMcFeegle on 2010-01-13
Sorry, but not solved for me. I'm also using mythtv, but I had the problem since installing Kubuntu 9.10.

I also recognized, that the black screen problem isn't persisting: after killing X via Alt-Print-K once or twice the video appears as if nothing ever happend. The Xorg.0.log of a working X instance doesn't differ in any line from a failing one.  The mythtvfrontend log contains: 

```

X Error: BadAlloc (insufficient resources for operation) 11
        Extension:    133 (Uknown extension)
        Minor opcode: 19 (Unknown request)                                                                   
        Resource id:  0x4400001

```

Any hint, where to search for a solution?

---

### Post by smallJockMcFeegle on 2010-01-13
Ok, also fixed for me.  After recognizing that the X-Errors differ in different numbers, I intended to start a new thread. This also lead me to the  [multimedia howto page]("http://ubuntuforums.org/showthread.php?t=766683"). Thee are some instructions to add the **medibuntu **repository. I followed them but it didn't help in the first instance. I also had to enable the "update" feature for all sources in KPackageKit.

Launch KPackageKit, Settings.


[LIST]
[*]Software of Kubuntu: check all
[*]Other Software: check all except cdrom
[*]Updates: check all, I've selected "only notify about available updates"
[/LIST]

Now I've been provided by 104 updates. After installing them the problem vanished.

---

